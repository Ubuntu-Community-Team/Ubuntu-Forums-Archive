---
title: "X - Server"
date: 2006-11-21
forum: Server Platforms
---

### Post by jimmymac on 2006-11-21
Hi guys,

I've installed Dapper Server and am in the process of configuring NFS etc.

No problems with that (so far!)

What I would like to do is install X so that it can be launched.  But it is not the default start up.
Also I would like users remotely accessing via SSH to be able to launch graphical applications.
I think that makes sense....

Cheers,

Jimmy

---

### Post by fazavon on 2006-11-21
Do you have an X windows installed now?

if so all you have to do is edit the inittab 

6.06
vi /etc/inittab

edit the line that says

id:2:initdefault

to 

id:1:initdefault

if in 6.10 

gedit /etc/inittab

id:2:initdefault

to 

id:1:initdefault

be sure you run sudo first or it will not work

//j

---

### Post by jimmymac on 2006-11-21
Haven't installed X yet.  Have got a bit of time to tinker tomorrow so I'll have a go then and let you know how it turns out!

Cheers,

Jimmy

---

### Post by tturrisi on 2006-11-21
apt-get install xorg gnome-core (will give you the basic Gnome graphical environment)
use startx to get to graphical desktop

DON'T do apt-get install gnome  (way too much garbage included)
DON'T do apt-get install gnome-desktop (bloated unnecessary stuff)
DON't do apt-get install gdm  (forces graphical login)

---

### Post by jimmymac on 2006-11-22
Ok,

Apparently there isn't a package just called xorg and gnome-core doesn't exist.

Do I need to enable the universe & multiverse repos?  Was trying to avoid it but can do if need be!!

And this will still start up without x loaded?

Cheers,

Jimmy

---

### Post by tturrisi on 2006-11-22
enable the Univers repositories
apt-get install gnome-core xserver-xorg
Will not boot to graphical, use the command startx to get to graphical desktop.  X will not load at startup until use command startx.  Xorg should auto detect your hardware during the install.  If run startx & have monitor, display or mouse issues then run
dpkg-reconfigure xserver-xorg
and follow the onscreen questions & prompts.

---

### Post by jimmymac on 2006-11-22
Excellent will do that later.

Quick unrelated question, how do I stop it asking for the cd when I install new packages?

Cheers,

Jimmy

---

### Post by jimmymac on 2006-11-22
Anyway I sorted that just by thinking!  Amazing thing that wossname...brain!

Just installing the xserver & gnome-core.  Thanks for all the help!

Cheers,

Jimmy

---

### Post by jimmymac on 2006-11-22
So how to change permissions so that a normal user can startx?

And can you startx remotely through ssh?

TIA,

Jimmy

---

