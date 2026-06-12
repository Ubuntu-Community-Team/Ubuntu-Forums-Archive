---
title: "startup problems U16.04 LTS LVM LUKS hdd encryption after recent kernel updates"
date: 2019-05-16
forum: Security
---

### Post by bakker-r on 2019-05-16
L.S. 

My pentium ibm pc running on Ubuntu 16.04 LTS has been installed with LUKS hdd encryption on LVM. Decryption at startup worked fine until lately. Since the latest updates, including a kernel update, the problems occur.  

  
 
After entering the key the decryption will start, but comes to a full stop before the startup is finished. Nothing is possible in that situation. The screen is frozen. The HDD is inactive. Switching off the power is the only way out.  

  
 
Restarting the system the GRUB loader shows up. After choosing Ubuntu the startup screen shows up. Entering the key results in a completed startup and normal usable system.  

  
 
Is there anyone who has a clue to what the problem might be and how this problem can be solved. I suppose there might be more of us with the same problem.   

 
Thanks, Jo

---

### Post by TheFu on 2019-05-16
Failing HDD.
Failing cable.
Failing disk controller.
Failing PSU.
Failing motherboard.

I hope you have excellent backups.

I've been using LUKS with LVM for a long time.  Using now on a 16.04 system. **Not seeing any issues as you've described.**

You can test by booting from alternate media, using "Try Ubuntu" option, opening the LUKS container, using vgscan to get the LVM PVs, VGs, and LVs recognized.  Then mount the LVs, as you need.

Hopefully, the Live-boot performs perfectly, which is what I would expect.  If it doesn't, that might be better news since it removes the disk subsystem from the likely issues.  OTOH, swapping a bad SATA cable is the cheapest to fix.  From the alternate boot media, you can also run SMART tests against the disk. Cable problems can be seen pretty easily.  A failing HDD, if SMART sees it, can be seen too by the number of relocated sectors and pending relocated sectors.  Interpreting SMART output takes getting used to.  Use google to look up each of the numbered parameters and pay attention to the raw values.

Cable, disk issues are the least hassle to fix and uncover. The others are harder.

---

### Post by bakker-r on 2019-05-17
Extra info.

The problems occurred on several PC systems after the same Ubuntu update. 
Before the UBUNTU update LUKS on LVM worked perfect on these systems from the first installation on. 

So that excludes failing hardware like HDD, cable, disk controller, PSU and motherboard.
On the other hand the hard reset by switching off the power on daily basis may cause failing hardware in some time.

---

### Post by ajgreeny on 2019-05-17
What were those updates that you think may have caused the problem, and on what date?

