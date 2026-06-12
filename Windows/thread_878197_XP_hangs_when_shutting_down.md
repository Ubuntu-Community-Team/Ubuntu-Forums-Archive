---
title: "XP hangs when shutting down"
date: 2008-08-02
forum: Windows
---

### Post by Sand &amp; Mercury on 2008-08-02
I've got this problem on my girlfriend's computer; it had a major onset of the gremlins lately, being infested with spyware/viruses until I threw AVG and AdAware on it and cleaned it out, but there's still this problem remaining.

When shutting down, everything seems peaches until a certain point; it logs out, gets past 'saving your personal settings', but on about 4/5 occasions it will hang on 'Windows is shutting down' and can only be switched off by holding the power button for a few seconds.

Could anyone think of where I could look to track this problem down? Does Windows keep logs anywhere of this kind of thing?

---

### Post by tamoneya on 2008-08-02
look in event manager.  I think (its been a long time) it is in controlpanel -> administrative tools -> event viewer.  There might be something in between admin tools and event view but i cant really remember...

---

### Post by jualin on 2008-08-02
Maybe reinstalling will make it work. :lolflag:

---

### Post by jualin on 2008-08-02
> **tamoneya said:**
> look in event manager.  I think (its been a long time) it is in controlpanel -> administrative tools -> event viewer.  There might be something in between admin tools and event view but i cant really remember...
Yes that's the correct locations for the logs, however the logs in Windows are not as specific as the logs in Linux. Good luck!

---

### Post by tamoneya on 2008-08-02
> **jualin said:**
> Yes that's the correct locations for the logs, however the logs in Windows are not as specific as the logs in Linux. Good luck!

I never said they would be very descriptive but if it was logged thats where it would be.

Good luck


I agree the simplest way is probably to just reinstall.

---

### Post by fiddledd on 2008-08-03
It was a known problem with XP before SP1 [KB307274](http://support.microsoft.com/?kbid=307274). If the logs don't tell you anything you could try uninstalling AVG and Adaware if you never had the problem before. Often when XP hangs on shutdown it's a service causing it and I would guess AVG installs at least 1 service.

---

### Post by RavUn on 2008-08-04
My brother's computer has this problem.  I've been trying to mess with it but couldn't figure it out.  His hangs when shutting down and when starting up.  It'll hang on the XP splash screen when starting up and the shutting down issue is the same as yours.

Let me know if you figure it out.  I've tried looking at the bootlog... but the boot log doesn't seem helpful if I can't boot, and if I can boot I assume the issue is not in the log!  It starts in safe mode just fine so I think it's an issue with loading a driver.  I figure it's related to the shut down issue.

---

### Post by fiddledd on 2008-08-04
> **RavUn said:**
> My brother's computer has this problem.  I've been trying to mess with it but couldn't figure it out.  His hangs when shutting down and when starting up.  It'll hang on the XP splash screen when starting up and the shutting down issue is the same as yours.

Let me know if you figure it out.  I've tried looking at the bootlog... but the boot log doesn't seem helpful if I can't boot, and if I can boot I assume the issue is not in the log!  It starts in safe mode just fine so I think it's an issue with loading a driver.  I figure it's related to the shut down issue.

If it boots OK in Safe Mode then it's probably a driver. Boot into safe mode and use msconfig to disable all services, then boot normally, it should boot OK. Then enable one service and reboot. Keep doing this until you can't boot, then the last service you enabled is the culprit, so boot into Safe Mode and disable it, then reboot. If this doesn't make sense it because I'm rushing, I'll have more time a bit later or tomorrow. Oh, in case you don't know where it is, Start->Run then type msconfig.

---

### Post by RavUn on 2008-08-04
Awesome, I'd heard to do this but never actually knew how.  Thanks.

---

### Post by jualin on 2008-08-05
> **RavUn said:**
> Awesome, I'd heard to do this but never actually knew how.  Thanks.

Let us know if the problem is now solved.

---

