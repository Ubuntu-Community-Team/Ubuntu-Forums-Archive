---
title: "installing city of heroes in wine 1.1.28"
date: 2009-08-30
forum: Wine
---

### Post by xstackerx on 2009-08-30
Im in desperate need of someone who can tell me how i install and download city of heroes/villains, using wine. i am currently running ubuntu 9.04 jaunty version. Please help me. I know its possible but im very new to linux period. So please let me know asap. Thanks

---

### Post by Rocket2DMn on 2009-08-30
Moved to the Wine forum area.

---

### Post by NightMKoder on 2009-08-30
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2980](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2980)

Just update to wine 1.1.28, and install it. Seems like it works perfectly.

---

### Post by xstackerx on 2009-08-30
i have 1.1.28. then i open the cohupdater.exe with the wine emulator thing and it starts downloading at like 9.0k/sec. and then after a while it just disappears and stops downloading. ive tried it like 5 times. not sure what im doing wrong.

---

### Post by NightMKoder on 2009-08-30
Try applying the patches manually, ie find them online and run them.

EDIT: the bug you're describing is [http://bugs.winehq.org/show_bug.cgi?id=16916](http://bugs.winehq.org/show_bug.cgi?id=16916) , there is a fix at the end.

---

### Post by ExplicitViper on 2009-08-30
1. Install the base Linux operating system.

2. Install the restricted drivers (proprietary) for your video card.

In Ubuntu 7.10 it's as easy as enabling them in System > Administration > Restricted Driver Manager.

After the install you will need to restart Ubuntu for the restricted drivers to start.

3. Install Wine on you system.

4. Install City of Heroes.

The easiest way is to simply put your City of Heroes CD in and in the CD right click on Setup.exe > Open with other Application > Wine Windows Emulator.

Follow the install directions as normal and updates as normal.

5. After installing and before playing City of Heroes for the first there are a few things you will want to do.

a. Ensure your visual effects are set to "none". System > Preferences > Appearance > Visual Effects.

b. Currently the settings in City of Heroes won't manage your graphics card Antialiasing.

If you have an Nvidia card it's easy to adjust this. Simply type nvidia-settings in a terminal window and the Nvidia settings manager will open.

Go to Antialiasing Settings and adjust it to override application settings accordingly.

c. Desktop Icon. If City of Heroes did not add a desktop icon for you, right click on the desktop and click create launcher.

The command used should look something like: "/home/yourhomefolder/.wine/drive_c/Program Files/City of Heroes/CohUpdater.exe" With you home folder used and including the quotations.

6. Launch City of Heroes.

---

### Post by xstackerx on 2009-08-31
k so i finally got city of heroes to do something. now i can play but the only way i can is if i go into safe mode. how can i fix it to where i can just log in normally? is there some kinda command i should be using in my terminal?

---

