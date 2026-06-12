---
title: "Fear"
date: 2010-04-26
forum: Wine
---

### Post by Dadof4 on 2010-04-26
I'm trying to install F.E.A.R. in Wine and I can get the installer to launch and install the first disk. When it prompts me for the second disk I can eject the disk and put the second one in but when I click on OK I get an invalid path error, like it can't detect the second disk or the drive. Any suggestions?

---

### Post by asdfoo on 2010-04-26
> **Dadof4 said:**
> I'm trying to install F.E.A.R. in Wine and I can get the installer to launch and install the first disk. When it prompts me for the second disk I can eject the disk and put the second one in but when I click on OK I get an invalid path error, like it can't detect the second disk or the drive. Any suggestions?

make sure you're using the latest version of Wine, 1.1.43.

Type "wine eject" at the terminal when you're ready to eject.

---

### Post by Dadof4 on 2010-04-26
Thanks for the quick reply. I updated to 1.1.43 and tried the "wine eject" from both the d: and c: drives in the Wine console and get the same issue. 

A little better description of what happens might help a little more too.

From *Run Application* type "wineconsole cmd" and get to a prompt Z:\home\steve. I then switch to the D: where the FEAR install CD is. Type "setup" and the installation starts and the first disk installs fine. When I get prompted to insert the second disk, I go to the console again and change to the C: drive, and then type "eject". I have tried to eject from both C: and D: with the same results. When the disk does eject the tray opens and then closes right away. If I can change the disk, the installation doesn't recognize that it is the second disk and states it's an invalid path.

Kind of odd. Almost like it is stuck on the disk in the drive still being the first disk...

---

### Post by asdfoo on 2010-04-27
> **Dadof4 said:**
> Thanks for the quick reply. I updated to 1.1.43 and tried the "wine eject" from both the d: and c: drives in the Wine console and get the same issue. 

A little better description of what happens might help a little more too.

From *Run Application* type "wineconsole cmd" and get to a prompt Z:\home\steve. I then switch to the D: where the FEAR install CD is. Type "setup" and the installation starts and the first disk installs fine. When I get prompted to insert the second disk, I go to the console again and change to the C: drive, and then type "eject". I have tried to eject from both C: and D: with the same results. When the disk does eject the tray opens and then closes right away. If I can change the disk, the installation doesn't recognize that it is the second disk and states it's an invalid path.

Kind of odd. Almost like it is stuck on the disk in the drive still being the first disk...

Instead of switching to the drive where the cd is located, try:

wine /media/cdrom/setup.exe

---

### Post by Dadof4 on 2010-04-27
No dice. I get File not Found.....

---

### Post by asdfoo on 2010-04-28
> **Dadof4 said:**
> No dice. I get File not Found.....

well, substitute the correct path depending on where ubuntu has mounted the cdrom

first explore to it using a file browser nautilus or whatever to make sure it is mounted then, use the path that is displayed in nautilus

it might be, /media/cdrom-1 or something, it changes

---

