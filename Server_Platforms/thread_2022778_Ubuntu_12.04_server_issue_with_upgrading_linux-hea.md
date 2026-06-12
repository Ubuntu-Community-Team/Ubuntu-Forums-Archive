---
title: "Ubuntu 12.04 server issue with upgrading linux-headers"
date: 2012-07-11
forum: Server Platforms
---

### Post by realmrealm on 2012-07-11
I'm trying to upgrade a 12.04 64bit server.

It should also be noted that this server is a VM in a VBox instance

```
sudo apt-get update
```works fine

but

When I go to do a
```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-headers-server linux-image-server linux-server
The following packages will be upgraded:
  accountsservice cron language-pack-en libaccountsservice0 libgnutls26
  linux-headers-3.2.0-25 python-crypto
7 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 1,027 kB/12.5 MB of archives.
After this operation, 56.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main cron amd64 3.0pl1-120ubuntu4 [85.0 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libgnutls26 amd64 2.12.14-5ubuntu3.1 [459 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main language-pack-en all 1:12.04+20120618 [115 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main accountsservice amd64 0.6.15-2ubuntu9.1 [44.1 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libaccountsservice0 amd64 0.6.15-2ubuntu9.1 [30.5 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main python-crypto amd64 2.4.1-1ubuntu0.1 [293 kB]
Fetched 1,027 kB in 6s (154 kB/s)                                                        
(Reading database ... 
dpkg: warning: files list file for package `linux-headers-3.2.0-25' missing, assuming package has no files currently installed.
(Reading database ... 52923 files and directories currently installed.)
Preparing to replace linux-headers-3.2.0-25 3.2.0-25.40 (using .../linux-headers-3.2.0-25_3.2.0-25.40_all.deb) ...
Unpacking replacement linux-headers-3.2.0-25 ...
```It freezes and does nothing. (i've let it go hours with nothing happening)

I have to exit out with a CTRL-Z and then I can't try again until I reboot. Even if I kill the dpkg job. Then when it comes back up I have to do a:
```
sudo dpkg --configure -a
```The /var/log/dpkg.log says:
```
2012-07-11 13:07:52 status half-installed linux-headers-3.2.0-25 3.2.0-25.40
2012-07-11 13:09:53 startup packages configure
2012-07-11 13:12:07 startup packages purge
2012-07-11 13:15:12 startup archives unpack
2012-07-11 13:15:12 upgrade linux-headers-3.2.0-25 3.2.0-25.40 3.2.0-25.40
2012-07-11 13:15:12 status half-installed linux-headers-3.2.0-25 3.2.0-25.40
2012-07-11 13:23:08 startup packages configure
2012-07-11 13:23:34 startup archives unpack
2012-07-11 13:23:35 upgrade linux-headers-3.2.0-25 3.2.0-25.40 3.2.0-25.40
2012-07-11 13:23:35 status half-installed linux-headers-3.2.0-25 3.2.0-25.40
```I've tried doing:
```
apt-get purge
``````
apt-get autoclean
``````
apt-get autoclean
``````
apt-get purge linux-headers-3.2.0-25
```None of these have worked, and I'm afraid I'm coming up empty with google searches. 

So what do you guys think?

Thanks in advance!

---

### Post by SeijiSensei on 2012-07-11
Try "sudo apt-get dist-upgrade" and see if that helps.  You might need to use the "-f" option as well.

---

