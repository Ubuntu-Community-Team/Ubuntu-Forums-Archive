---
title: "Starting GUI Desktop in Serial Console"
date: 2011-02-23
forum: Server Platforms
---

### Post by swilson2000 on 2011-02-23
I have installed KDE and all the software for it to run on my server through the serial console but when I go and run "startx" I get the following and KDE doesn't start running. Any help would be appreciated. Thanks.


root@u15434060:~# startx


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
Current Operating System: Linux u15434060 2.6.32-28-server #55-Ubuntu SMP Mon Jan 10 23:57:16 UTC 2011 x86_64
Kernel command line: root=/dev/md1 ro console=tty0 console=ttyS0,57600
Build Date: 10 December 2010  05:52:57PM
xorg-server 2:1.7.6-2ubuntu7.5 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
Current version of pixman: 0.16.4
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb 23 10:32:55 2011
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28 [0x45fcc8]
1: /usr/bin/X (0x400000+0x5dfbd) [0x45dfbd]
2: /lib/libpthread.so.0 (0x7f9f2c202000+0xf8f0) [0x7f9f2c2118f0]
3: /usr/bin/X (xf86InitViewport+0x4b) [0x51242b]
4: /usr/bin/X (InitOutput+0xb2d) [0x46e36d]
5: /usr/bin/X (0x400000+0x26005) [0x426005]
6: /lib/libc.so.6 (__libc_start_main+0xfd) [0x7f9f2aef9c4d]
7: /usr/bin/X (0x400000+0x25d59) [0x425d59]
Segmentation fault at address 0x24

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

---

### Post by arrrghhh on 2011-02-23
Why would you want to run X on a server at all?

I'm not sure you can pipe X over a serial connection, but I'm not really sure how that works honestly.  I'm used to working on Cisco gear, which obviously doesn't involve X :p.

---

