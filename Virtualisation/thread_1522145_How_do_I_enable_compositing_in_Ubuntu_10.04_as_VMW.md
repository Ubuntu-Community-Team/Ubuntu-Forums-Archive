---
title: "How do I enable compositing in Ubuntu 10.04 as VMWare Workstation guest?"
date: 2010-07-01
forum: Virtualisation
---

### Post by winchendonsprings on 2010-07-01
After doing searching the forum here as well as google I didn't find too much help on this subject. I first posted on the VMWare forum, but I figured someone here might know something helpful. 

 I have Ubuntu 10.04 i386 Installed in Workstation 7.1.0 build-26102 and I  have Accelerate 3d graphics checked off in my VM settings for this  machine.


  Compiz, Docky, Gnome-Do, AWN  all ask for enabling compositing. 


 Any idea what i can do? 


 [COLOR=#000000]Here is what compiz-check says - [/COLOR]
[COLOR=Indigo]
[/COLOR] 
 
 
 [COLOR=Indigo][COLOR=#800080]ry@ubuntu:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         VMware SVGA II Adapter
 Driver in use:         vmware
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [SKIP]("http://communities.vmware.com/community-document-picker.jspa?communityID=&subject=SKIP")
 Checking for non power of two support...          [SKIP]("http://communities.vmware.com/community-document-picker.jspa?communityID=&subject=SKIP")
 Checking for composite extension...               [  OK ]("http://communities.vmware.com/community-document-picker.jspa?communityID=&subject=+OK+")
 Checking for FBConfig...                          [SKIP]("http://communities.vmware.com/community-document-picker.jspa?communityID=&subject=SKIP")
 Checking for hardware/setup problems...           [WARN]("http://communities.vmware.com/community-document-picker.jspa?communityID=&subject=WARN")

Something potential problematic has been detected with your setup:
 Warning: Detected driver is not on the whitelist. 

Would you like to know more? (Y/n) y

 Your driver is not widely known to work with Compiz and thus may be
 blacklisted on certain distributions.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N) [/COLOR][/COLOR]

---

### Post by bodhi.zazen on 2010-07-01
Guests do not directly use your hardware and trying to directly use the hardware is likely to be problematic.

First, last time I looked, VMWare did not support Ubuntu very well, so if they claim to support 3d graphics you will need to use a supported OS, use the VMWare forums, or code it yourself. You may get lucky and find a fix with google or perhaps someone will answer here.

Personally, I use the composting built into XFCE or gnome rather then compiz. It works well, but is not the same as compiz.

Hopefully that will work for you as well, or if not I hope you find a better answer.

I am moving this to a more appropriate location, where hopefully you may find a better answer.

---

### Post by winchendonsprings on 2010-07-01
Thanks.

Here is what someone who works at VMWare said - 

Unfortunately 3d acceleration is currently only supported for Windows  (XP, Vista, 7) guests.  OpenGL support for Linux guests is something  we'd really like to add to the product but we don't know when it will  happen. 														

[http://communities.vmware.com/message/1563609#1563609](http://communities.vmware.com/message/1563609#1563609)

---

### Post by cgroza on 2010-07-01
Virtual Box supports it. I don't know if this is the right solution for you.

---

### Post by winchendonsprings on 2010-07-01
about 2 years ago i wish i had started using virtualbox rather than vmware. now i have a few virtual machines that i need and i'd rather not try to convert them to virtualbox. damn

you think virtualbox ose ever have usb support?

---

### Post by Gilgad Drumheller on 2010-07-12
Composting isn't the same as Compiz.  VMWare currently doesn't seem to support the level of hardware interaction required for Compiz, but there are composting solutions that work.

[http://ubuntu-tutorials.com/2009/02/24/enable-basic-compositing-for-gnome-do-08x/](http://ubuntu-tutorials.com/2009/02/24/enable-basic-compositing-for-gnome-do-08x/)

tl:dr install xcompmgr and configure to start when ubuntu starts

---

