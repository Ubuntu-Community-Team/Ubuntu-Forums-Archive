---
title: "[SOLVED] Ext. Hard Drive Installation Problem"
date: 2008-12-26
forum: Wine
---

### Post by DucksAndDolphins on 2008-12-26
So I'm trying to run Microsoft FSX with Wine, and it works fine as far as the Installation Wizard goes. The only problem is that I cannot find a folder with enough free space to save the information to before I even start installation. Naturally, this is the reason I got an external hard drive, so that I could have more free disk space. I couldn't find a way to get the information to save to the external, so I tried freeing up space on my regular drive, but that didn't work. How do I configure it so that I can save to the external??

---

### Post by cogadh on 2008-12-26
Add the external drive to Wine as a drive in winecfg.

---

### Post by DucksAndDolphins on 2008-12-26
How do I know what path it is if I'm adding it in winecfg?

---

### Post by cogadh on 2008-12-26
On the Drives tab in winecfg, you just need to create a new fake Windows drive (like drive "E:") with the Linux mount path of the external drive. You will need to confirm for yourself what that mount path is, I don't know where you mounted it on your system. Once you have done that, any Windows software you run should be able to "see" that drive as it would in Windows.

---

### Post by DucksAndDolphins on 2008-12-26
Alright, thanks a bunch.

---

