---
title: "How to configure LDAP on Ubuntu"
date: 2017-02-27
forum: Server Platforms
---

### Post by lifer84 on 2017-02-27
Hi All,

I am fairly new to Ubuntu and i want to setup a LDAP server in my machine on Ubuntu 14.04.
I ran the following commands -

sudo apt-get update
sudo apt-get install slapd ldap-utils

After running - sudo apt-get install slapd ldap-utils i got the follwing error

gourav@gourav-Lenovo-G50-80:~$ sudo apt-get install slapd ldap-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ldap-utils is already the newest version.
slapd is already the newest version.
The following packages were automatically installed and are no longer required:
  libjpeg62 libsigsegv2 linux-headers-4.4.0-31 linux-headers-4.4.0-31-generic
  linux-headers-4.4.0-45 linux-headers-4.4.0-45-generic
  linux-image-4.4.0-31-generic linux-image-4.4.0-45-generic
  linux-image-extra-4.4.0-31-generic linux-image-extra-4.4.0-45-generic
  linux-signed-image-4.4.0-45-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 54 not upgraded.
1 not fully installed or removed.
Need to get 0 B/15.0 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
dpkg: error processing package libsigsegv2:amd64 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
Errors were encountered while processing:
 libsigsegv2:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)
gourav@gourav-Lenovo-G50-80:~$ 

Please help me setup this LDAP on Ubuntu, also any information related to configuring LDAP on Ubuntu will be highly appreciated.

Thanks.

---

### Post by marchello_lippi2 on 2017-03-15
Hi, the link below describes ubuntu 12.04, but still should be what you need
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-a-basic-ldap-server-on-an-ubuntu-12-04-vps](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-a-basic-ldap-server-on-an-ubuntu-12-04-vps)

---

### Post by cariboo on 2017-03-15
Moved here, as you may get help quicker.

---

### Post by TheFu on 2017-03-20
What you need to do depends on the goals for using LDAP.

Many webapps will hook into LDAP for end-user logins just fine. Each webapp will have a different how-to for LDAP.  Supporting Unix/Linux logins is a little different. There's a schema addition which adds the POSIX scheme/fields.  You'll want to decide how much you want to secure access to different parts of the LDAP DB. Which parts of the LDAP DB needs to be accessible by different class of users for different purposes.

I wimped out and used the LDAP built into my communications server for system logins and webapp access. Not quite SSO, but at least we only had 1 account/password to access all our corporate systems and only 1 REALLY STRONG password to access everything.  Plus the password could be changed only through the email webapp system.

If I were doing this again, I'd deploy FreeIPA on a CentOS VM for the LDAP and management, then use Ubuntu for all my clients. FreeIPA is a mess of f/loss projects and different languages all belted together. There was an effort to port it to Debian/Ubuntu, but I don't think that was successful. I haven't looked at it recently, so that may have been solved.

---

