---
title: "Package Manager &amp; Update Manager problems"
date: 2012-05-19
forum: System76 Support
---

### Post by MoebusNet on 2012-05-19
While updating using Update Manager, my wireless connection dropped out. Attempted Update Manager again, no go. Same for apt-get update.

In Terminal:

```
Fetched 1,576 B in 14s (111 B/s)                                               
Reading package lists... Error!
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com precise-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://planet76.com ./ Release: The following signatures were invalid: BADSIG 176A5C84ED67C9ED System76 Development (System76 Development Package Signing Key) <dev@system76.com>
W: GPG error: http://archive.canonical.com precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EFD5FA852F20733F
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://us.archive.ubuntu.com precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://us.archive.ubuntu.com precise-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://us.archive.ubuntu.com precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/Release  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/Release  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
```

I tried to report a bug using ubuntu-bug package-manager, but that didn't work either (unable to determine package)

I'm at a loss what to do next, so help will be appreciated.

---

### Post by 2F4U on 2012-05-20
Does executing these commands help?

  cd /var/lib/apt
  sudo mv lists lists.old
  sudo mkdir -p lists/partial
  sudo apt-get update

This will rebuild the cache.

If it doesn't help, this forum post has additional suggestions:

[http://ubuntuforums.org/showthread.php?t=1869890](http://ubuntuforums.org/showthread.php?t=1869890)

---

### Post by wilee-nilee on 2012-05-20
I would start with grabbing the missing keys, here is the first missing one add the key to the code per missing key.

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 176A5C84ED67C9ED
```Do this with every missing key then run a update to see if you have all set.

The link from above suggests this as well as some other methods check out drs305's posts.

---

### Post by MoebusNet on 2012-05-20
OK, I've found part of my problem. The wireless internet provider where I'm staying kicks you off-line if you use too much data (like updates). My other data connection is through my Verizon cell phone, which currently seems to be throttled down to the point of unusability for updates. I guess I'll have to go somewhere where I can get a decent data connection before I can do anything more. I'll check back when I can get this sorted.

Thanks for the input wilee-nilee & 2F4U.

---

### Post by MoebusNet on 2012-05-20
Before packing everything up in search of a decent data connection, I got the phone number for tech support for the wireless network I'm using. I explained that I use Ubuntu Linux, that I'm having trouble completing an update because I keep getting kicked off the wireless system and could he please help. I gave him my MAC address and he reset the wireless system from his end as well as removing the requirement for me to log-in to the wireless system.

I tried grabbing the missing keys as wilee-nilee suggested,but there must have been more wrong than that would fix. So I rebuilt the cache as 2F4U suggested and that seems to have sorted everything.

This is why I've used Ubuntu for years...the community is just unsurpassed in helpfulness.

Thank you for your help!

---

### Post by voicesinthefan on 2012-05-22
> **2F4U said:**
> Does executing these commands help?

  cd /var/lib/apt
  sudo mv lists lists.old
  sudo mkdir -p lists/partial
  sudo apt-get update

This will rebuild the cache.

If it doesn't help, this forum post has additional suggestions:

[http://ubuntuforums.org/showthread.php?t=1869890](http://ubuntuforums.org/showthread.php?t=1869890)

Thanks 2F4U!  I had the same problem and this fixed it.

---

### Post by teriyaki-89 on 2012-08-01
Hi i am facing the same problem on ubuntu 12.04

W: GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59
W: GPG error: [http://kz.archive.ubuntu.com](http://kz.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

 i did this
[B]cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get update
[/B]
and  this 
**sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 082CCEDF94558F59  40976EAF437D05B5 **
and got 
[B]Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.aaN7ANuRBd --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 082CCEDF94558F59 40976EAF437D05B5
gpg: requesting key 94558F59 from hkp server keyserver.ubuntu.com
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpgkeys: key 082CCEDF94558F59 not found on keyserver
gpgkeys: key 40976EAF437D05B5 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0[/B]

Why can't it find the key?

---

### Post by abhicr on 2012-08-05
hey folks,

I had the same bad-sig error, and this bunch of commands helped get my update manager up and going... hth... :)

sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update

-abhi
P.S: a previous comment already had the third command onwards, but that was still throwing back the error... a clean helped and then everything got back to normal... :)

---

### Post by teriyaki-89 on 2012-08-05
**thank you, did everything above **


GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59
W: GPG error: [http://kz.archive.ubuntu.com](http://kz.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/binary-amd64/Packages](http://archive.canonical.com/ubuntu/dists/precise/partner/binary-amd64/Packages)  Bad header line

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/precise/partner/binary-i386/Packages)  Bad header line

W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric-proposed_main_binary-amd64_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by isantop on 2012-08-06
> **teriyaki-89 said:**
> **thank you, did everything above **


GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59
W: GPG error: [http://kz.archive.ubuntu.com](http://kz.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/binary-amd64/Packages](http://archive.canonical.com/ubuntu/dists/precise/partner/binary-amd64/Packages)  Bad header line

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/precise/partner/binary-i386/Packages)  Bad header line

W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric-proposed_main_binary-amd64_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

For the bad-sig problem, you need to adjust the key command to match the key you need. In your case, the command would be:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 94558F59
```

For the other problems, I would recommend running all of the above commands again:

```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get update
```

(note that using "sudo" before each command is slightly safer, and preferable. You'll only need to type your password once anyway.)

---

### Post by teriyaki-89 on 2012-08-09
did the commands above the problem still persists.
my ubuntu is  under the proxy 

[B]W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/binary-amd64/Packages](http://archive.canonical.com/ubuntu/dists/precise/partner/binary-amd64/Packages)  404  Not Found[/B]

I imported key and tried to update this like apt-gey update, but still no luck

---

### Post by isantop on 2012-08-09
> **teriyaki-89 said:**
> did the commands above the problem still persists.
my ubuntu is  under the proxy 

[B]W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/binary-amd64/Packages](http://archive.canonical.com/ubuntu/dists/precise/partner/binary-amd64/Packages)  404  Not Found[/B]

I imported key and tried to update this like apt-gey update, but still no luck

Try this:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 437D05B5
```

---

### Post by teriyaki-89 on 2012-08-09
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.UE5RXMpNlQ --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

**after apt-get update the same error**

---

### Post by isantop on 2012-08-10
> **teriyaki-89 said:**
> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.UE5RXMpNlQ --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

**after apt-get update the same error**

I think the problem you're seeing is related to the proxy you're using. Can you try it without the proxy?

---

### Post by teriyaki-89 on 2012-08-12
> I think the problem you're seeing is related to the proxy you're using. Can you try it without the proxy?

**Yes the problem was because of proxy. Why can't ubuntu's apt work with proxy?**

---

### Post by isantop on 2012-08-13
> **teriyaki-89 said:**
> **Yes the problem was because of proxy. Why can't ubuntu's apt work with proxy?**

I would actually guess that it was because of that specific proxy.

---

### Post by teriyaki-89 on 2012-08-17
this is usual proxy on windows 7 called [ccproxy]("http://www.youngzsoft.net/ccproxy/")
and i can easily browse on web via this

---

### Post by isantop on 2012-08-17
> **teriyaki-89 said:**
> this is usual proxy on windows 7 called [ccproxy]("http://www.youngzsoft.net/ccproxy/")
and i can easily browse on web via this

Right, but the proxy may not allow connections to the specific servers needed for APT. That wouldn't really be a flaw in APT, but the proxy.

---

### Post by teriyaki-89 on 2012-08-19
there are no restrictions on proxy, and i can get all ubuntu servers through proxy, so the error is only on verification with signature
i can send all apt log

---

### Post by isantop on 2012-08-21
> **teriyaki-89 said:**
> there are no restrictions on proxy, and i can get all ubuntu servers through proxy, so the error is only on verification with signature
i can send all apt log

The proxy doesn't support *all* of the services that APT requires (at least those related to verification). Otherwise, you wouldn't be able to use it when you weren't behind the proxy.

---

### Post by teriyaki-89 on 2012-08-22
that's really sad moment, 
 i have to use proxy, cause have no direct access

---

### Post by bonesTdog on 2012-08-25
The 2F4U solution worked perfectly for me as well running 12.04!  Thank goodness there are smart folks like you out there keeping us running and in-line! Thanks!

---

### Post by teriyaki-89 on 2012-08-26
could you please explain it or give the url for this solution

---

### Post by abhicr on 2012-08-27
Hey fellas,
had a problem to access and update  from behind my proxy... here's a solution i found

[https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy](https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy)

scroll down to the topic titled[SIZE=2] "Setting up apt-get to use a http-proxy"

Oh, and thanks @bonesTdog, your hint to check with the 2F4U solution was the key to fix my problem :) @teriyaki-89, was this what you're looking for...?

-abhi
[/SIZE]

---

### Post by teriyaki-89 on 2012-08-27
> @teriyaki-89, was this what you're looking for...?     **nope** 
thank you guys for help i exported my variables in **/etc/apt.conf**
```
Acquire::http::proxy "http://www:pass@10.7.59.12:808/";
Acquire::https::proxy "http://www:pass@10.7.59.12:808/";
Acquire::ftp::proxy "http://www:pass@10.7.59.12:808/";
Acquire::socks::proxy "http://www:pass@10.7.59.12:808/";
```
**/etc/bash.bashrc**
```
export ftp_proxy="http://www:pass@10.7.59.12:808";
export http_proxy="http://www:pass@10.7.59.12:808";
export https_proxy="http://www:pass@10.7.59.12:808";
```
Also i have a proxy entry in network tab and cause of it's proxy interface drawback i wrote some entries to gconf where i put proxy user, password and bypass list, so only chromium and mozilla can work with windows proxy now on other machine and all ubuntu grafical applications don't work, apt does not work cause of hashe mismatch but it can download some packages i see this in proxy logs. In terminal i can use wget and download packages. And if i setup squid proxy server ubuntu can work with this well.
I wish next ubuntu release have no drawback working under not native linux proxies like ccproxy

---

### Post by CDXX on 2012-08-28
> **abhicr said:**
> hey folks,

I had the same bad-sig error, and this bunch of commands helped get my update manager up and going... hth... :)

sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update

-abhi
P.S: a previous comment already had the third command onwards, but that was still throwing back the error... a clean helped and then everything got back to normal... :)


Kool beans bra, mos definitely worked for my issue/s. ):P

I myself recently upgraded to 12.04 from 10.04 and all has been well if not better since. But a few days ago I fire up the update manager and start getting errors that just wont quit. Only affecting the Update Manager and the Software Center. The error I would get when trying to run the update manager;

'[B][I]Reading package lists... Error!
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.[/I][/B]'

All is well once more.. ;)

---

### Post by Gemneroth on 2012-09-03
> **abhicr said:**
> hey folks,

I had the same bad-sig error, and this bunch of commands helped get my update manager up and going... hth... :)

sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update

-abhi
P.S: a previous comment already had the third command onwards, but that was still throwing back the error... a clean helped and then everything got back to normal... :)

Wonderful! This worked for me! Thanks for posting how to do this!

---

### Post by alsander on 2012-09-30
Originally Posted by **abhicr**                     [[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=12151338#post12151338")                 
                 hey folks,

I had the same bad-sig error, and this bunch of commands helped get my update manager up and going... hth... :smile:

====================================
sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
===============================

I'm another happy camper...  This fixed my bad-sig error.  Thanks to all.

---

### Post by my real name is steve on 2012-12-02
> **voicesinthefan said:**
> Thanks 2F4U!  I had the same problem and this fixed it.

So far I have tried the /cd/var/lib/apt suggestion above and it did shorten the list quite a bit, just still have errors.

i also tried:

If you just want to add the one repository key generating the errors:
Code:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 437D05B5 3E5C1192
sudo apt-get update



I've tried putting in:
sudo ./launchpad-update

REF:[http://ubuntuforums.org/showthread.php?p=12383824#post12383824](http://ubuntuforums.org/showthread.php?p=12383824#post12383824)

I've tried putting in /bin /opt /tmp /etc and several other places and executing it each time, but no dice when I try the sudo /.launchpad-update cmd in Terminal.

and ubuntuforums.org/showthread.php?p=12383824#post12383824
[http://ubuntuforums.org/showthread.php?t=1869890](http://ubuntuforums.org/showthread.php?t=1869890)
[http://deb-multimedia.org/](http://deb-multimedia.org/) (Loosely related)
(I accidentally deleted a few other things I tried so no URL for that).

A few things to note:

I CANNOT use the Authentication tab of Software Sources!
I no longer run Fiesty Fawn 7
I run DreamLinux 5
I have successfully done this in the past, I cannot recall the steps.

My out put errors:


Get:134 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en [12.3 kB]
Fetched 29.3 MB in 16min 13s (30.1 kB/s)                                       
Reading package lists... Done
W: GPG error: [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 83FBA1751378B444
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
stevewilliams@SteveRunsLinux:/var/lib/apt$ 

Me /etc/apt/sources.list

deb [http://ftp.debian.org/debian](http://ftp.debian.org/debian) testing main contrib non-free
#deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) testing main non-free

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
###################
## Debian Testing ##
###################
# Testing 
#deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) testing main contrib non-free
#deb-src [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) testing main contrib non-free

# Testing Security  [http://secure-testing-master.debian.net/](http://secure-testing-master.debian.net/)
deb [http://security.debian.org](http://security.debian.org) wheezy/updates main contrib non-free
deb-src [http://security.debian.org](http://security.debian.org) wheezy/updates main contrib non-free

#Testing Proposed Updates
deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) testing-proposed-updates main contrib non-free
deb-src [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) testing-proposed-updates main contrib non-free

# Debian Testing - - Multimedia
# deb [http://www.deb-multimedia.org](http://www.deb-multimedia.org) testing main non-free


# A shell script to automate the retrieval and installation of the Oracle (Sun) Java Runtime Environment
#  [http://www.duinsoft.nl/packages.php?t=en](http://www.duinsoft.nl/packages.php?t=en)
# Secure APT: apt-key adv --keyserver keys.gnupg.net --recv-keys 5CB26B26
# deb [http://www.duinsoft.nl/pkg](http://www.duinsoft.nl/pkg) debs all


# UBUNTU 

# Keys
 # sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
 # sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0

# deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) lucid main 
# deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) precise main

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric universe multiverse

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse


#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################


###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

###### Ubuntu Extras Repo
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################


####### 3rd Party Source Repos

#### LibreOffice (Source) - [http://www.documentfoundation.org/download/](http://www.documentfoundation.org/download/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
# deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) precise main

#### Wine (Source) - [https://launchpad.net/~ubuntu-wine/+archive/ppa/](https://launchpad.net/~ubuntu-wine/+archive/ppa/)
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
# deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) precise main 
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

Edit: (Reason: new borked Terminal output, we're improving, not quite there yet.).

I suspect, though I'm not quite sure yet, that the UBUNTU 10.xxxx at the bottom of the /var/cache/xxxx is a different version than the on DreamLinux 5 is based on. 

Here is my Terminal output this time:

Get:86 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main reiserfsprogs i386 1:3.6.21-1build1 [505 kB]
Get:87 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main vbetool i386 1.1-2ubuntu1 [10.7 kB]
Get:88 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main vorbis-tools i386 1.4.0-1ubuntu2 [125 kB]
Get:89 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main wodim i386 9:1.1.11-2ubuntu2 [367 kB]
Get:90 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main x11proto-randr-dev all 1.4.0+git20101207.0d32bb07-0ubuntu2 [32.0 kB]
Get:91 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe xfce4-mixer i386 1:4.8.0-2ubuntu1 [171 kB]
Get:92 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe xfdesktop4 i386 4.8.3-2ubuntu7 [152 kB]
Get:93 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe xfdesktop4-data all 4.8.3-2ubuntu7 [1026 kB]
Get:94 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main xfonts-encodings all 1:1.0.4-1ubuntu1 [583 kB]
Get:95 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main xorg-docs-core all 1:1.6-1ubuntu2 [42.2 kB]
Get:96 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main xserver-xorg-video-radeon i386 1:6.14.99~git20111219.aacbd629-0ubuntu2 [445 kB]
Get:97 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libbs2b0 i386 3.1.0+dfsg-2ubuntu1 [11.2 kB]
Get:98 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main liblircclient0 i386 0.9.0-0ubuntu1 [16.0 kB]
Get:99 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe mesa-utils i386 8.0.1+git20110129+d8f7d6b-0ubuntu2 [27.6 kB]
Fetched 44.8 MB in 8min 1s (93.0 kB/s)                                         
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 103359 files and directories currently installed.)
Preparing to replace findutils 4.4.2-4 (using .../findutils_4.4.2-4ubuntu1_i386.deb) ...
Unpacking replacement findutils ...
Processing triggers for install-info ...
Processing triggers for man-db ...
Setting up findutils (4.4.2-4ubuntu1) ...
(Reading database ... 103319 files and directories currently installed.)
Preparing to replace tar 1.26-4 (using .../tar_1.26-4ubuntu1_i386.deb) ...
Unpacking replacement tar ...
Processing triggers for man-db ...
Processing triggers for mime-support ...
Setting up tar (1.26-4ubuntu1) ...
(Reading database ... 103281 files and directories currently installed.)
Preparing to replace libc-bin 2.13-37 (using .../libc-bin_2.15-0ubuntu10.3_i386.deb) ...
Unpacking replacement libc-bin ...
dpkg: error processing /var/cache/apt/archives/libc-bin_2.15-0ubuntu10.3_i386.deb (--unpack):
 trying to overwrite '/usr/share/man/man1/getent.1.gz', which is also in package manpages 3.42-1
configured to not write apport reports
                                      dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libc-bin_2.15-0ubuntu10.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
stevewilliams@SteveRunsLinux:~$



Thank you!! :popcorn:

---

### Post by isantop on 2012-12-03
You've got repos from Debian, DreamLinux, and Ubuntu all on one machine! Yikes! D=

That's defintiely causing the problems. The fact is, if you want to use Ubuntu repos, you pretty much have to use Ubuntu (or a derivative). There are tons of changes in some packages in Debian that aren't all compatibile with Ubuntu's pacakages, and that's cauing the conflict.

---

### Post by my real name is steve on 2012-12-03
> **isantop said:**
> You've got repos from Debian, DreamLinux, and Ubuntu all on one machine! Yikes! D=

That's defintiely causing the problems. The fact is, if you want to use Ubuntu repos, you pretty much have to use Ubuntu (or a derivative). There are tons of changes in some packages in Debian that aren't all compatibile with Ubuntu's pacakages, and that's cauing the conflict.

I have done this before, and right now no errors at all since I last posted this.
 would you be willing to take a look at what I do have set up and tell me step by step what I **CAN** do to keep what I have already and [color=blue] 1} update the 12.04 ubuntu security script in etc/apt/sources.list [/color] **[color=orange] 2} keep the conflits to a miimum **[/color] ?

I also cannot find the script marked deb hllp://**[color=purple]partners.canocal.xxxx**[/color].net that goes in /sources.list and the one  that goes right under it in the old ubuntu versions. - I'm not sure if these are still used in this file since oob 7.04. ??

I had firefox runnining in this set up with DreamLinux 4 and oob and some other goodies, no luck here and I see oob has departed pretty far from Debian 7 Wheezy in some respects, but I'd like to get this as close to stable and pretty as I can, if you don't mind helping.

Thank you!

---

### Post by isantop on 2012-12-04
> **my real name is steve said:**
> Would you be willing to take a look at what I do have set up and tell me step by step what I **CAN** do to keep what I have already and [color=blue] 1} update the 12.04 ubuntu security script in etc/apt/sources.list [/color] [b][color=orange] 2} keep the conflits to a miimum

I honestly  can't. I don't have any experience with this sort of thing, and we can't offer any support for non-Ubuntu OS. You might be able to find support through a different venue (a Debian or DreamLinux forum), but this is completely outside of my support scope. :)

---

### Post by mojo706 on 2013-01-12
Yoh I'm not on System 76 but on Ubuntu (irrelevant I know) but thank you anyway for the suggestion on rebuilding cache. Worked perfectly!:p

---

### Post by mamboze on 2013-01-15
Excellent thread and thanks @ 2F4U for 

> 
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get update

This will rebuild the cache.



It worked for me running 11.04 on a Samsung RV511 laptop

---

### Post by IvanMP on 2013-01-22
Hi all

i still have a problem and i try everything, and when i try apt-get update i get the following ...

> 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease [2,330 B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [2,330 B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease [2,330 B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [2,330 B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease [2,330 B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease [2,330 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release
E: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release: The following signatures were invalid: NODATA 1 NODATA 2


Can pleas some one help me !

---

### Post by isantop on 2013-01-22
> **IvanMP said:**
> Hi all

i still have a problem and i try everything, and when i try apt-get update i get the following ...



Can pleas some one help me !

Have you tried running the commands in a terimal:

```
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get update
```

This should help out a lot.

---

### Post by IvanMP on 2013-01-22
Yes i did im using Ubuntu server 12.04LTS and all i have i terminal ... and still nothing ...  any idea ? pls i rely need this ....

---

### Post by isantop on 2013-01-22
> **IvanMP said:**
> Yes i did im using Ubuntu server 12.04LTS and all i have i terminal ... and still nothing ...  any idea ? pls i rely need this .... and one thing i have now notes is that /etc/apt/source.list is empty ...

Your sources.list is empty?

Honestly, the best option for you right now is probably to reinstall Ubuntu. That will fix your package manager.

---

### Post by IvanMP on 2013-01-23
re installing is not an option and its not a solution ... there must be a way

---

### Post by xXTwitchXx on 2013-02-22
W: There is no public key available for the following key IDs:
3B4FE6ACC0B21F32
W: There is no public key available for the following key IDs:
3B4FE6ACC0B21F32
W: There is no public key available for the following key IDs:
3B4FE6ACC0B21F32
W: There is no public key available for the following key IDs:
3B4FE6ACC0B21F32
W: There is no public key available for the following key IDs:
3B4FE6ACC0B21F32
W: There is no public key available for the following key IDs:
3B4FE6ACC0B21F32


trying to update moon, got as far as updating the repositories. tried to run sudo apt-get updates and i got that error up top there.

---

### Post by derock666 on 2013-03-02
I was having the same issue.  This seems to have fixed things for me as well.  Thanks!

---

### Post by MoebusNet on 2013-03-15
> **abhicr said:**
> hey folks,

I had the same bad-sig error, and this bunch of commands helped get my update manager up and going... hth... :)

sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update

-abhi
P.S: a previous comment already had the third command onwards, but that was still throwing back the error... a clean helped and then everything got back to normal... :)

Happened again, I needed the above to repair. Thanks abhi! :)

---

### Post by wavesailor on 2013-03-23
> **2F4U said:**
> Does executing these commands help?

  cd /var/lib/apt
  sudo mv lists lists.old
  sudo mkdir -p lists/partial
  sudo apt-get update

This will rebuild the cache.

If it doesn't help, this forum post has additional suggestions:

[http://ubuntuforums.org/showthread.php?t=1869890](http://ubuntuforums.org/showthread.php?t=1869890)

That worked for me - Thanks

---

### Post by Vixx_Daru on 2013-05-10
> **2F4U said:**
> Does executing these commands help?

  cd /var/lib/apt
  sudo mv lists lists.old
  sudo mkdir -p lists/partial
  sudo apt-get update

This will rebuild the cache.

If it doesn't help, this forum post has additional suggestions:

[http://ubuntuforums.org/showthread.php?t=1869890](http://ubuntuforums.org/showthread.php?t=1869890)

It worked for me. Thank you **2F4U**.

---

### Post by Fahuadai on 2013-05-22
> **2F4U said:**
> Does executing these commands help?

  cd /var/lib/apt
  sudo mv lists lists.old
  sudo mkdir -p lists/partial
  sudo apt-get update

This will rebuild the cache.

If it doesn't help, this forum post has additional suggestions:

[http://ubuntuforums.org/showthread.php?t=1869890](http://ubuntuforums.org/showthread.php?t=1869890)

Thank you - this solved my issue. Currently upgrading :)

---

### Post by TynieTinker on 2013-07-07
I'm new to ubuntu, and I had the same problem while I was trying to install the Intel Graphics pack. But instead of being simple for me, I got this when I tried running the suggested commands:
> E: Unable to lock the download directory

So I browsed around online, came across another forum post that solved my issue. So I thought I'd share it on this thread, to save others encountering the same problem having to search for more answers. :)
 I found out that running this:
```
sudo apt-get autoremove && sudo apt-get clean && sudo apt-get autoclean
```

In a fresh terminal, seemed to solve my issues to be able to run:
```
sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```

With no issues, Like **abhicr **suggested.

Thanks for the help. :)

---

### Post by ajaaskel2 on 2013-10-04
Thanks for that:

```
sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```

which evidently solved also my problem which was looking like this:

sudo apt-get update
.
.
W: Tiedoston bzip2:/var/lib/apt/lists/partial/archive.canonical.com_ubuntu_dists_raring_partner_binary-amd64_Packages nouto ei onnistunut  Tarkistussumma ei täsmää         [COLOR=#00ffff](English:  "package download failed, checksum does not match")[/COLOR]

E: Some index files failed to download. They have been ignored, or old ones used instead.

[COLOR=#00ffff][/COLOR]

---

### Post by isantop on 2013-10-04
As a note, using "sudo -i" is not generally recommended. The preferred way would be:

```
sudo apt-get clean
sudo cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```

---

### Post by Getwitit on 2013-10-19
Executing those commands helped me. Thank you 2F4U!! 
Running: Ubuntu 12.04.3 LTS (GNU/Linux 3.2.0-54-generic-pae i686)

Thanks again.

---

### Post by scott.a.mccullough on 2013-11-01
> **2F4U said:**
> Does executing these commands help?

  cd /var/lib/apt
  sudo mv lists lists.old
  sudo mkdir -p lists/partial
  sudo apt-get update

This will rebuild the cache.

If it doesn't help, this forum post has additional suggestions:

[http://ubuntuforums.org/showthread.php?t=1869890](http://ubuntuforums.org/showthread.php?t=1869890)


This sequence of commands fixed exactly this problem for me.

---

### Post by Akacheebe on 2014-03-16
> **2F4U said:**
> Does executing these commands help?

  cd /var/lib/apt
  sudo mv lists lists.old
  sudo mkdir -p lists/partial
  sudo apt-get update

This will rebuild the cache.

This one fixed the update errors on my system.

---

### Post by buminda on 2014-04-05
thx mate . this worked for me !!

---

### Post by sugat_itlog on 2014-07-12
I just change my download source.

my error was ... 
GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


You can do the above steps it just that you have to re-add the other repository that you had before renaming the lists folder. Its linux and you can do different methods but same result.

---

