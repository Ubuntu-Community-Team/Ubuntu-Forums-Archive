---
title: "Can't play DVD in 16.04 beta"
date: 2016-03-25
forum: Ubuntu Development Version
---

### Post by stoc2528 on 2016-03-25
I've been unable to play DVD's in Ubuntu 16.04 for some time. I just installed 16.04 beta 2 that was released today and still can't.  DVD's play perfectly in 14.04.  I've installed DVD support for 15.10 and newer per instructions below but it still won't work.

[h=2]Ubuntu 15.10 and newer[/h] From Ubuntu 15.10 onwards, libdvd-pkg is available to ease the installation of libdvdcss. 

[LIST]
[*]Install the **libdvd-pkg** package (**no need to add third party repositories**) via Synaptic or command line: 
[/LIST]
sudo apt-get install libdvd-pkgFollow libdvd-pkg's instructions to let it download, compile, and install libdvdcss. but still can't

---

### Post by howefield on 2016-03-25
Moved to the "*Ubuntu Development Version*" forum.

---

### Post by QDR06VV9 on 2016-03-25
> **stoc2528 said:**
> I've been unable to play DVD's in Ubuntu 16.04 for some time. I just installed 16.04 beta 2 that was released today and still can't.  DVD's play perfectly in 14.04.  I've installed DVD support for 15.10 and newer per instructions below but it still won't work.

**Ubuntu 15.10 and newer**

 From Ubuntu 15.10 onwards, libdvd-pkg is available to ease the installation of libdvdcss. 

[LIST]
[*]Install the **libdvd-pkg** package (**no need to add third party repositories**) via Synaptic or command line: 
[/LIST]
sudo apt-get install libdvd-pkgFollow libdvd-pkg's instructions to let it download, compile, and install libdvdcss. but still can't


For 32 and 64 bit versions of "libdvdcss2", direct download below, just install with Gdebi after download:

