---
title: "Itunes appcrash"
date: 2010-02-15
forum: Virtualisation
---

### Post by Captjac91 on 2010-02-15
Hey guys i have a little problem that i can't seem to figure out. 

Ok first off i'm running ubuntu 9.10 and Vista on Virtual box. 

My main reason for using virtual box was to run Itunes however after I installed it and tried to run it, i get a message saying that itunes has stopped working, when i click problem details i get this:

Problem Signature:
 Problem Event Name:  APPCRASH
 Application Name: Itunes.exe
 Application Version: 9.0.3.15
 Application Timestamp: 4b590a69
 Fault Module Name: StackHash_fd00
 Fault Module Version: 0.0.0.0
 Fault Module Timestamp: 00000000
 Exception Code: c0000005
 Exception Offset: 000000dd
 OS Version: 6.0.6001.2.1.0.256.6
 Locale ID: 1033
 Additional Information 1: fd00
 Additional Information 2: ea6f5fe8924aaa756324d57f87834160
 Additional Information 3: fd00
 Additional Information 4: ea6f5fe8924aaa756324d57f87834160

I have no idea what any of this means... lol, if someone could help me to figure out how to fix this or how to run itunes on virtual box I would greatly appreciate the help :)

---

### Post by amchornet on 2010-03-20
I have the exact same problem and could also use help also have the same ubuntu and windows 7 in v box....

---

### Post by PuckPuck on 2010-03-21
Known issue.  This has to do with iTunes 9.0.3 and VirtualBox running on Ubuntu.  Whether this is a VirtualBox or iTunes issues I'm not sure.

There is a very easy fix.

1) Uninstall iTunes 9.0.3.  Doing this will not preserve your music library settings.
2) Download iTunes 9.0.2 from [www.oldapps.com/itunes.php](www.oldapps.com/itunes.php)
3) Install iTunes 9.0.2.  If you uninstalled 9.0.3 through the control panel, your library settings will be preserved.

4) Do not update your iTunes until someone else on here has validated that the newer version works, and/or a newer VirtualBox version works.


I have been running this and it works great.  Home sharing, iPod connectivity, etc.  The only issue I think I found is when you are downloading multiple new songs at once.  Seems like if you download 3 or more at the same time, it locks up.  Maybe its just my environment.  I now make sure I don't download more than 2 items at once, and leave everything else queued up.

---

### Post by amchornet on 2010-03-21
THANKYOU SO MUCH I did not think of it. The older version of I tunes worked and again I thank you:KS:popcorn::P:P:P

---

### Post by bdaman80 on 2010-03-26
I am having the same problem, downloading 9.02 now.  How well does the iphone sync / update work in virtualized win 7?  Will i have a constant fight on my hands?

---

### Post by Rob_H on 2010-06-27
You can run the latest version of iTunes under VirtualBox by enabling VT-x/AMD-V hardware acceleration if your processor supports it. Look for the setting under System > Acceleration in the virtual machine settings dialog. This solution is discussed on the [Apple forums]("http://discussions.apple.com/thread.jspa?threadID=2322501&start=60&tstart=0"). Presumably, iTunes is using some esoteric feature of the processor that doesn't work correctly in VirtualBox unless you flip this switch. Hope it helps you.

---

