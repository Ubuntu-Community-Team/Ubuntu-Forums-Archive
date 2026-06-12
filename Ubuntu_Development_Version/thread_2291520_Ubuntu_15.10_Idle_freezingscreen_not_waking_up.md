---
title: "Ubuntu 15.10 Idle freezing/screen not waking up"
date: 2015-08-20
forum: Ubuntu Development Version
---

### Post by aziz07 on 2015-08-20
Hi,

I am using Ubuntu 15.10 with default Xorg drivers but when I leave my laptop idle for 10min or more, I often find it frozen with either screen off or screen on. I confirm the freezing with screen off by pressing numlock key which doesn't respond anymore. Only a hard reboot with power button long press works.
I have settled for Xorg drivers as Nvidia drivers bundled with Ubuntu did not let me login after install; its logging out automatically after I input my pw. I wasn't able to install nvidia beta 355 .run drivers as opening them does nothing even with permission for execution.

thanks

---

### Post by dino99 on 2015-08-21
which kind is session is opened ? (DE)
avoid installing driver from .run, there is the xorg-edgers ppa to get the latest driver fine tuned for ubuntu & the likes
so start purging the installed one before installing the ppa's driver (then deactivate the ppa)

---

### Post by aziz07 on 2015-08-22
Hello,
I reverted to Ubuntu 15.04 and no more freezing issues. How do I get the xorg-edgers ppa and is it stable?

thank you

---

### Post by f-info-3 on 2015-09-28
Hi
I have same problem
And I have set the "screen turn off" setting to "never" to overcome problem.
But every morning I have to shut down and start up system to get screen.
And I can't go back due to some reasons.
Any solution except downgrading system?

Thanks
Ert

---

### Post by rrnbtter on 2015-09-28
Greetings,
I'm having the same issue with an Intel system so I doubt that it has anything to do with Nvida. Also, It doesn't seem to be kernel related since it persists across the RC versions. It seems to me that it has to be lib related but no opinion where. In any case downgrading to 15.04 kind of defeats the purpose of running a dev version in the first place so its just business as usual for me.

---

### Post by psylem on 2015-11-05
I had this issue and fixed it by downgrading my nVidia drivers from v352.41 back to 346.96. After upgrade I immediately selected the highest version drivers available and incorrectly attributed the systems refusal to wake up with the Ubuntu upgrade.

---

### Post by philinux on 2015-11-05
Thread closed we are now on Xenial thanks.

---