[http://mirror.home-dn.net/debian-multimedia/pool/main/libd/libdvdcss/](http://mirror.home-dn.net/debian-multimedia/pool/main/libd/libdvdcss/)
Regards

---

### Post by stoc2528 on 2016-03-25
Already have libdvdcss installed:

"libdvdcss2 is already the newest version (1.4.0-1~local)"

---

### Post by QDR06VV9 on 2016-03-25
> **stoc2528 said:**
> Already have libdvdcss installed:

"libdvdcss2 is already the newest version (1.4.0-1~local)"
That's Odd? Try this...fingers crossed.
```
sudo dpkg-reconfigure libdvd-pkg
```

---

### Post by Doug S on 2016-03-25
It doesn't seem to work for me either.

I had to go: "sudo dpkg-reconfigure libdvd-pkg", as runirckus mentioned; Then it wanted me to install extra multimedia plugins; Then it wanted me to install extra multimedia plugins again, although it was much much more stuff involved the second time; Then it started to play the movie DVD but stopped after a few seconds saying "An error occurred - Internal data flow error" (repeatable).

---

### Post by QDR06VV9 on 2016-03-25
Ahh Yes I also forgot this from a few months back mc4man had posted: [http://ubuntuforums.org/archive/index.php/t-2312060.html](http://ubuntuforums.org/archive/index.php/t-2312060.html)
> At least here "sudo apt-get install libdvd-pkg" didn't actually install libdvdcss2, just libdvd-pkg, as in - 
"Setting up libdvd-pkg (1.4.0-1-1) ...
libdvd-pkg: dpkg database is locked. You may need to use command "sudo dpkg-reconfigure libdvd-pkg".

(- there was obviously nothing else locking  dpkg other than the above orig apt-get command.
Running the suggested command actually did get, build & install libdvdcss2

As far as vlc - "core input error: ES_OUT_RESET_PCR called" is  irrelevant to your dvd playback issues, just typical vlc nonsense.

I'd, in order, for 16.04 - 
make sure libdvdcss2 is actually installed
**delete ~/.dvdcss folder**
With dvd already in your drive (assumes default device of /dev/sr0)  start vlc as such & see if dvd plays. If not read thru log file in  Home folder

export DVDCSS_METHOD=title && export DVDCSS_VERBOSE=2
followed by 

export LIBOVERLAY_SCROLLBAR=0 && vlc dvd:// > vlc_output.log 2>&1
Where he suggested removing [B]delete ~/.dvdcss folder
[/B]Thanks for memory-jog Doug S

---

### Post by sudodus on 2016-03-25
I tried in my installed system, and it works to play a DVD movie. I have installed the whole lubuntu-restricted-extras.

---

### Post by Frogs Hair on 2016-03-25
```
sudo dpkg-reconfigure libdvd-pkg
``` 

This worked for me. I hadn't tried a DVD yet . Thanks :)

---

### Post by cariboo on 2016-03-25
I'm running an install from October, added ubuntu-restricted extra plus depends, then installed libdvd-pkg, and handbrake, as I wanted to backup my Buffy dvd set. Dvd's play using either VLC or Videos, I did get a region error once, but otherwise everything plays as it should.

---

### Post by Cavsfan on 2016-03-25
I got a DVD to play in Xubuntu 16.04. It would not play at first but I installed **libdvd-pkg** with apt instead of apt-get this time (for about the first time ever :p) FWIW.

It installed some other stuff and then a blue screen asked me to run **sudo dpkg-reconfigure libdvd-pkg** when finished.
That installed **libdvdcss_1.4.0.orig.tar.bz2**. 

Here's the entire terminal output. All I had to do was eject the DVD and re-insert it and then I opened Parole Media Player and then opened the DVD and it played Fast and Furious from 2001.

```
cavsfan@cavsfan-le-beast:~$ sudo apt install libdvd-pkg
[sudo] password for cavsfan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  autopoint dh-autoreconf
The following NEW packages will be installed:
  autopoint dh-autoreconf libdvd-pkg
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 436 kB of archives.
After this operation, 580 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 autopoint all 0.19.7-2ubuntu3 [406 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 dh-autoreconf all 11 [15.8 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial/multiverse amd64 libdvd-pkg all 1.4.0-1-1 [14.9 kB]
Fetched 436 kB in 0s (998 kB/s)      
Preconfiguring packages ...
Selecting previously unselected package autopoint.
(Reading database ... 227081 files and directories currently installed.)
Preparing to unpack .../autopoint_0.19.7-2ubuntu3_all.deb ...
Unpacking autopoint (0.19.7-2ubuntu3) ...
Selecting previously unselected package dh-autoreconf.
Preparing to unpack .../dh-autoreconf_11_all.deb ...
Unpacking dh-autoreconf (11) ...
Selecting previously unselected package libdvd-pkg.
Preparing to unpack .../libdvd-pkg_1.4.0-1-1_all.deb ...
Unpacking libdvd-pkg (1.4.0-1-1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up autopoint (0.19.7-2ubuntu3) ...
Setting up dh-autoreconf (11) ...
Setting up libdvd-pkg (1.4.0-1-1) ...
libdvd-pkg: dpkg database is locked. You may need to use command "sudo dpkg-reconfigure libdvd-pkg".
libdvd-pkg: Building and installation of package(s) [libdvdcss2 libdvdcss-dev] postponed till after next APT operation.
cavsfan@cavsfan-le-beast:~$ sudo dpkg-reconfigure libdvd-pkg
libdvd-pkg: Downloading orig source...
I: libdvdcss_1.4.0
/usr/bin/wget --tries=3 --timeout=40 --read-timeout=40 --continue -O libdvdcss_1.4.0.orig.tar.bz2 \
          http://download.videolan.org/pub/libdvdcss/1.4.0/libdvdcss-1.4.0.tar.bz2 \
        || /usr/bin/uscan --noconf --verbose --rename --destdir=/usr/src/libdvd-pkg --check-dirname-level=0 --force-download --download-current-version /usr/share/libdvd-pkg/debian
--2016-03-25 18:10:24--  http://download.videolan.org/pub/libdvdcss/1.4.0/libdvdcss-1.4.0.tar.bz2
Resolving download.videolan.org (download.videolan.org)... 88.191.250.2, 2a01:e0d:1:3:58bf:fa02:c0de:5
Connecting to download.videolan.org (download.videolan.org)|88.191.250.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 364373 (356K) [application/octet-stream]
Saving to: ‘libdvdcss_1.4.0.orig.tar.bz2’

libdvdcss_1.4.0.orig.tar.bz2                                        100%[=================================================================================================================================================================>] 355.83K   694KB/s    in 0.5s    

2016-03-25 18:10:25 (694 KB/s) - ‘libdvdcss_1.4.0.orig.tar.bz2’ saved [364373/364373]

libdvd-pkg: Checking orig.tar integrity...
/usr/src/libdvd-pkg/libdvdcss_1.4.0.orig.tar.bz2: OK
libdvd-pkg: Unpacking and configuring...
libdvd-pkg: Building the package... (it may take a while)
libdvd-pkg: Build log will be saved to /usr/src/libdvd-pkg/libdvdcss2_1.4.0-1~local_amd64.build
Current: = cap_chown,cap_dac_override,cap_dac_read_search,cap_fowner,cap_fsetid,cap_kill,cap_setgid,cap_setuid,cap_setpcap,cap_linux_immutable,cap_net_bind_service,cap_net_broadcast,cap_net_admin,cap_net_raw,cap_ipc_lock,cap_ipc_owner,cap_sys_module,cap_sys_rawio,cap_sys_chroot,cap_sys_ptrace,cap_sys_pacct,cap_sys_admin,cap_sys_boot,cap_sys_nice,cap_sys_resource,cap_sys_time,cap_sys_tty_config,cap_mknod,cap_lease,cap_audit_write,cap_audit_control,cap_setfcap,cap_mac_override,cap_mac_admin,cap_syslog,cap_wake_alarm,cap_block_suspend,37+ep
Bounding set =cap_chown,cap_dac_override,cap_fowner,cap_wake_alarm,cap_block_suspend,37
Securebits: 024/0x14/5'b10100
 secure-noroot: no (unlocked)
 secure-no-suid-fixup: yes (unlocked)
 secure-keep-caps: yes (unlocked)
uid=0(root)
gid=0(root)
groups=0(root)
libdvd-pkg: Installing...
Selecting previously unselected package libdvdcss-dev:amd64.
(Reading database ... 227130 files and directories currently installed.)
Preparing to unpack .../libdvdcss-dev_1.4.0-1~local_amd64.deb ...
Unpacking libdvdcss-dev:amd64 (1.4.0-1~local) ...
Selecting previously unselected package libdvdcss2:amd64.
Preparing to unpack .../libdvdcss2_1.4.0-1~local_amd64.deb ...
Unpacking libdvdcss2:amd64 (1.4.0-1~local) ...
Setting up libdvdcss2:amd64 (1.4.0-1~local) ...
Setting up libdvdcss-dev:amd64 (1.4.0-1~local) ...
Processing triggers for libc-bin (2.23-0ubuntu2) ...

```

Hope this helps.

---

### Post by stoc2528 on 2016-03-25
When I run:  sudo dpkg-reconfigure libdvd-pkg    

I get: libdvd-pkg: guest package [libdvdcss2/1.4.0-1~local] is already installed

...But it's now playing DVD's   I don't get it?

Thanks for the help guys!

---

