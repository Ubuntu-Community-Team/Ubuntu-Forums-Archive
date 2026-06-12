---
title: "Install Windows 2002 on Ubuntu 10.10"
date: 2010-12-05
forum: System76 Support
---

### Post by oldslow on 2010-12-05
Hello,

I am attempting to install Windows 2002 on Ubuntu 10.10 using Wine 1.2.1.

After opening the SETUP.EXE file using Wine, entering the Product Key, and clicking "Next" to load the software; the windows page disappears and quits loading the software. No errors appear during this process.

Any ideas?

Thanks

---

### Post by HotShotDJ on 2010-12-05
> **oldslow said:**
> Hello,

I am attempting to install Windows 2002 on Ubuntu 10.10 using Wine 1.2.1.

After opening the SETUP.EXE file using Wine, entering the Product Key, and clicking "Next" to load the software; the windows page disappears and quits loading the software. No errors appear during this process.

Any ideas?

Thanks
One doesn't install Windows in Wine.  Wine provides a Windows compatibility layer to Linux that works well for some applications, not so much for others.  It is NOT a virtualization software package.
If you would like to install a full version of Windows within Ubuntu, I usually recommend VirtualBox, but there are others (see the Virtualization forum here at ubuntuforums).

---

### Post by oldslow on 2010-12-05
> **HotShotDJ said:**
> One doesn't install Windows in Wine.  Wine provides a Windows compatibility layer to Linux that works well for some applications, not so much for others.  It is NOT a virtualization software package.
If you would like to install a full version of Windows within Ubuntu, I usually recommend VirtualBox, but there are others (see the Virtualization forum here at ubuntuforums).

HotShotDJ,
 
Thanks for the information of clarity. 

Question, can Windows 2002 Excel, Word, and Access be within Ubuntu without the full version? If yes, what do you recommend?

Thanks

---

### Post by HotShotDJ on 2010-12-06
> **oldslow said:**
> HotShotDJ,
 
Thanks for the information of clarity. 

Question, can Windows 2002 Excel, Word, and Access be within Ubuntu without the full version? If yes, what do you recommend?

ThanksYou may be able to run Excel, Word and/or Access directly under Wine. Check out the [WineHQ Application Database]("http://appdb.winehq.org/") for more information. (I've never done it myself, so I can't really give you first hand experience.  I do know that people have done it.)

For help with Wine, I recommend the Ubuntuforums [Wine]("http://ubuntuforums.org/forumdisplay.php?f=313") forum.  If you'd like to try virtualization, check out the Ubuntuforums [Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308") forum.  Its not that we don't want to help you in this forum, but there are people in those other two that have more expertise in this matter.  Best of luck!!!

PS:  Is there any reason why you need those three applications?  OpenOffice is a robust suite of productivity applications that I use almost exclusively.

---

### Post by oldslow on 2010-12-06
> **HotShotDJ said:**
> You may be able to run Excel, Word and/or Access directly under Wine. Check out the [WineHQ Application Database]("http://appdb.winehq.org/") for more information. (I've never done it myself, so I can't really give you first hand experience.  I do know that people have done it.)

For help with Wine, I recommend the Ubuntuforums [Wine]("http://ubuntuforums.org/forumdisplay.php?f=313") forum.  If you'd like to try virtualization, check out the Ubuntuforums [Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308") forum.  Its not that we don't want to help you in this forum, but there are people in those other two that have more expertise in this matter.  Best of luck!!!

PS:  Is there any reason why you need those three applications?  OpenOffice is a robust suite of productivity applications that I use almost exclusively.

HotShotDJ,

Thanks again for the information. I will look into the forums you have mentioned.

To answer your question about those three applications. I like OpenOffice applications, but I wanted to stay with Windows applications for job-related reasons. However, I will further look into the OpenOffice applications because they may be of equal interest. 

Thank you for your help,

Oldslow

---

