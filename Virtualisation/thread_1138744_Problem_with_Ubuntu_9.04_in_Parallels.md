---
title: "Problem with Ubuntu 9.04 in Parallels"
date: 2009-04-26
forum: Virtualisation
---

### Post by b4pjoe on 2009-04-26
I've installed Ubuntu 9.04 in Parallels 3.0 build 5636 on my Mac:

Mac OS 10.5.6

2.16 GHz Intel Core 2 Duo

ATI Radeon X1600 display adapter.

The install goes without a hitch and after restarting after the install it comes to the login window. All looks fine and when I log in I see the desktop background, the menu's and hear the opening sound play. Then it kicks me back to the log in screen. I don't see any error messages. It just sends me back to the log in screen. Log in again and it does the same thing. Over and over and over again.

I tried installing it in VirtualBox as well and I can log in on it but I'm limited to 640x480 or 800x600 resolution so that is not much better.

Thanks in advance.

---

### Post by MacSkyrate on 2009-04-27
Same here.. hope someone has a good idea what this is..

Thanks for all future contributes :)

Regards

---

### Post by b4pjoe on 2009-04-27
If it helps I was able to get my screen resolutions back in VirtualBox by installing the Guest Additions.

I'm thinking installing Parallels Tools might be the fix for the Parallels problem except you can't install them until you log in but you can't log in to install them. Quite a dilemma...

:P

---

### Post by MacSkyrate on 2009-04-27
LOL nice reply... 

Sooo.. i've gone thru Parallels site and they do not have a single post on this matter.. Strange if you ask me..

---

### Post by b4pjoe on 2009-04-27
I'm thinking it is probably a Parallels problem as Ubuntu works fine on VirtualBox on the Mac. I don't have the latest Parallels which is version 4. And I probably can't count on Parallels fixing version 3 that I do have. What version of Parallels are you using?

---

### Post by b4pjoe on 2009-04-27
I managed to get a failsafe terminal window that I can log into and stay logged in so I tried installing Parallels Tools. It starts to install but then quits with a "Installation for xorg.1.6 not found". Any ideas? Anyone?

---

### Post by b4pjoe on 2009-04-28
> **MacSkyrate said:**
> LOL nice reply... 

Sooo.. i've gone thru Parallels site and they do not have a single post on this matter.. Strange if you ask me..

There are posts there now about it. It appears that Ubuntu 9.04 will not work with Parallels Desktop 3 or 4.

[http://forum.parallels.com/showthread.php?t=89645](http://forum.parallels.com/showthread.php?t=89645)

---

### Post by MacSkyrate on 2009-04-28
> **b4pjoe said:**
> There are posts there now about it. It appears that Ubuntu 9.04 will not work with Parallels Desktop 3 or 4.

[http://forum.parallels.com/showthread.php?t=89645](http://forum.parallels.com/showthread.php?t=89645)

I know because its my post ;)

---

### Post by alpha0 on 2009-05-12
I am also having the same problem. The login window keeps looping.

I am trying to install Ubuntu 9.04 on the following:
OS: Mac OS X 10.4.11
Parallels: 3.0

---

### Post by engineson on 2009-06-12
I had the same issues while trying to install in Parallels 3... I was able to run successfully in VMware Fusion however, Fusion and Parallels cannot run together... Hope this helps

---

### Post by threeraindrops on 2009-07-09
Just in case *Parallels Desktop* developers attend this thread:
I too face the same problem as described in this thread. 

Looking forward to some prompt and happy resolution

---

### Post by marcvk on 2009-07-21
Hi,

Same happened to me:

(Mac OS X 10.5.7, Parallels Desktop 3.0 for Mac build 5638, running Ubuntu Desktop 9.04)

When running startx from the console instead of logging in via gdm, the following error message below is shown, note that the xserver is still starting up after the first error message, so it doesn't seem to affect it, the sig11 in libpixman-1.so.0 of course does!

Any ideas what might be causing this?

# startx

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux anna-ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul 21 15:50:12 2009
(==) Using config file: "/etc/X11/xorg.conf"

error setting MTRR (base = 0xc0000000, size = 0x01000000, type = 1) Function not implemented (38)

Backtrace:
0: /usr/bin/X11/X(xorg_backtrace+0x3b) [0x813518b]
1: /usr/bin/X11/X(xf86SigHandler+0x55) [0x80c7be5]
2: [0xb7f5f400]
3: /usr/lib/libpixman-1.so.0 [0xb7ebf724]
4: /usr/lib/libpixman-1.so.0 [0xb7ec4350]
5: /usr/lib/libpixman-1.so.0(pixman_image_composite+0x761) [0xb7ec3f71]
6: /usr/lib/xorg/modules//libfb.so(fbComposite+0x1b2) [0xb76eb632]
7: /usr/bin/X11/X [0x818030a]
8: /usr/bin/X11/X(CompositePicture+0x19a) [0x817255a]
9: /usr/bin/X11/X [0x8178405]
10: /usr/bin/X11/X [0x8175125]
11: /usr/bin/X11/X(Dispatch+0x33f) [0x808d57f]
12: /usr/bin/X11/X(main+0x3bd) [0x80722ed]
13: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7b34775]
14: /usr/bin/X11/X [0x80717a1]
Saw signal 11.  Server aborting.
 ddxSigGiveUp: Closing log
 ddxSigGiveUp: re-raising 11
xinit:  connection to X server lost.

---

### Post by marantis on 2009-07-21
same problem here. does already exist any solution?!

---

### Post by fguillen on 2009-08-13
Same problem here. :/

Parallels Desktop 3.0 for Mac
Build 5600 (8 may 2008)

---

### Post by fguillen on 2009-08-13
Working on 

Parallels Desktop 4.0
Build 4.0.3844

Maybe was only the memory configuration, I turned it to: 512MB

f.

---

