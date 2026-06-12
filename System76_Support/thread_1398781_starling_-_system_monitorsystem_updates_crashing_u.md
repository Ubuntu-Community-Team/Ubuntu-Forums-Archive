---
title: "starling - system monitor/system updates crashing ubuntu"
date: 2010-02-04
forum: System76 Support
---

### Post by Thepookster on 2010-02-04
Brand new Staling, just arrived today, a little disappointed at the moment. 

Got a system lock up with nothing but a black screen when I tried launching the system monitor, had to power cycle and hard boot.

Tried running the latest updates, system crashed again with a black screen, again had to power cycle.  now the computer just locks up at the login screen with an error and then freezes, I cant even use the computer at this point

Error in the top right corner at login screen:
the configuration defaults for GNOME power manager have not been installed correctly, please contact system administrator.

 I'm assuming this is due to the computer crashing while installing updates.

Any ideas?

---

### Post by Thepookster on 2010-02-04
Wondering if this has anything to do with the errors I was getting regarding the repository, it kept hanging when reloading the software list and saying it could not locate certain repositories with a URL that had some type of system76 driver domain.

Also trying to load the page for restoring your system (figured I could do this since nothing important is on it yet) but getting page loading errors.

---

### Post by jml on 2010-02-05
Another thread comments on the fact that both System 76 web sites are having problems.  So any attempt to download anything from them right now will fail.

---

### Post by thomasaaron on 2010-02-05
DON'T WORRY! WE HAVEN'T GONE AWAY!

Our web hosting service is experiencing a data center-wide outage. We are currently transferring our site to other servers and expect this process to take a couple of days.

While we will be unable to take orders while the site is down, we are still available via forums, phone and email to answer any sales or support questions you have.

This will also keep the System76 Driver from running, as it pings our website to determine that there is an Internet connection. We're sorry for this inconvenience.

Please see...
[http://ubuntuforums.org/showthread.php?t=1399130](http://ubuntuforums.org/showthread.php?t=1399130)
...for further updates on our website.

Tom Aaron
[email]support@system76.com[/email]
720-226-9269

---

### Post by jangat on 2010-02-21
Has there been any resolution to this problem?
 
I received my starling on Feb 19 with 9.10 loaded. I loaded the System76 drivers from their web site but have done no other updates.

I also get a black screen of death when I try to run the System Monitor. There are no error messages. Like the OP, I have to cycle the power to reboot.

Any ideas?

---

### Post by thomasaaron on 2010-02-22
jangat,

We're not working on this particular bug right now. Instead, we're trying to get the driver included by default in the next version of Ubuntu. That will *probably* fix the System Monitor bug and several other issues.

---

### Post by Schrollini on 2010-02-23
I too can reproduce this problem.  This looks like a kernel panic to me.  In X, the screen goes black except for a text cursor in the upper left-hand corner and the mouse cursor where it had last been, and the caps-lock light blinks.

If I switch to a VT, I can get nearly the same behavior, but with an error message also present:

```
:~$ export DISPLAY=:0.0
:~$ gnome-system-monitor

** (gnome-system-monitor:1979): WARNING **: SELinux was found but is not enabled.

[  436.144602] Kernel panic - not syncing: stack-protector: Kernel stack is corrupted in: c049e1f5
[  436.144612]
[  436.145303] [drm:intelfb_panic] *ERROR* panic occurred, switching back to text console
```

This isn't a lot to go on, and I'm not seeing any panic information in /var/log/messages.  My WAG is that intelfb means Intel framebuffer, and this panic was instigated by the video driver.  But I'm way out of my league here and may be completely off base.

ETA: Sorry **thomasaaron**, I completely overlooked your post above.  Sounds like you guys already have a pretty good idea what the problem is.

---

