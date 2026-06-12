---
title: "Question on System76 driver update in Update Manager"
date: 2009-11-13
forum: System76 Support
---

### Post by PoachedSalmon on 2009-11-13
I'm a complete newbie to Linux and just got a Starling a couple of weeks ago. Tonight I have an update for the System76 driver in Update Manager. However, for the description of the update, under Changes, it just says #Failed to detect distribution#. The size of the update is 817kb.  Does anyone know what that means?  I don't want to cause any problems if I install the update. I probably wouldn't have a clue how to fix it.    Thanks in advance.

---

### Post by PoachedSalmon on 2009-11-14
Anyone? The driver update appeared after I clicked Check in Update Manager.

---

### Post by allersj on 2009-11-14
I would hold off on applying that update, unless you hear otherwise from one of the System76 folks.

I don't think there is anything in the update you need, unless you are running 9.10.

---

### Post by Vadi on 2009-11-14
> **PoachedSalmon said:**
> Anyone? The driver update appeared after I clicked Check in Update Manager.

The update changelogs are only available for packages from the repository. Anywhere else, it won't work. It's a current limitation of the Update Manager.

So since the system76 driver comes from their own repository, not the official ubuntu one - there is no changelog (and it gives that non-user friendly error message, unfortunately).

I wouldn't worry about it and upgrade since it's available.

---

### Post by PoachedSalmon on 2009-11-14
Allersj, thanks for the reply. I'm running 9.04. There is another update listed for tzdata, but I'll wait to hear from System76, hopefully on Monday, before I install either of them. Something definitely isn't working right. When I turn on the system, I don't get an automatic notification (like I usually do) that there are updates available. I have to launch Update Manager to see that those 2 updates are still there.     To Vadi: So, if I do install the updates, are you saying that the System76 driver update is just a phantom; meaning nothing would happen to the driver?

---

### Post by Vadi on 2009-11-14
No, it would update the driver fine with the new version. Just ignore the error :)

Also, the Update Manage auto-opens only if there are security updates available. For other types, it doesn't bother you so much.

---

### Post by PoachedSalmon on 2009-11-14
Thanks, Vadi.

However, it would be nice if there was an online list somewhere from System76 indicating that a new version of the driver is available and why the update is necessary. I thought that version 2.3.9 was the version we should be using and that's the one I have already installed.  


When my Mac notifies me of updates, I can go to Apple support online and get another list of what exactly is being installed as confirmation. And I know there is an online list of updates to Ubuntu.

---

### Post by Vadi on 2009-11-14
Well, it is maintained here: [http://knowledge76.com/index.php/System76_Driver_Changelog](http://knowledge76.com/index.php/System76_Driver_Changelog)

But Thomas Aaron would need to update the wiki I guess.

My laptop doesn't need anything from the system76 driver as Ubuntu already by default provides everything, so I just forgot about it myself :)

---

### Post by PoachedSalmon on 2009-11-16
Bump in hopes that Thomas Aaron sees this and can comment.

---

### Post by thomasaaron on 2009-11-16
Hi, Poached Salmon.

It's OK to install the update. We used to maintain an online list of fixes applied for the driver, but at some point it fell into disuse.

There have been a number of requests lately to revive it, so I'll talk to my managers about that.

In the meantime, the System76 driver is always backwards compatible, and you can always download it and run it if it appears in Update Manger.

---

### Post by PoachedSalmon on 2009-11-16
OK, thanks.
 
I guess it was just the "Failed to detect distribution" under Change that made me nervous. I don't recall seeing that for the 2.3.9 update.

---

