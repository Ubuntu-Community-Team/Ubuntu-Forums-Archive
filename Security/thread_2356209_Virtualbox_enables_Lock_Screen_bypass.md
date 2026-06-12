---
title: "Virtualbox enables Lock Screen bypass"
date: 2017-03-20
forum: Security
---

### Post by icoexist on 2017-03-20
(Running Ubuntu 16.04.2)
I noticed this when I returned to my computer after leaving it alone for a bit. I had Windows 7 up fullscreen on my primary monitor when I left (and my secondary just showed my Ubuntu Desktop). My screen is set to turn off after an x amount of time, and lock when the screen goes black.

I returned to the computer to continue some work, and noticed that the machine came right back up -- and I could still see my Ubuntu Desktop on my second screen. I moved and clicked my mouse on my secondary monitor, then moved it back to the VM. The computer froze for a split second only to display the Lock Screen for maybe .5 seconds, then flashed away and returned to the VM. At this point, I knew what I saw -- my lockscreen was just bypassed. I was then able to lower my VM from fullscreen and continue using the system without ever typing the password that is supposed to be required. This problem can be reproduced several times, sometimes locking, however most of the time it flashes the lock screen, then *magically* unlocks. 

I looked for similar issues and bugs, however only found this [one]("https://ubuntuforums.org/showthread.php?t=1909965"), which only talks about the vulnerability of the VM, and if the VM windows gets unfocused, the system will lock -- HOWEVER, that is not my case. I cannot tell you if this is only a problem I can reproduce on my system, however if you have a similar setup, do give this a go and see what happens.

Also if there is a different place where this post belongs, please let me know! I just saw this and **had** to report it. I also have a video of this, but I didn't want to just stick it up anywhere for the world to see. Then again I'm kinda doing that with this post... Right.

---

### Post by QIII on 2017-03-20
Hello!

Your thread is just fine here, and we'll see if you get some support.

But this is not a bug reporting venue.  It's a voluntary user to user support forum.  Nobody here works for Canonical or develops Ubuntu (well, there are a couple of people who wander in and out very occasionally ...).

To report the ***bug***, you might try [https://launchpad.net/](https://launchpad.net/) (for reporting to Canonical) or [https://www.virtualbox.org/wiki/Bugtracker](https://www.virtualbox.org/wiki/Bugtracker) (for Virtualbox).

Cheers!

---

