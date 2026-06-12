---
title: "Problems with Serp 7 suspend after connecting an external monitor"
date: 2011-12-02
forum: System76 Support
---

### Post by aranaea on 2011-12-02
I recently followed the guide from [http://ubuntuforums.org/showthread.php?t=1887858 ]("http://ubuntuforums.org/showthread.php?t=1887858")
to get the nouveau drivers installed and get my external monitor working.  But now suspend is hanging and just showing the 'Ubuntu' screen.  In order to get out of it I need to reboot the machine.

If I don't connect the external monitor at all then suspend works fine.  But once I've connected the monitor I'm doomed.  It doesn't matter if I disconnect it or try to suspend with it connected, the machine will hang.

I'm running 64 bit Ubuntu 11.10 and Unity on a Serp 7 and using the nouveau drivers.  Any ideas about what might be going on?

---

### Post by isantop on 2011-12-02
We don't do any testing with Suspend on the Nouveau drivers. Does it work if you use the Nvidia Proprietary drivers?

---

### Post by aranaea on 2011-12-02
The nvidia drivers seem to crash X when I try to enable the second monitor.  Both screens go black and the machine becomes unresponsive.  I'd be happy to use them if there is a way to make them work.

---

### Post by isantop on 2011-12-02
> **aranaea said:**
> The nvidia drivers seem to crash X when I try to enable the second monitor.  Both screens go black and the machine becomes unresponsive.  I'd be happy to use them if there is a way to make them work.

It should revert back in a minute or so. After that trying again will usually allow you to configure to monitor properly.

---

### Post by mgolden on 2011-12-02
When you use the nVidia driver, you have to restart X when you make changes.  Log out, and then do a restart X server on the login screen.

---

### Post by aranaea on 2011-12-02
In the past (10.10) I was able to make changes with the NVidia X Server settings app and they would last until I restarted X or made changes again.  That's sorta working now that I've re-installed the drivers but sometimes I have to "apply" the changes a couple of times.

---

### Post by mgolden on 2011-12-03
I am able to suspend/resume with nouveau when I don't have a second monitor plugged in.  I don't have a second monitor available right here so it will have to wait until Monday for the full test.  However, when I google around I do see lots of bug reports about suspend/hibernate and the nouveau driver.  Probably it's worth filing a bug about the particular problem you're having.

---

### Post by mgolden on 2011-12-06
I was able to confirm the bug in the nouveau driver, and have filed a bug report for it on Ubuntu Launchpad.  I was also able to get TwinView to work spreading the screen on two monitors.  I do not know why I didn't do it right before.

I have reworked the knowlegde76 page to reflect the discussion on this thread.

---

### Post by ubuntu27 on 2011-12-07
> **mgolden said:**
> I was able to confirm the bug in the nouveau driver, and have filed a bug report for it on Ubuntu Launchpad.  I was also able to get TwinView to work spreading the screen on two monitors.  I do not know why I didn't do it right before.

I have reworked the knowlegde76 page to reflect the discussion on this thread.


It would be nice if you could post the URL for the bug report. :)

---

### Post by mgolden on 2011-12-13
Here is the bug report:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/900615](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/900615)

---

