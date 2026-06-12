---
title: "Can't reliably foot 14.04 in a virtualbox vm"
date: 2015-04-02
forum: Virtualisation
---

### Post by Adam_Felson on 2015-04-02
I've run ubuntu in a virtualbox vm hosted on windows for years now and never had the slightest problem.

Until I tried 14.04.  Like everywhere else I've tried 14.04 (server, native on a laptop) it has been a complete disaster.

4 out of 5 times it'll lock up -- purple screen of death?  Only recourse is a hard reset.
When it does finally make it to starting X, there will be a half dozen "system program problem detected" against a black background.
Clicking on "report" is the same as clicking on "cancel".  Trying to report the problem does nothing that I can see.
About 60% of the time, clicking cancel on the dialogs does nothing and the system stays in a locked up state;  again a hard reset is the only recourse.

When it finally gets around to displaying the desktop, that process often can take the better part of 5 minutes.  Or come up in 10 seconds.  I never know.

Is there any way to diagnose these lockups?  I tire of needing to lose a half hour of my time every time I try to bring up ubuntu 14.04 within virtualbox.
Virtualbox version:  4.3.26
Ubuntu uname -a: Linux afelson-VirtualBox 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:33:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by TheFu on 2015-04-02
Can you post your VM settings?
[http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox) -is what I've used for years to make it work fast.
Post if you have any issues/questions with those settings. Main thing I recommend - don't use Unity or any desktop that demands 3D accel hardware.

Also, if this is an issue with other VMs too, perhaps a reinstall of virtualbox is needed?  Don't forget to update the guest additions - they need to match versions between the hostOS and the guestVM.

---

### Post by oldos2er on 2015-04-02
Moved to Virtualisation.

---