If you're not sure run command ```
grep -i " upgrade " /var/log/dpkg.log.1 /var/log/dpkg.log
``` look for the date in question in the list and you will see all the packages upgraded at that time.

---

### Post by bakker-r on 2019-05-18
It were the updates including the kernel updates. Not the yesterday updates 17th of may with kernel updates but the one before.  
Unfotunately I don´t see them with: grep -i " upgrade " /var/log/dpkg.log.1 /var/log/dpkg.log

I suppose it was the update at or around the 26th of april.
Here is my list with updates from the 17th of april until now.

```
/var/log/dpkg.log.1:2019-04-17 22:45:59 upgrade ntfs-3g:i386 1:2015.3.14AR.1-1ubuntu0.2 1:2015.3.14AR.1-1ubuntu0.3
/var/log/dpkg.log.1:2019-04-17 22:46:03 upgrade ubuntu-core-launcher:i386 2.37.4ubuntu0.1 2.38
/var/log/dpkg.log.1:2019-04-17 22:46:04 upgrade snapd:i386 2.37.4ubuntu0.1 2.38
/var/log/dpkg.log.1:2019-04-17 22:46:35 upgrade ubuntu-minimal:i386 1.361.2 1.361.3
/var/log/dpkg.log.1:2019-04-17 22:46:36 upgrade ubuntu-standard:i386 1.361.2 1.361.3
/var/log/dpkg.log.1:2019-04-17 22:46:37 upgrade firefox:i386 66.0.2+build1-0ubuntu0.16.04.1 66.0.3+build1-0ubuntu0.16.04.1
/var/log/dpkg.log.1:2019-04-17 22:47:00 upgrade firefox-locale-en:i386 66.0.2+build1-0ubuntu0.16.04.1 66.0.3+build1-0ubuntu0.16.04.1
/var/log/dpkg.log.1:2019-04-17 22:47:01 upgrade libsnapd-glib1:i386 1.33-0ubuntu0.16.04.1 1.47-0ubuntu0.16.04.0
/var/log/dpkg.log.1:2019-04-17 22:47:03 upgrade libxslt1.1:i386 1.1.28-2.1ubuntu0.1 1.1.28-2.1ubuntu0.2
/var/log/dpkg.log.1:2019-04-17 22:47:04 upgrade xsltproc:i386 1.1.28-2.1ubuntu0.1 1.1.28-2.1ubuntu0.2
/var/log/dpkg.log.1:2019-04-17 22:47:05 upgrade nordvpn:i386 2.2.0-3 3.0.0-1
/var/log/dpkg.log.1:2019-04-17 22:47:12 upgrade ubuntu-desktop:i386 1.361.2 1.361.3
/var/log/dpkg.log.1:2019-04-25 07:47:04 upgrade distro-info-data:all 0.28ubuntu0.10 0.28ubuntu0.11
/var/log/dpkg.log.1:2019-04-26 16:18:50 upgrade login:i386 1:4.2-3.1ubuntu5.3 1:4.2-3.1ubuntu5.4
/var/log/dpkg.log.1:2019-04-26 16:19:06 upgrade passwd:i386 1:4.2-3.1ubuntu5.3 1:4.2-3.1ubuntu5.4
/var/log/dpkg.log.1:2019-04-26 16:19:21 upgrade tzdata:all 2018i-0ubuntu0.16.04 2019a-0ubuntu0.16.04
/var/log/dpkg.log.1:2019-04-26 16:19:24 upgrade console-setup-linux:all 1.108ubuntu15.4 1.108ubuntu15.5
/var/log/dpkg.log.1:2019-04-26 16:19:27 upgrade console-setup:all 1.108ubuntu15.4 1.108ubuntu15.5
/var/log/dpkg.log.1:2019-04-26 16:19:31 upgrade keyboard-configuration:all 1.108ubuntu15.4 1.108ubuntu15.5
/var/log/dpkg.log.1:2019-04-26 16:19:35 upgrade libisc-export160:i386 1:9.10.3.dfsg.P4-8ubuntu1.12 1:9.10.3.dfsg.P4-8ubuntu1.14
/var/log/dpkg.log.1:2019-04-26 16:19:36 upgrade libdns-export162:i386 1:9.10.3.dfsg.P4-8ubuntu1.12 1:9.10.3.dfsg.P4-8ubuntu1.14
/var/log/dpkg.log.1:2019-04-26 16:19:37 upgrade bind9-host:i386 1:9.10.3.dfsg.P4-8ubuntu1.12 1:9.10.3.dfsg.P4-8ubuntu1.14
/var/log/dpkg.log.1:2019-04-26 16:19:39 upgrade dnsutils:i386 1:9.10.3.dfsg.P4-8ubuntu1.12 1:9.10.3.dfsg.P4-8ubuntu1.14
/var/log/dpkg.log.1:2019-04-26 16:19:40 upgrade libisc160:i386 1:9.10.3.dfsg.P4-8ubuntu1.12 1:9.10.3.dfsg.P4-8ubuntu1.14
/var/log/dpkg.log.1:2019-04-26 16:19:41 upgrade libdns162:i386 1:9.10.3.dfsg.P4-8ubuntu1.12 1:9.10.3.dfsg.P4-8ubuntu1.14
/var/log/dpkg.log.1:2019-04-26 16:19:43 upgrade libisccc140:i386 1:9.10.3.dfsg.P4-8ubuntu1.12 1:9.10.3.dfsg.P4-8ubuntu1.14
/var/log/dpkg.log.1:2019-04-26 16:19:44 upgrade libisccfg140:i386 1:9.10.3.dfsg.P4-8ubuntu1.12 1:9.10.3.dfsg.P4-8ubuntu1.14
/var/log/dpkg.log.1:2019-04-26 16:19:45 upgrade liblwres141:i386 1:9.10.3.dfsg.P4-8ubuntu1.12 1:9.10.3.dfsg.P4-8ubuntu1.14
/var/log/dpkg.log.1:2019-04-26 16:19:46 upgrade libbind9-140:i386 1:9.10.3.dfsg.P4-8ubuntu1.12 1:9.10.3.dfsg.P4-8ubuntu1.14
/var/log/dpkg.log.1:2019-04-26 16:20:13 upgrade linux-generic-hwe-16.04:i386 4.15.0.47.68 4.15.0.48.69
/var/log/dpkg.log.1:2019-04-26 16:20:14 upgrade linux-image-generic-hwe-16.04:i386 4.15.0.47.68 4.15.0.48.69
/var/log/dpkg.log.1:2019-04-26 16:20:49 upgrade linux-headers-generic-hwe-16.04:i386 4.15.0.47.68 4.15.0.48.69
/var/log/dpkg.log.1:2019-04-26 16:20:51 upgrade linux-libc-dev:i386 4.4.0-145.171 4.4.0-146.172
/var/log/dpkg.log.1:2019-04-26 16:20:53 upgrade nordvpn:i386 3.0.0-1 3.0.0-4
/var/log/dpkg.log:2019-05-02 07:13:39 upgrade evince:i386 3.18.2-1ubuntu4.3 3.18.2-1ubuntu4.4
/var/log/dpkg.log:2019-05-02 07:13:46 upgrade libevdocument3-4:i386 3.18.2-1ubuntu4.3 3.18.2-1ubuntu4.4
/var/log/dpkg.log:2019-05-02 07:13:52 upgrade libgstreamer-plugins-base1.0-0:i386 1.8.3-1ubuntu0.2 1.8.3-1ubuntu0.3
/var/log/dpkg.log:2019-05-02 07:13:58 upgrade gstreamer1.0-plugins-base:i386 1.8.3-1ubuntu0.2 1.8.3-1ubuntu0.3
/var/log/dpkg.log:2019-05-02 07:14:00 upgrade libevview3-3:i386 3.18.2-1ubuntu4.3 3.18.2-1ubuntu4.4
/var/log/dpkg.log:2019-05-02 07:14:01 upgrade evince-common:all 3.18.2-1ubuntu4.3 3.18.2-1ubuntu4.4
/var/log/dpkg.log:2019-05-02 07:14:11 upgrade gir1.2-gst-plugins-base-1.0:i386 1.8.3-1ubuntu0.2 1.8.3-1ubuntu0.3
/var/log/dpkg.log:2019-05-02 07:14:12 upgrade gstreamer1.0-alsa:i386 1.8.3-1ubuntu0.2 1.8.3-1ubuntu0.3
/var/log/dpkg.log:2019-05-02 07:14:14 upgrade gstreamer1.0-plugins-base-apps:i386 1.8.3-1ubuntu0.2 1.8.3-1ubuntu0.3
/var/log/dpkg.log:2019-05-02 07:14:18 upgrade gstreamer1.0-x:i386 1.8.3-1ubuntu0.2 1.8.3-1ubuntu0.3
/var/log/dpkg.log:2019-05-02 22:27:53 upgrade iproute2:i386 4.3.0-1ubuntu3.16.04.4 4.3.0-1ubuntu3.16.04.5
/var/log/dpkg.log:2019-05-02 22:27:56 upgrade libldap-2.4-2:i386 2.4.42+dfsg-2ubuntu3.4 2.4.42+dfsg-2ubuntu3.5
/var/log/dpkg.log:2019-05-02 22:27:57 upgrade unity:i386 7.4.5+16.04.20180221-0ubuntu1 7.4.5+16.04.20190312-0ubuntu1
/var/log/dpkg.log:2019-05-02 22:27:59 upgrade libunity-core-6.0-9:i386 7.4.5+16.04.20180221-0ubuntu1 7.4.5+16.04.20190312-0ubuntu1
/var/log/dpkg.log:2019-05-02 22:28:01 upgrade unity-schemas:all 7.4.5+16.04.20180221-0ubuntu1 7.4.5+16.04.20190312-0ubuntu1
/var/log/dpkg.log:2019-05-02 22:28:02 upgrade unity-services:i386 7.4.5+16.04.20180221-0ubuntu1 7.4.5+16.04.20190312-0ubuntu1
/var/log/dpkg.log:2019-05-02 22:44:59 upgrade ureadahead:i386 0.100.0-19 0.100.0-19.1
/var/log/dpkg.log:2019-05-04 10:33:09 upgrade unattended-upgrades:all 0.90ubuntu0.10 1.1ubuntu1.18.04.7~16.04.2
/var/log/dpkg.log:2019-05-06 21:08:26 upgrade sudo:i386 1.8.16-0ubuntu1.5 1.8.16-0ubuntu1.6
/var/log/dpkg.log:2019-05-07 13:57:51 upgrade distro-info-data:all 0.28ubuntu0.11 0.28ubuntu0.12
/var/log/dpkg.log:2019-05-08 09:29:47 upgrade grub-pc:i386 2.02~beta2-36ubuntu3.21 2.02~beta2-36ubuntu3.22
/var/log/dpkg.log:2019-05-08 09:29:48 upgrade grub-pc-bin:i386 2.02~beta2-36ubuntu3.21 2.02~beta2-36ubuntu3.22
/var/log/dpkg.log:2019-05-08 09:29:50 upgrade grub2-common:i386 2.02~beta2-36ubuntu3.21 2.02~beta2-36ubuntu3.22
/var/log/dpkg.log:2019-05-08 09:29:52 upgrade grub-common:i386 2.02~beta2-36ubuntu3.21 2.02~beta2-36ubuntu3.22
/var/log/dpkg.log:2019-05-08 09:29:59 upgrade wpasupplicant:i386 2.4-0ubuntu6.4 2.4-0ubuntu6.5
/var/log/dpkg.log:2019-05-10 12:21:01 upgrade cups-browsed:i386 1.8.3-2ubuntu3.4 1.8.3-2ubuntu3.5
/var/log/dpkg.log:2019-05-10 12:21:08 upgrade libcupsfilters1:i386 1.8.3-2ubuntu3.4 1.8.3-2ubuntu3.5
/var/log/dpkg.log:2019-05-10 12:21:09 upgrade cups-filters-core-drivers:i386 1.8.3-2ubuntu3.4 1.8.3-2ubuntu3.5
/var/log/dpkg.log:2019-05-10 12:21:12 upgrade libfontembed1:i386 1.8.3-2ubuntu3.4 1.8.3-2ubuntu3.5
/var/log/dpkg.log:2019-05-10 12:21:13 upgrade ghostscript:i386 9.26~dfsg+0-0ubuntu0.16.04.8 9.26~dfsg+0-0ubuntu0.16.04.9
/var/log/dpkg.log:2019-05-10 12:21:15 upgrade ghostscript-x:i386 9.26~dfsg+0-0ubuntu0.16.04.8 9.26~dfsg+0-0ubuntu0.16.04.9
/var/log/dpkg.log:2019-05-10 12:21:17 upgrade libgs9:i386 9.26~dfsg+0-0ubuntu0.16.04.8 9.26~dfsg+0-0ubuntu0.16.04.9
/var/log/dpkg.log:2019-05-10 12:21:20 upgrade libgs9-common:all 9.26~dfsg+0-0ubuntu0.16.04.8 9.26~dfsg+0-0ubuntu0.16.04.9
/var/log/dpkg.log:2019-05-10 12:21:24 upgrade cups-filters:i386 1.8.3-2ubuntu3.4 1.8.3-2ubuntu3.5
/var/log/dpkg.log:2019-05-10 12:21:25 upgrade firefox-locale-en:i386 66.0.3+build1-0ubuntu0.16.04.1 66.0.4+build3-0ubuntu0.16.04.1
/var/log/dpkg.log:2019-05-10 12:21:27 upgrade firefox-locale-nl:i386 66.0.3+build1-0ubuntu0.16.04.1 66.0.4+build3-0ubuntu0.16.04.1
/var/log/dpkg.log:2019-05-14 17:05:39 upgrade samba-libs:i386 2:4.3.11+dfsg-0ubuntu0.16.04.19 2:4.3.11+dfsg-0ubuntu0.16.04.20
/var/log/dpkg.log:2019-05-14 17:05:44 upgrade libwbclient0:i386 2:4.3.11+dfsg-0ubuntu0.16.04.19 2:4.3.11+dfsg-0ubuntu0.16.04.20
/var/log/dpkg.log:2019-05-14 17:05:45 upgrade libsmbclient:i386 2:4.3.11+dfsg-0ubuntu0.16.04.19 2:4.3.11+dfsg-0ubuntu0.16.04.20
/var/log/dpkg.log:2019-05-14 17:05:46 upgrade lshw:i386 02.17-1.1ubuntu3.5 02.17-1.1ubuntu3.6
/var/log/dpkg.log:2019-05-14 17:05:48 upgrade firefox:i386 66.0.4+build3-0ubuntu0.16.04.1 66.0.5+build1-0ubuntu0.16.04.1
/var/log/dpkg.log:2019-05-14 17:06:14 upgrade firefox-locale-en:i386 66.0.4+build3-0ubuntu0.16.04.1 66.0.5+build1-0ubuntu0.16.04.1
/var/log/dpkg.log:2019-05-14 17:06:15 upgrade firefox-locale-nl:i386 66.0.4+build3-0ubuntu0.16.04.1 66.0.5+build1-0ubuntu0.16.04.1
/var/log/dpkg.log:2019-05-14 17:06:16 upgrade nordvpn:i386 3.0.0-4 3.0.1-1
/var/log/dpkg.log:2019-05-17 11:27:24 upgrade debconf-i18n:all 1.5.58ubuntu1 1.5.58ubuntu2
/var/log/dpkg.log:2019-05-17 11:27:26 upgrade debconf:all 1.5.58ubuntu1 1.5.58ubuntu2
/var/log/dpkg.log:2019-05-17 11:27:40 upgrade cups-core-drivers:i386 2.1.3-4ubuntu0.7 2.1.3-4ubuntu0.8
/var/log/dpkg.log:2019-05-17 11:27:41 upgrade cups-server-common:all 2.1.3-4ubuntu0.7 2.1.3-4ubuntu0.8
/var/log/dpkg.log:2019-05-17 11:27:43 upgrade cups-common:all 2.1.3-4ubuntu0.7 2.1.3-4ubuntu0.8
/var/log/dpkg.log:2019-05-17 11:27:45 upgrade libcupscgi1:i386 2.1.3-4ubuntu0.7 2.1.3-4ubuntu0.8
/var/log/dpkg.log:2019-05-17 11:27:46 upgrade cups-client:i386 2.1.3-4ubuntu0.7 2.1.3-4ubuntu0.8
/var/log/dpkg.log:2019-05-17 11:27:48 upgrade libcupsimage2:i386 2.1.3-4ubuntu0.7 2.1.3-4ubuntu0.8
/var/log/dpkg.log:2019-05-17 11:27:49 upgrade libcupsppdc1:i386 2.1.3-4ubuntu0.7 2.1.3-4ubuntu0.8
/var/log/dpkg.log:2019-05-17 11:27:50 upgrade cups-daemon:i386 2.1.3-4ubuntu0.7 2.1.3-4ubuntu0.8
/var/log/dpkg.log:2019-05-17 11:27:57 upgrade libcupsmime1:i386 2.1.3-4ubuntu0.7 2.1.3-4ubuntu0.8
/var/log/dpkg.log:2019-05-17 11:27:58 upgrade libcups2:i386 2.1.3-4ubuntu0.7 2.1.3-4ubuntu0.8
/var/log/dpkg.log:2019-05-17 11:28:00 upgrade cups:i386 2.1.3-4ubuntu0.7 2.1.3-4ubuntu0.8
/var/log/dpkg.log:2019-05-17 11:28:02 upgrade cups-bsd:i386 2.1.3-4ubuntu0.7 2.1.3-4ubuntu0.8
/var/log/dpkg.log:2019-05-17 11:28:04 upgrade cups-ppdc:i386 2.1.3-4ubuntu0.7 2.1.3-4ubuntu0.8
/var/log/dpkg.log:2019-05-17 11:28:33 upgrade intel-microcode:i386 3.20180807a.0ubuntu0.16.04.1 3.20190514.0ubuntu0.16.04.1
/var/log/dpkg.log:2019-05-17 11:28:35 upgrade linux-generic-hwe-16.04:i386 4.15.0.48.69 4.15.0.50.71
/var/log/dpkg.log:2019-05-17 11:28:36 upgrade linux-image-generic-hwe-16.04:i386 4.15.0.48.69 4.15.0.50.71
/var/log/dpkg.log:2019-05-17 11:29:10 upgrade linux-headers-generic-hwe-16.04:i386 4.15.0.48.69 4.15.0.50.71
/var/log/dpkg.log:2019-05-17 11:29:11 upgrade linux-libc-dev:i386 4.4.0-146.172 4.4.0-148.174
```

---

