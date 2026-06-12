---
title: "Bug report( Xorg crashed with SIGABRT in xdl_xs115_) fix mail received"
date: 2014-03-05
forum: Ubuntu Development Version
---

### Post by su:bhatta on 2014-03-05
I had reported the bug regarding Video playback, on video playback my session was getting logged off and yesterday I recieved this mail :
```

[IMG]https://ssl.gstatic.com/ui/v1/icons/mail/profile_mask2.png[/IMG]


Maarten Lankhorst <snip>
8:44 PM (14 hours ago)[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]

[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]
[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]

to me 
[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]

[B]** Package changed: xorg-server (Ubuntu) => fglrx-installer (Ubuntu)
[/B]
--
You received this bug notification because you are subscribed to the bug
report.
[https://bugs.launchpad.net/bugs/1285627](https://bugs.launchpad.net/bugs/1285627)

Title:
  Xorg crashed with SIGABRT in xdl_xs115_atiddxPixmapIsTypeOf()

Status in &#8220;fglrx-installer&#8221; package in Ubuntu:
  New

Bug description:
  Opening a 3GP video in parole Player made the system logoff and this
  bug was generated.

  As of now can only use VLC player to play any videos that too after the following change:
  Turning OFF Acceralated Graphics in the Video Tab of Preferences in VLC Player.

  Thank you.
  Bhatta

  ProblemType: Crash
  DistroRelease: Ubuntu 14.04
  Package: xserver-xorg-core 2:1.15.0-1ubuntu6
  ProcVersionSignature: Ubuntu 3.13.0-8.28-lowlatency 3.13.2
  Uname: Linux 3.13.0-8-lowlatency x86_64
  NonfreeKernelModules: fglrx
  ApportVersion: 2.13.2-0ubuntu5
  Architecture: amd64
  CrashCounter: 1
  Date: Thu Feb 27 16:51:41 2014
  ExecutablePath: /usr/bin/Xorg
  InstallationDate: Installed on 2014-02-13 (13 days ago)
  InstallationMedia: Ubuntu-Studio 14.04 "Trusty Tahr" - Alpha amd64 (20140211)
  ProcCmdline: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
  ProcEnviron:


```

Now, does this mean that if i reinstall fglrx will that solve the problem ? 
Really sorry, this is the first time I have got such a mail and I dont understand the right course of action.

---

### Post by Doug S on 2014-03-05
> **bhattabhishek said:**
> ...Now, does this mean that if i reinstall fglrx will that solve the problem ? 
Really sorry, this is the first time I have got such a mail and I dont understand the right course of action.No. Someone has just identified and set the relevant package for the bug report.

---

### Post by su:bhatta on 2014-03-05
Doug, Thanks a ton. 

In that case this I am marking this thread as Solved as there is not much to do.

---

### Post by Doug S on 2014-03-05
I would suggest to keep your system up to date and check for your bug report issue often (say every few days). Sometimes issues get solved without realization of some other related bug report or whatever.

---

### Post by su:bhatta on 2014-03-05
Will surely keep that in mind. 
I am updating the system everyday !

Thanks for the help.

---

### Post by su:bhatta on 2014-03-20
This has been fixed and now there are no issues. 
Yesterdays fglrx-updates did the trick.

---

### Post by rocapp on 2014-10-19
I just got a similar crash from package xserver-xorg-core 2:1.15.1-0ubuntu2.1

---

### Post by cariboo on 2014-10-19
The above problem is 10.04 related, and as such should be discussed in the regular part of the Forum. Thread closed.

---

