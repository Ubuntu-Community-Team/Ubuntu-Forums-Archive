---
title: "Kubuntu with Dan's Guardian Script???"
date: 2007-06-18
forum: Ubuntu Christian Edition
---

### Post by shane2peru on 2007-06-18
Hey, I have switched to Kubuntu.  I had to install from scratch as just installing kubuntu-desktop left me with no icons in KDE.  Tried for over a week and could not fix it.  Any way, I was wondering if anyone has installed Dan's guardian with Jeremy's script on Kubuntu?  I would like to install it, but would like to know if someone else has gotten it to work on Kubuntu.  Thanks!

Shane

---

### Post by mysticrider92 on 2007-06-19
Kubuntu is Ubuntu with KDE as the default desktop (you probably already know that), so the only thing that might not work right is the GUI, but with the gtk libraries that should work too. I personally don't use KDE, so I am not completely sure if it will work, but it should.

---

### Post by shane2peru on 2007-06-19
> **mysticrider92 said:**
> Kubuntu is Ubuntu with KDE as the default desktop (you probably already know that), so the only thing that might not work right is the GUI, but with the gtk libraries that should work too. I personally don't use KDE, so I am not completely sure if it will work, but it should.

Well, it was a nice thought.  Problem #1 no zenity installed, I installed that and ran into problem #2 - gksu doesn't seem to work with KDE.  Haven't gotten further.  I can either edit the script, or install it all myself and run the the guides to configure it.  I have done it before, but really like the nice GUI for the settings.

Shane

---

### Post by k1001001 on 2007-06-19
In KDE, you get graphical root access by using 'kdesu'. 'gksudo' is for the GNOME (regular Ubuntu) desktop environment.

---

### Post by shane2peru on 2007-06-19
> **k1001001 said:**
> In KDE, you get graphical root access by using 'kdesu'. 'gksudo' is for the GNOME (regular Ubuntu) desktop environment.

Thanks.  I can probably just go in and edit the script then and anywhere it says gksudo change it to kdesu.  Or I just noticed too that I can install gksudo via apt-get.  I may give that a try.  If it has a gazillion dependencies, then I will edit the script.  Thanks.

Shane

---

### Post by shane2peru on 2007-06-19
> **shane2peru said:**
> Thanks.  I can probably just go in and edit the script then and anywhere it says gksudo change it to kdesu.  Or I just noticed too that I can install gksudo via apt-get.  I may give that a try.  If it has a gazillion dependencies, then I will edit the script.  Thanks.

Shane

Ok, I edited the script to say kdesu instead of gksudo.  It worked and installed!  However, it didn't work after that.  I was able to open the GUI thing, but, it wouldn't change any settings it said it was, but it really wasn't.  I'm sure it too uses gksudo.  I looked around a little at it but was not able to determine how to fix it at all.  Oh, well.  I had to uninstall all the programs it installed, and now we know it doesn't work with KDE!  :)  I guess we are stuck with installing by hand, and editing by hand. 

Shane

---

