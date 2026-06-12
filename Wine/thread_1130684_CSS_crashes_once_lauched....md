---
title: "CS:S crashes once lauched..."
date: 2009-04-20
forum: Wine
---

### Post by LogicalOne on 2009-04-20
I get to the part that has the server information and it just crashes. I've installed the ATI 9.4 drivers and I am running Jaunty. Wine itself works fine--IMGBurn works; what could this be?

The game just resets to desktop after like 4 seconds. I've checked to confirm the drivers are properly installed--they are. I have an HD4850 so it's not a capability issue?

Any ideas?

Thanks in advance.

---

### Post by asdfoo on 2009-04-20
> **LogicalOne said:**
> I get to the part that has the server information and it just crashes. I've installed the ATI 9.4 drivers and I am running Jaunty. Wine itself works fine--IMGBurn works; what could this be?

The game just resets to desktop after like 4 seconds. I've checked to confirm the drivers are properly installed--they are. I have an HD4850 so it's not a capability issue?

Any ideas?

Thanks in advance.

Well ati drivers are not nearly as good as the nvidia drivers, regardless of how much you have paid for the hardware... but that aside, have you checked the AppDB?

One thing to try is setting OffscreenRenderingMode to fbo using regedit, 

HKCU, Software, Wine, Direct3D (create this key), make a new String value named OffscreenRenderingMode and set the value to fbo.

close regedit and try launching CS:S again.

---

### Post by u235sentinel on 2009-04-20
> **LogicalOne said:**
> I get to the part that has the server information and it just crashes. I've installed the ATI 9.4 drivers and I am running Jaunty. Wine itself works fine--IMGBurn works; what could this be?

The game just resets to desktop after like 4 seconds. I've checked to confirm the drivers are properly installed--they are. I have an HD4850 so it's not a capability issue?

Any ideas?

Thanks in advance.

I've had a lot of issues with ATI when it comes to Linux especially high end graphics.  I wouldn't recommend them.  I'm currently running an Nvidia 9800GTX+ which works great so far with my games and programs.

---

### Post by LogicalOne on 2009-04-20
Guess I'll go back to XP on this comp and have my comp with the 9800 GTX+ set up with Ubuntu. Or possibly use WUBI.

I love everything about Ubuntu but the gaming. I have a slightly used system with a faulty mobo that I'll fix and install ubuntu on.

---

