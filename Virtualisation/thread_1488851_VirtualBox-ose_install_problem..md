---
title: "VirtualBox-ose install problem."
date: 2010-05-20
forum: Virtualisation
---

### Post by Barry53 on 2010-05-20
Hi All,

I have Lucid 64bit server installed. I have installed VirtualBox-ose. I can create a virtual machine using VBoxManage and all seems to go well until i try to start the vm.
 
```
VBoxManage startvm Lucid-server-32
[Sun VirtualBox Command Line Management Interface Version 3.1.6_OSE
(C) 2005-2010 Sun Microsystems, Inc.
All rights reserved.


Waiting for the remote session to open...
ERROR: Virtual machine 'Lucid-server-32' has terminated unexpectedly during startup

Details: code NS_ERROR_FAILURE (0x80004005), component Machine, interface IMachine, callee <NULL>


```
If I try VirtualBox to launch the gui I get:
```
VirtualBox
Failed to open the X11 display!
```
If I try to start x windows I get this:
```
startx

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0

Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu

Current Operating System: Linux hagrid 2.6.32-22-server #33-Ubuntu SMP Wed Apr 28 14:34:48 UTC 2010 x86_64

Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-server root=UUID=d19de7ff-474d-49a9-8f0e-8cd88c27ae1d ro

Build Date: 23 April 2010  05:11:46PM

xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 

Current version of pixman: 0.16.4

	Before reporting problems, check http://wiki.x.org

	to make sure that you have the latest version.

Markers: (--) probed, (**) from config file, (==) default setting,

	(++) from command line, (!!) notice, (II) informational,

	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.

(==) Log file: "/var/log/Xorg.0.log", Time: Thu May 20 12:52:30 2010

(==) Using config directory: "/usr/lib/X11/xorg.conf.d"

(EE) Failed to load module "ati" (module does not exist, 0)

(EE) Failed to load module "vesa" (module does not exist, 0)

(EE) Failed to load module "fbdev" (module does not exist, 0)

(EE) No drivers available.


Fatal server error:
no screens found


Please consult the The X.Org Foundation support
 
	 at http://wiki.x.org
 for help. 

Please also check the log file at "/var/log/Xorg.0.log" for additional information.


 ddxSigGiveUp: Closing log
giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.


```
The packages I have loaded are:
```
ii  virtualbox-guest-additions      3.1.6-1                           guest additions iso image for VirtualBox

ii  virtualbox-ose                  3.1.6-dfsg-2ubuntu2               x86 virtualization solution - base binaries

ii  virtualbox-ose-dkms             3.1.6-dfsg-2ubuntu2               x86 virtualization solution - kernel module 

ii  virtualbox-ose-guest-dkms       3.1.6-dfsg-2ubuntu2               x86 virtualization solution - guest addition

ii  virtualbox-ose-guest-utils      3.1.6-dfsg-2ubuntu2               x86 virtualization solution - non-X11 guest 

ii  virtualbox-ose-guest-x11        3.1.6-dfsg-2ubuntu2               x86 virtualization solution - X11 guest util

ii  virtualbox-ose-qt               3.1.6-dfsg-2ubuntu2               x86 virtualization solution - Qt based user 

ii  libx11-6                        2:1.3.2-1ubuntu3                  X11 client-side library

ii  libx11-data                     2:1.3.2-1ubuntu3                  X11 client-side library

ii  x11-common                      1:7.5+5ubuntu1                    X Window System (X.Org) infrastructure

ii  x11-utils                       7.5+3                             X11 utilities

ii  x11-xkb-utils                   7.5+1                             X11 XKB utilities

ii  xserver-xorg                    1:7.5+5ubuntu1                    the X.Org X server

ii  xserver-xorg-core               2:1.7.6-2ubuntu7                  Xorg X server - core server

ii  xserver-xorg-input-evdev        1:2.3.2-5ubuntu1                  X.Org X server -- evdev input driver

```

I suspect VirtualBox is running OK and my problem lies in x windows. I don't have a gui such as gnome or kde running as this is a server. I don't think i need one, VirtualBox is suppose th be the window manager, I think

Can anyone see where I have gone astray?

Thanks in advance,
Barry

---

### Post by Barry53 on 2010-05-20
I found the answer, I needed the drivers for my video card.:)

```
sudo apt-get install xserver-xorg-video-ati
```

did the trick!

Hope this helps someone else.

---

### Post by yabloko on 2010-10-12
I was coming up against the same message but my error was that I was trying to launch VirtualBox before I had X11 running.

So from headless Ubuntu server I entered:

```
startx
```

which loads xfce, where I then opened terminal and entered:

```
VirtualBox
```

That worked for me.

---

