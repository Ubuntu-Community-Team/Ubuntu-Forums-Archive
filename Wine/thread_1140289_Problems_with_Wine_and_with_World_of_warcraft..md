---
title: "Problems with Wine and with World of warcraft."
date: 2009-04-27
forum: Wine
---

### Post by Ouden on 2009-04-27
Hello. I've same problems with wine. First of all, time ago, i've installed wine with deb package. Now I can't update it with repository. 

Next, I've many errors with world of warcraft. With wine 1.1.20, there isn't the cursor, and my mini-map is with (But i've red that thi bug is under development). How do I resolve the cursor's bug?

I've added these lines in my conf file:

> SET gxApi "OpenGL"
SET M2UseShaders "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET ffxDeath "0"
SET ffxSpecial "0"

I've added the string in the registry, too.

---

### Post by Ouden on 2009-04-28
Any idea? I use ATI X1650 with the drivers for ubuntu.

---

### Post by Clopin on 2009-04-28
Could you please tell us the output from terminal when running WoW?
And have you tried running WoW with -opengl at end of command line?

---

### Post by Ouden on 2009-04-28
Maibe is this my error. I always start wow by the double click in the icon...

---

### Post by Doopydoo22 on 2009-04-28
The SET gxApi "OpenGL" line in your config.wtf file eliminates the need to append the launch command with -opengl, so that should be fine.

Otherwise I'm afraid I won't of much help.

---

### Post by Ouden on 2009-04-29
Mmmmmh.... So, I can use WoW with Ubuntu, I must use windows... ç_ç

---

### Post by Guestttt on 2009-04-29
my patch wont download it says my computer seems to be behind a firewall but my firewall is turned off

---

