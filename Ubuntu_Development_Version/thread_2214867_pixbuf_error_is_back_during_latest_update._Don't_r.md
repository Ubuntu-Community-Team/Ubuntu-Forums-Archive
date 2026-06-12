---
title: "pixbuf error is back during latest update. Don't reboot without fixing it first."
date: 2014-04-03
forum: Ubuntu Development Version
---

### Post by philinux on 2014-04-03
The error says to run this :-

```
gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache 
```

You need sudo -i first. It should tell you you need a pixbuf dev package installing. Do that then run the above code. All good to reboot.

---

### Post by wgarcia on 2014-04-03
Shouldn't it be:

```
gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
```

you seem to be missing an "e" at the end.

---

### Post by sdowney717 on 2014-04-03
I have seen that error before but never did anything with it. Reboots ok.
Why the mention about running that command before rebooting?

---

### Post by anca-emanuel on 2014-04-03
[https://bugs.launchpad.net/ubuntu/+source/gdk-pixbuf/+bug/619003](https://bugs.launchpad.net/ubuntu/+source/gdk-pixbuf/+bug/619003)

---

### Post by philinux on 2014-04-03
> **sdowney717 said:**
> I have seen that error before but never did anything with it. Reboots ok.
Why the mention about running that command before rebooting?

Because you end up with total system failure just after login.

Fixable from tty of course.

---

### Post by grahammechanical on 2014-04-03
> [COLOR=#000000]Because you end up with total system failure just after login.[/COLOR]

Not on my machine. Earlier today I updated. Which brought in the pixbuf update and required a reboot = no problems. Then after a couple of hours I shut down to rest my eyes and I have since rebooted without any problems. I decided to run that command anyway. I got this.

> The program 'gdk-pixbuf-query-loaders' is currently not installed. You can install it by typing: apt-get install libgdk-pixbuf2.0-dev

Which I did and then I ran the command. Well, in for a penny. In for a pound. Thanks anyway for the heads up. I guess the fact that some of us get these bugs and others do not is down to Phased Updates.

Regards.

---

### Post by philinux on 2014-04-03
+1 Graham.

I've only seen this before on my desktop.  Laptop got hit today after an update and dist-upgrade. Nothing to remove etc. But on rebooting. Nada.

---

### Post by sdowney717 on 2014-04-03
scott@scott-P5QC:~$ sudo gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
bash: /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache: Permission denied
scott@scott-P5QC:~$ 

wont run with sudo?

```
scott@scott-P5QC:~$ sudo apt-get install libgdk-pixbuf2.0-dev
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libglib2.0-dev libpcre3-dev libpng12-dev libpthread-stubs0-dev libx11-dev
  libx11-doc libxau-dev libxcb1-dev libxdmcp-dev x11proto-core-dev
  x11proto-input-dev x11proto-kb-dev xorg-sgml-doctools xtrans-dev zlib1g-dev
Suggested packages:
  libglib2.0-doc libxcb-doc
The following NEW packages will be installed:
  libgdk-pixbuf2.0-dev libglib2.0-dev libpcre3-dev libpng12-dev
  libpthread-stubs0-dev libx11-dev libx11-doc libxau-dev libxcb1-dev
  libxdmcp-dev x11proto-core-dev x11proto-input-dev x11proto-kb-dev
  xorg-sgml-doctools xtrans-dev zlib1g-dev
0 upgraded, 16 newly installed, 0 to remove and 6 not upgraded.
Need to get 5,422 kB of archives.
After this operation, 28.9 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/main libpcre3-dev amd64 1:8.31-2ubuntu2 [237 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty/main zlib1g-dev amd64 1:1.2.8.dfsg-1ubuntu1 [183 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty/main libglib2.0-dev amd64 2.40.0-1ubuntu1 [1,319 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty/main xorg-sgml-doctools all 1:1.11-1 [12.9 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty/main x11proto-core-dev all 7.0.24-1 [748 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ trusty/main libxau-dev amd64 1:1.0.8-1 [11.1 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ trusty/main libxdmcp-dev amd64 1:1.1.1-1 [26.9 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ trusty/main x11proto-input-dev all 2.3-1 [139 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ trusty/main x11proto-kb-dev all 1.0.6-2 [269 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ trusty/main xtrans-dev all 1.3.2-1 [69.9 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ trusty/main libpthread-stubs0-dev amd64 0.3-4 [4,068 B]
Get:12 http://us.archive.ubuntu.com/ubuntu/ trusty/main libxcb1-dev amd64 1.10-2ubuntu1 [76.6 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ trusty/main libx11-dev amd64 2:1.6.2-1ubuntu2 [629 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ trusty/main libpng12-dev amd64 1.2.50-1ubuntu2 [206 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ trusty/main libgdk-pixbuf2.0-dev amd64 2.30.7-0ubuntu1 [42.9 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu/ trusty/main libx11-doc all 2:1.6.2-1ubuntu2 [1,448 kB]
Fetched 5,422 kB in 7s (773 kB/s)                                              
Selecting previously unselected package libpcre3-dev:amd64.
(Reading database ... 387632 files and directories currently installed.)
Preparing to unpack .../libpcre3-dev_1%3a8.31-2ubuntu2_amd64.deb ...
Unpacking libpcre3-dev:amd64 (1:8.31-2ubuntu2) ...
Selecting previously unselected package zlib1g-dev:amd64.
Preparing to unpack .../zlib1g-dev_1%3a1.2.8.dfsg-1ubuntu1_amd64.deb ...
Unpacking zlib1g-dev:amd64 (1:1.2.8.dfsg-1ubuntu1) ...
Selecting previously unselected package libglib2.0-dev.
Preparing to unpack .../libglib2.0-dev_2.40.0-1ubuntu1_amd64.deb ...
Unpacking libglib2.0-dev (2.40.0-1ubuntu1) ...
Selecting previously unselected package xorg-sgml-doctools.
Preparing to unpack .../xorg-sgml-doctools_1%3a1.11-1_all.deb ...
Unpacking xorg-sgml-doctools (1:1.11-1) ...
Selecting previously unselected package x11proto-core-dev.
Preparing to unpack .../x11proto-core-dev_7.0.24-1_all.deb ...
Unpacking x11proto-core-dev (7.0.24-1) ...
Selecting previously unselected package libxau-dev:amd64.
Preparing to unpack .../libxau-dev_1%3a1.0.8-1_amd64.deb ...
Unpacking libxau-dev:amd64 (1:1.0.8-1) ...
Selecting previously unselected package libxdmcp-dev:amd64.
Preparing to unpack .../libxdmcp-dev_1%3a1.1.1-1_amd64.deb ...
Unpacking libxdmcp-dev:amd64 (1:1.1.1-1) ...
Selecting previously unselected package x11proto-input-dev.
Preparing to unpack .../x11proto-input-dev_2.3-1_all.deb ...
Unpacking x11proto-input-dev (2.3-1) ...
Selecting previously unselected package x11proto-kb-dev.
Preparing to unpack .../x11proto-kb-dev_1.0.6-2_all.deb ...
Unpacking x11proto-kb-dev (1.0.6-2) ...
Selecting previously unselected package xtrans-dev.
Preparing to unpack .../xtrans-dev_1.3.2-1_all.deb ...
Unpacking xtrans-dev (1.3.2-1) ...
Selecting previously unselected package libpthread-stubs0-dev:amd64.
Preparing to unpack .../libpthread-stubs0-dev_0.3-4_amd64.deb ...
Unpacking libpthread-stubs0-dev:amd64 (0.3-4) ...
Selecting previously unselected package libxcb1-dev:amd64.
Preparing to unpack .../libxcb1-dev_1.10-2ubuntu1_amd64.deb ...
Unpacking libxcb1-dev:amd64 (1.10-2ubuntu1) ...
Selecting previously unselected package libx11-dev:amd64.
Preparing to unpack .../libx11-dev_2%3a1.6.2-1ubuntu2_amd64.deb ...
Unpacking libx11-dev:amd64 (2:1.6.2-1ubuntu2) ...
Selecting previously unselected package libpng12-dev.
Preparing to unpack .../libpng12-dev_1.2.50-1ubuntu2_amd64.deb ...
Unpacking libpng12-dev (1.2.50-1ubuntu2) ...
Selecting previously unselected package libgdk-pixbuf2.0-dev.
Preparing to unpack .../libgdk-pixbuf2.0-dev_2.30.7-0ubuntu1_amd64.deb ...
Unpacking libgdk-pixbuf2.0-dev (2.30.7-0ubuntu1) ...
Selecting previously unselected package libx11-doc.
Preparing to unpack .../libx11-doc_2%3a1.6.2-1ubuntu2_all.deb ...
Unpacking libx11-doc (2:1.6.2-1ubuntu2) ...
Processing triggers for man-db (2.6.6-1) ...
Processing triggers for libglib2.0-0:i386 (2.40.0-1ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.40.0-1ubuntu1) ...
Setting up libpcre3-dev:amd64 (1:8.31-2ubuntu2) ...
Setting up zlib1g-dev:amd64 (1:1.2.8.dfsg-1ubuntu1) ...
Setting up libglib2.0-dev (2.40.0-1ubuntu1) ...
Setting up xorg-sgml-doctools (1:1.11-1) ...
Setting up x11proto-core-dev (7.0.24-1) ...
Setting up libxau-dev:amd64 (1:1.0.8-1) ...
Setting up libxdmcp-dev:amd64 (1:1.1.1-1) ...
Setting up x11proto-input-dev (2.3-1) ...
Setting up x11proto-kb-dev (1.0.6-2) ...
Setting up xtrans-dev (1.3.2-1) ...
Setting up libpthread-stubs0-dev:amd64 (0.3-4) ...
Setting up libxcb1-dev:amd64 (1.10-2ubuntu1) ...
Setting up libx11-dev:amd64 (2:1.6.2-1ubuntu2) ...
Setting up libpng12-dev (1.2.50-1ubuntu2) ...
Setting up libgdk-pixbuf2.0-dev (2.30.7-0ubuntu1) ...
Setting up libx11-doc (2:1.6.2-1ubuntu2) ...
scott@scott-P5QC:~$ gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
bash: /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache: Permission denied
scott@scott-P5QC:~$ sudo gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
bash: /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache: Permission denied
scott@scott-P5QC:~$ sudo gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
bash: /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache: Permission denied
scott@scott-P5QC:~$ sudo gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
bash: /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache: Permission denied
scott@scott-P5QC:~$ 

```

---

### Post by sdowney717 on 2014-04-03
ok, got it to run, first had to sudo -s

```
scott@scott-P5QC:~$ sudo -s
root@scott-P5QC:~#  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
root@scott-P5QC:~# 

```

---

### Post by zika on 2014-04-03
All that can be done in one line with tee... ;)
Not tea but tee... ;) Tea could be useful also as stimulus...
Do not we have every U+1 round couple of these situations?

---

### Post by PaulBx on 2014-08-07
I got this today on my upgrade. It said that loaders.cache file was missing but when I looked there the file did exist. So I didn't run that suggested command as I guessed it was for creating the file, and rebooted. Everything looks OK so far.

I see this is a very old bug. I guess it is intermittent so it is hard to diagnose?

I did an image backup of my system disk before running the upgrade, so if I rolled the old system back onto my hard drive it would be available for debugging this problem if anyone is interested in giving that a shot.

---