### Post by tturrisi on 2006-11-22
Create the user account.  Logout as root.  Login as new user:  startx.
x over ssh:
[http://www.google.com/search?hl=en&lr=&q=X+over+ssh&btnG=Search](http://www.google.com/search?hl=en&lr=&q=X+over+ssh&btnG=Search)

---

### Post by jimmymac on 2006-11-22
Ok I followed the tutorial at:

[http://www.cag.lcs.mit.edu/~wentzlaf/faq/ssh_X.html](http://www.cag.lcs.mit.edu/~wentzlaf/faq/ssh_X.html)

and my x over ssh still doesn't work.

Any ideas?

MTIA

Jimmy

---

### Post by jimmymac on 2006-11-22
So...

After setting up configuring X, I try to start it as sudo and get the following:

user@venus:~$ sudo startx
Password:
xauth:  creating new authority file /home/user/.serverauth.4722

X: warning; process set to priority -1 instead of requested priority 0

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux venus 2.6.15-26-server #1 SMP Thu Aug 3 04:09:15 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov 23 00:03:59 2006
(==) Using config file: "/etc/X11/xorg.conf"
(**) RADEON(0): RADEONPreInit
(**) RADEON(0): RADEONScreenInit e0000000 0
(**) RADEON(0): Map: 0xe0000000, 0x10000000
(**) RADEON(0): RADEONSave
(**) RADEON(0): RADEONSaveMode(0x81ff2d0)
(**) RADEON(0): Read: 0x0000000c 0x00030065 0x00000000
(**) RADEON(0): Read: rd=12, fd=101, pd=3
(**) RADEON(0): RADEONSaveMode returns 0x81ff2d0
(**) RADEON(0): DRI New memory map param
(**) RADEON(0): RADEONInitMemoryMap() :
(**) RADEON(0):   mem_size         : 0x10000000
(**) RADEON(0):   agp_size         : 0x081ff1a8
(**) RADEON(0):   agp_base         : 0x081ff1a8
(**) RADEON(0):   MC_FB_LOCATION   : 0xefffe000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0): RADEONModeInit()
1280x1024     108.00  1280 1328 1440 1688  1024 1025 1028 1066 (24,32) +H +V
1280x1024     108.00  1280 1328 1440 1688  1024 1025 1028 1066 (24,32) +H +V
(**) RADEON(0): Pitch = 10485920 bytes (virtualX = 1280, displayWidth = 1280)
(**) RADEON(0): dc=10800, of=21600, fd=96, pd=2
(**) RADEON(0): RADEONInit returns 0x81ffc80
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81ffc80)
(**) RADEON(0): RADEONRestoreMemMapRegisters() :
(**) RADEON(0):   MC_FB_LOCATION   : 0xefffe000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x0000000c 0x00010060 0x00000000 (0x0000a700)
(**) RADEON(0): Wrote: rd=12, fd=96, pd=1
(**) RADEON(0): GRPH_BUFFER_CNTL from 20205c5c to 200f5c5c
(**) RADEON(0): RADEONSaveScreen(0)
(**) RADEON(0): Setting up initial surfaces
(**) RADEON(0): Initializing fb layer
(**) RADEON(0): Setting up accel memmap
(**) RADEON(0): Initializing backing store
(**) RADEON(0): DRI Finishing init !
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): GRPH_BUFFER_CNTL from 20205c5c to 200f5c5c
(**) RADEON(0): Setting up final surfaces
(**) RADEON(0): Initializing Acceleration
(**) RADEON(0): EngineInit (32/32)
(**) RADEON(0): Pitch for acceleration = 160
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): Initializing DPMS
(**) RADEON(0): Initializing Cursor
(**) RADEON(0): Initializing color map
(**) RADEON(0): Initializing DGA
(**) RADEON(0): Initializing Xv
(**) RADEON(0): RADEONScreenInit finished
error opening security policy file /etc/X11/xserver/SecurityPolicy
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Error:            No Symbols named "nodeadkeys" in the include file "gb"
>                   Exiting
>                   Abandoning symbols file "default"
Errors from xkbcomp are not fatal to the X server
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
Could not init font path element /usr/share/X11/fonts/misc/, removing from list!Could not init font path element /usr/share/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/share/X11/fonts/OTF, removing from list!
Could not init font path element /usr/share/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/share/X11/fonts/CID/, removing from list!
Could not init font path element /usr/share/X11/fonts/100dpi/, removing from list!
Could not init font path element /usr/share/X11/fonts/75dpi/, removing from list!

Fatal server error:
could not open default font 'fixed'
(**) RADEON(0): RADEONLeaveVT
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): RADEONRestore
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81ff2d0)
(**) RADEON(0): RADEONRestoreMemMapRegisters() :
(**) RADEON(0):   MC_FB_LOCATION   : 0x1fff0000
(**) RADEON(0):   MC_AGP_LOCATION  : 0x27ff2000
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x0000000c 0x00030065 0x00000000 (0x0000a700)
(**) RADEON(0): Wrote: rd=12, fd=101, pd=3
(**) RADEON(0): Ok, leaving now...
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.


Any ideas?

Much obliged,

Jimmy

---

### Post by tturrisi on 2006-11-22
were you root when you installed x?
You should not need sudo to startx.

---

