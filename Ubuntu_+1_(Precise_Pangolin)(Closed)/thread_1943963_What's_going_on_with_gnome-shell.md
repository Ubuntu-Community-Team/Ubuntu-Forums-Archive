---
title: "What's going on with gnome-shell?"
date: 2012-03-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by creata.physics on 2012-03-20
When the beta first came out gnome shell ran okay, but it would run.  Now it runs, but windows are blank (see attachment).  
When I run:
LIBGL_ALWAYS_SOFTWARE=1 gnome-shell --replace

Gnome-shell runs and the windows **do** load, but the fps is so horrible it makes it useless.

I've done all the recent updates that are currently available. How can  fix this? I'm so close to finally running gnome-shell properly for the first time since it came out.

---

### Post by neu5eeCh on 2012-03-20
It's the latest Gnome feature in their continuing effort to simplify and focus the user experience. The reader will no longer be distracted by "window content". Task focusing has been reduced to its essence. ;-)

---

### Post by keithpeter on 2012-03-20
Hello creata.physics

What graphics card are you using?

Proprietary drivers?

I do actually have windows on gnome-shell but I am seeing random freezes (nvidia graphics card and proprietary drivers)

@VTPoet: don't give the User Experience Specialists any more ideas, *please*.

---

### Post by dino99 on 2012-03-20
as you seems having trouble with libGL, this an issue with the nvidia 295.20 in case you are using it, downgrade to 295.10 (nvnews)

---

### Post by Gregory Lee on 2012-03-20
You're getting some nice rectangularity, there.

Gnome 3 has worked off and on for me, using the (older) fglrx driver.  But mostly it works.  After yesterday's updates, I lost it, and rebooting wouldn't bring it back, so I fell back to Gnome Classic.  Today, after more updates, Gnome 3 is working again.  For me.

---

### Post by Harry33 on 2012-03-20
Funny, I am running the newest available gnome-shell release (3.3.90) and with the nvidia proprietary drivers (295.20) + xserver 1.12.
I do not have any issues with gnome-shell.

---

### Post by creata.physics on 2012-03-20
I'm using an intel graphics card unfortunately, i865G. I know I am not even supposed to get the gnome 3 experience, I was just hoping eventually there would be a fix or if there was a cure to this issue. I tried fedora 17 because they said they'd have the full gnome 3 experience but I have the exact same issue with them. I guess I'll just have to continue using the fallback version until I get a new computer.

---

### Post by xebian on 2012-03-20
I had some hung-up issues yesterday but once I re-compiled the kernel modules for 295.20 it went away.  Usually I used -K -k option for my new kernels but if problems comes up I recompile fresh.  BTW I compile my own kernels- 3.3.0 & 3.2.12, and I use the installer from Nvidia if that helps.

---

