---
title: "The file is not marked as executable"
date: 2010-07-27
forum: Wine
---

### Post by tobbe654 on 2010-07-27
Whenever I try to install using wine I get the error message saying that the software is not marked as executable. From what I've understood, it means that it is not marked as safe..

This makes wine useless for me.

Is there no way to make it run in wine anyway?

All answers are appreciated!

---

### Post by Bonster on 2010-07-27
right click on file, properties, permission, check mark - allow executing,
done

---

### Post by tobbe654 on 2010-07-29
wow that was embarrassing D: but thanks!

---

### Post by ozz_man on 2011-11-05
I'm having this same problem but it's a file on a CD, can't seem to change it there.  Do I have to copy the files over to a local directory or is there some way to do it from the CD?  That would be best for what I'm trying to do.

---

### Post by Soulcage on 2011-11-06
Try this instead: right click on a .exe file click properties then click open with then wine windows program loader then click set as default then close. See if that works. If you're on a older version of ubuntu you should be able to click add then find it in the list.

---

### Post by ozz_man on 2011-11-06
Thanks for the reply... ending up getting it to work by going through the terminal and using 'wine cmd', then navigating to the executable in the CD from the Windows command prompt.  That worked fine for me... 

Thanks though! :)

---

