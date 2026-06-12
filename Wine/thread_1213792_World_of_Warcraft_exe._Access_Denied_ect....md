---
title: "World of Warcraft exe. Access Denied ect..."
date: 2009-07-15
forum: Wine
---

### Post by MysteriousMayonaise on 2009-07-15
So I just got Linux on my laptop and want to play some games, World of Warcraft included. When I got Wine installed, I tried to open the World of Warcraft exe., first time it didn't do anything. So I did a few things like trying to download Wine manually, and they didn't really work, then I tried to download Wine again from the Add/Remove section of Applications. This time when I try to open the exe. it says "Access Denied". I can't copy anything, nothing. How can I solve this?

---

### Post by MysteriousMayonaise on 2009-07-15
> **MysteriousMayonaise said:**
> So I just got Linux on my laptop and want to play some games, World of Warcraft included. When I got Wine installed, I tried to open the World of Warcraft exe., first time it didn't do anything. So I did a few things like trying to download Wine manually, and they didn't really work, then I tried to download Wine again from the Add/Remove section of Applications. This time when I try to open the exe. it says "Access Denied". I can't copy anything, nothing. How can I solve this?

Nobody replied to my last thread.

---

### Post by MysteriousMayonaise on 2009-07-15
Could somebody help me with this please? I really don't know what to do and am getting very very frustrated.

---

### Post by philcamlin on 2009-07-15
to reinstall you do sudo apt-get purge wine

then sudo apt-get install wine 

and try right clicking on the .exe and see if there is a chick in the box next to "use as excecutible" or whatever 

hope that helps :)

---

### Post by lisati on 2009-07-15
People have seen it: [http://ubuntuforums.org/showthread.php?p=7619608#post7619608](http://ubuntuforums.org/showthread.php?p=7619608#post7619608)

---

### Post by overdrank on 2009-07-15
Please do not create multiple threads on the same issue. It is polite to bump your thread once a 24 hr period. Threads merged :)

---

### Post by Maheriano on 2009-07-15
Just wanted to let you know I read your problem but can't help. Don't know how.

---

### Post by MysteriousMayonaise on 2009-07-15
> **philcamlin said:**
> to reinstall you do sudo apt-get purge wine

then sudo apt-get install wine 

and try right clicking on the .exe and see if there is a chick in the box next to "use as excecutible" or whatever 

hope that helps :)
I got the first two codes to work in the terminal, but I can't see the chick in the box next to "use as excecutible. I still get "Access Denied" when I try to open the .exe.


I also have to add, that I have tried installing Elder Scrolls IV Oblivion on this system, and I've had even less success. When I try to open it with Wine, it literally doesn't do anything, just loads for 20 or 30 seconds, then stops.


I made a Ubuntu 9.04 disk on my PC, and am very tempted to just reformat this whole laptops hard drive with it. I just don't want to download every single thing. I had Linux installed at a little cyber cafe nearby. So I don't know if I would be able to get all the things he got on my laptop on it myself.

---

### Post by DRajagopal on 2009-12-13
I'm sorry if I'm resurrecting an old thread . I came here because I got the same error when I ran a wow update . What worked for me is selecting the folder itself from the Places system menu . Which means you go to .wine/drive_c/Program Files first right click on the World Of Warcraft folder -> properties -> Permissions tab and give Folder Access Create and delete files and file access read and write to owner . If that doesnt work try giving it to group and if that fails other . Another way to do this would be to cd /home/<username>/.wine/drive_c/Program Files and do a chmod -R u+rwx World\ of\ Warcraft/ etc (etc standing for the group and other if owner doesnt work for you as in g+rwx and o+rwx instead u+rwx) .

Hope this helps you get past the access denied error .:)

---

### Post by arkanabar on 2009-12-15
The problem is known to the Wine community.  Basically, the Launcher (Launcher.exe) turns off ALL permissions for the directory it's in.  

```
chmod 755 "/home/{username}/.wine/drive_c/Program Files/World of Warcraft"
```

then launch Wow.exe from your file manager -- right click and select "Launch using Wine Programs Loader", or else right-click and select "Properties" then the "Open With" tab, then select "Wine Program Loader" -- this works in both Nautilus and PCmanFM in my experience.  I also suggest bookmarking your WoW folder in your file manager.

---

### Post by Alatar1 on 2009-12-15
Forget all the rest of those, go here [http://ubuntuforums.org/showthread.php?t=1330927](http://ubuntuforums.org/showthread.php?t=1330927) problem solved.

sorry if that seems rude, its just about the 1000th time someone posted about that problem...

---

