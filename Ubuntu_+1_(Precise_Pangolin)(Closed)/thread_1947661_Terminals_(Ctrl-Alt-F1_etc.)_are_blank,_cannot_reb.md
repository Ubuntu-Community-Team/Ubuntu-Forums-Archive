---
title: "Terminals (Ctrl-Alt-F1 etc.) are blank, cannot reboot/shutdown"
date: 2012-03-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by tim1 on 2012-03-27
Hi I am using precise for a while now and as was my experience before with previous dev releases now that we come close to release the really annoying bugs hit.

The first bug is that I cannot switch to the terminals with Ctrl+Alt+F-Keys, the screen just stays blank/black.

The second bug is that I cannot reboot or shutdown the computer. The Screen will turn black aswell and the fans will start to run on full power until I long press the power button to shut it down by force.

I think these problems may be somehow related but I don't know how to debug the second one without fixing the first one.

Any ideas? I used google and the forum search but didn't get helpful results, maybe I used the wrong search terms.

---

### Post by dino99 on 2012-03-27
you might check your logs: xsession-errors & /var/log/
you might check the driver activation: sudo jockey-gtk

and log out/in (ctrl+alt+del)

---

### Post by tim1 on 2012-03-27
I am using the nvidia driver which is working properly.

I rebooted and logged out/in mutliple times, it is a permanent problem.

Also, I looked at the log files but they are huge and I have no idea what to look for specifically.

---

### Post by meborc on 2012-03-27
I also have the issue of kernel panic during reboot/shutdown. I have an ATI card though and so far I thought that ATI drivers were the main cause of that.

I have resulted in Alt+SysRq+RSEIUB sequence for a clean reboot :D ([http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key))

---

### Post by tim1 on 2012-03-27
The key combinations you suggested don't work.

Ctrl-Alt-Del is not for logging out in, it's for reboot, as in Windows, when I press this logged in it just opens a dialog where I can select reboot and shutdown which both don't work, the computer will lock up.

If you meant Ctr-Alt-Backspace, this has been disabled in Ubuntu for a while now.

As for Alt+SysRq+RSEIUB, this does not work either when the computer already hangs, apparently it is really locked up hard.

---

### Post by miguelpires on 2012-03-27
Same Problem, but for me is intermittent, ie, sometimes that happends, some don't. I really wana try to find the bug, if someone can point out how.

---

### Post by meborc on 2012-03-27
> **tim1 said:**
> As for Alt+SysRq+RSEIUB, this does not work either when the computer already hangs, apparently it is really locked up hard.

Yeah, I meant that I use that combination when I need to reboot (before lockup) :)

---

### Post by rapiertg on 2012-03-27
Today i faced this problem too, but I use ATI card. Recentlly i changed to closed drivers and it was the cause. I had to use this old trick for plymouth for fglrx:
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)
It helped for virtual terminals,  ctrl + alt + F* worked again. Dont know if it will help you too with nvidia thou...

As for second problem pc started to not turning off today, so maybe some update broke something...

---

