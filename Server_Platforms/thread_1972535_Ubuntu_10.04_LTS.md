---
title: "Ubuntu 10.04 LTS"
date: 2012-05-03
forum: Server Platforms
---

### Post by metallica1973 on 2012-05-03
I setup an Ubuntu 10.04 server which has several developers on the box. I have been ask to add a gui to the server. Only one developer want the gui to start when she logs in(runlevel 2 with a GUI). I am used to seeing an /etc/inittab file which I cannot seem to find under this Ubuntu version. So once I get the GUI (lightdm/GNOME and etc.) installed, how do I set up just this user to have the GUI  to load only for this one user and not the rest?

---

### Post by metallica1973 on 2012-05-11
I figured it out. This should help

[php]
http://ubuntuforums.org/showthread.php?t=1485839
[/php]

---

### Post by metallica1973 on 2012-05-13
thanks for the replies. One more stupid question:

I used this how to:

[http://ubuntuforums.org/showthread.php?t=1479980](http://ubuntuforums.org/showthread.php?t=1479980)

and successfully installed ubuntu-desktop. The part I have trouble understanding is when the user ssh into the ubuntu 10.04 server and at the prompt she does a startx, I can see that it successfully running:

[php]
sudo startx
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
Current Operating System: Linux Daman 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=348b4aba-1a35-4866-8e2b-95e8065ed43c ro quiet splash
Build Date: 20 October 2011  03:05:54PM
xorg-server 2:1.7.6-2ubuntu7.10 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun May 13 16:48:07 2012
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(II) [KMS] drm report modesetting isn't supported.
  XRANDR name: VGA-0
  Connector: VGA
  CRT1: INTERNAL_DAC1
  DDC reg: 0x60
  XRANDR name: DVI-0
  Connector: DVI-D
  DFP2: INTERNAL_DVO1
  DDC reg: 0x64
finished output detect: 0
finished output detect: 1
finished all detect
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable primary dac
disable primary dac
disable FP2
disable primary dac
init memmap
init common
init crtc1
init pll1
freq: 108000000
best_freq: 108000000
best_feedback_div: 16
best_frac_feedback_div: 0
best_ref_div: 2
best_post_div: 2
restore memmap
restore common
restore crtc1
restore pll1
finished PLL1
set RMX
set primary dac
enable primary dac
disable FP2
[/php]

but there isnt a gui. Do I have to setup vnc-server in order for her to view the desktop? Remember that she connects via ssh. Thanks

---

### Post by CharlesA on 2012-05-13
You would need to forward X over SSH in order to run graphical applications via SSH.

```
ssh -X user@host
```

---

