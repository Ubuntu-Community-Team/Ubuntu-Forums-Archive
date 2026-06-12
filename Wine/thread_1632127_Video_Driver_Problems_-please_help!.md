---
title: "Video Driver Problems -please help!"
date: 2010-11-27
forum: Wine
---

### Post by jowancklee on 2010-11-27
I have been trying to run Team Fortress 2 on steam.  However, I have been having issues with it not displaying the intro screen properly (no text, just rectangles of color.)
The WINE appdb indicates that I need to change my video driver.  However, when I go System-Administration-Additional Drivers, it doesn't show any additional drivers.
I saw this this thread: [http://ubuntuforums.org/showthread.php?t=646064](http://ubuntuforums.org/showthread.php?t=646064) I tried to edit my xorg.conf file, but it doesn't exist.  I ran 'X -configure' and it created an xorg.conf.new file.  I tried to do what the thread said to, but when I ran 'sudo X -config /home/family/xorg.conf.new', I got this output:

"X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux FamilyDesktop 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=70862de6-ad6b-4d2f-9709-318b7622ce8f ro quiet splash
Build Date: 16 September 2010  05:39:22PM
xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.18.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov 27 15:16:24 2010
(++) Using config file: "/home/family/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) Failed to load module "i810" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log"

I am running Ubuntu 10.10 
Intel Pentium 4 2.8 ghz proc
2 gigabytes RAM
When I run 'lspci | grep VGA' I get '00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)'

Now for the question: How do I change my video driver?
Thank you!

---

### Post by jowancklee on 2010-11-27
Here's a picture of what the virtual desktop looks like after tf2 loads:
[http://tinypic.com/r/mblpbd/7](http://tinypic.com/r/mblpbd/7)

---

### Post by Soulcage on 2010-11-28
Additional drivers is meant for people running a nvidia or ati card.
(nvidia runs better)

---

### Post by jowancklee on 2010-11-28
Ok.  Then how do I go about changing/adding a video driver?

---

### Post by Soulcage on 2010-11-29
All I can say is go buy an nvidia video card install it then install your drivers via additional drivers.

---

### Post by cogadh on 2010-11-29
Yeah, I'm pretty sure that graphics "card" is not even capable of running TF2 in Windows, let alone on Linux through Wine. You need to replace that POS integrated chipset with a dedicated graphics card, preferably an Nvidia model (they have more robust Linux support than ATI currently does).

---

