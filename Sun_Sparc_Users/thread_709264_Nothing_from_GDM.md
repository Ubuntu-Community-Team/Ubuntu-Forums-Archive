---
title: "Nothing from GDM?"
date: 2008-02-27
forum: Sun Sparc Users
---

### Post by adamretter on 2008-02-27
I have a Sun Ultra 10 with a Creator 3D card.

I upgrade the OBP to 3.3.1 and then installed Ubuntu 7.10 Server for SPARC. The only non-standard thing I had to do was at the SILO boot prompt type this - 

boot> install append = "video=atyfb:off"

This was to get the install program to correctly output on the Creator 3D, after the install I added that parameter to silo.conf and everything works lovely :-) Very impressed so far.

I then decided that I wanted a desktop, so I ran "sudo aptitude install xubuntu-desktop", all installed perfectly. I had to change /etc/X11/xorg.conf to use Driver "sunffb" for X to use the Creator 3D instead of the built in ATI graphics.

I then ran "startx" and there was my xubuntu desktop, Brilliant!

Except... GDM is meant to start at system start up time (its installed as part of xubuntu-desktop), and provide a graphical login to X.

When I start up I see a brief flash (I assume GDM/X is trying to do something), then I am returned to tty8 - which shows -
* Starting GNOME Display Manager...     [OK]

If I switch to tty7 (Ctrl-Alt-F7) I see just a flashing white "-" character on a black background, looks like a console to me.

If I switch to tty1 (Ctrl-Alt-F1), login and run "ps -ax" I can see this -
4162 ?        Ss     0:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf

The GDM log file /var/log/gdm/:0.log shows the following which looks ok -

Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux inca 2.6.22-14-sparc64 #1 Tue Feb 12 03:18:52 UTC 2008 sparc64
Build Date: 18 January 2008
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb 27 14:18:38 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module already built-in
Detected FFB2+/vertical, Z-buffer, Double-buffered.
(EE) AIGLX: Screen 0 is not DRI capable
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.


Anyone have any ideas whats wrong here?

Thanks Adam.

---

### Post by capt_caveman on 2008-03-27
See [http://www.csn.ul.ie/~ivan/install_ubuntu_on_ultra10.html#gdm%20woes](http://www.csn.ul.ie/~ivan/install_ubuntu_on_ultra10.html#gdm%20woes) - try adding +xinerama to the /usr/bin/X -br -audit 0 line in /etc/gdm/gdm*.conf

---

