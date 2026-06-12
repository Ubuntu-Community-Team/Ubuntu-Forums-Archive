---
title: "Change sources.list via Preseed"
date: 2013-08-13
forum: Server Platforms
---

### Post by seancallaway on 2013-08-13
Greetings, Ubuntu-ers!

I am playing with a PXE Multi-Install server in my lab and have it  working to the point where I can do an unattended install of Ubuntu  Server. After a lot of work, I got all of the mis-configurations hammered out where, after telling the machine to boot from NIC and selecting the proper menu item, everything installs with zero interaction. The newly installed server reboots and allows me to login with the username and password specified in the preseed file. Perfect, so far.

My issue is that /etc/apt/sources.list (on the newly installed server) is pointing to the PXE  server, which is serving up the contents of the Ubuntu Server 12.04.2 ISO and is  not actually an apt cache, so running apt-get update on the newly  installed server tosses up a bunch of errors. 


  Is there a way, via the preseed file, that I can change the contents  of the sources.list to a local mirror, much like a regular CD install  would do? I understand that I could setup an apt cache, but this won't work with the end state, where these machines will not be able to see the PXE server post-deployment.


  Thanks in advance.

---

### Post by awells527 on 2013-08-13
This is what I have in my preseed file to point to an internal update server.

```

d-i mirror/country string manual
d-i mirror/http/hostname string server.example.net
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string

d-i apt-setup/restricted boolean true
d-i apt-setup/universe boolean true
d-i apt-setup/backports boolean true
d-i apt-setup/services-select multiselect security
d-i apt-setup/security_host string server.example.net
d-i apt-setup/security_path string /ubuntu

```

---

### Post by awells527 on 2013-08-13
-deleted-

---

### Post by seancallaway on 2013-08-13
> **awells527 said:**
> This is what I have in my preseed file to point to an internal update server.

```

d-i mirror/country string manual
d-i mirror/http/hostname string server.example.net
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string

d-i apt-setup/restricted boolean true
d-i apt-setup/universe boolean true
d-i apt-setup/backports boolean true
d-i apt-setup/services-select multiselect security
d-i apt-setup/security_host string server.example.net
d-i apt-setup/security_path string /ubuntu

```

Yes, this is basically what's in mine. The issue I'm facing is that I want it to point back to Ubuntu's servers post-install.

That being said, I have a possible solution using d-i preseed/late_command that I have yet to test. I will report back with my results.

---

### Post by awells527 on 2013-08-13
I think the first block is for the base system, and the second block is for post-install packages & sources.list.  I would have to run a couple tests to verify.

Ref the [example preseed]("https://help.ubuntu.com/12.04/installation-guide/example-preseed.txt") file.  Here is that relevant code again with the comments...

This section is at the top, right after the network settings:

```
### Mirror settings
# If you select ftp, the mirror/country string does not need to be set.
#d-i mirror/protocol string ftp
d-i mirror/country string manual
d-i mirror/http/hostname string archive.ubuntu.com
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string

# Alternatively: by default, the installer uses CC.archive.ubuntu.com where
# CC is the ISO-3166-2 code for the selected country. You can preseed this
# so that it does so without asking.
#d-i mirror/http/mirror select CC.archive.ubuntu.com
```

This is towards the bottom, after the partitioning, base system setup, etc.

```
### Apt setup
# You can choose to install restricted and universe software, or to install
# software from the backports repository.
#d-i apt-setup/restricted boolean true
#d-i apt-setup/universe boolean true
#d-i apt-setup/backports boolean true
# Uncomment this if you don't want to use a network mirror.
#d-i apt-setup/use_mirror boolean false
# Select which update services to use; define the mirrors to be used.
# Values shown below are the normal defaults.
#d-i apt-setup/services-select multiselect security
#d-i apt-setup/security_host string security.ubuntu.com
#d-i apt-setup/security_path string /ubuntu

# Additional repositories, local[0-9] available
#d-i apt-setup/local0/repository string \
#       http://local.server/ubuntu squeeze main
#d-i apt-setup/local0/comment string local server
# Enable deb-src lines
#d-i apt-setup/local0/source boolean true
# URL to the public key of the local repository; you must provide a key or
# apt will complain about the unauthenticated repository and so the
# sources.list line will be left commented out
#d-i apt-setup/local0/key string http://local.server/key

# By default the installer requires that repositories be authenticated
# using a known gpg key. This setting can be used to disable that
# authentication. Warning: Insecure, not recommended.
#d-i debian-installer/allow_unauthenticated boolean true
```

---

### Post by seancallaway on 2013-08-13
Yes, you're right about the bottom section, but that only applies to the security repository. Main, universe, etc. are still pointed at the local server.

---

### Post by awells527 on 2013-08-13
Ok, I guess I misunderstood how that was documented.

There is always the "preseed/late_command" option for downloading a sources.list file from your server.

---

### Post by seancallaway on 2013-08-13
Yes, this what I was talking about [earlier]("http://ubuntuforums.org/showthread.php?t=2167373&p=12755614#post12755614").

EDIT: I found my answer:

```
d-i preseed/late_command string wget http://pxe.lab.mydomain/sources.list -O /target/etc/apt/sources.list
```

You have to use /target, as the installer mounts the new hard drive to that point.

---

