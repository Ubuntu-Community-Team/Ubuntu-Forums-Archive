---
title: "How to Run steam games installed in windows on Ubuntu"
date: 2009-12-24
forum: Wine
---

### Post by taqkavar on 2009-12-24
I googled around and found no solutions for running my steam games which are installed in my windows partition in Ubuntu, basically I wanted to share the same installation between linux and windows. It was surprising how simple it actually is, so I'm posting about it here in case someone is  searching with no results, and doesn't have enough HDD to just reinstall the same game in his Ubuntu partition. 

1- Boot in windows, install steam and install your games
2- Boot into Linux, and install steam.
3- Go to C:\Program Files or wherever you installed your windows steam, right click on your steam folder and click "Make link"
4- Cut and paste the "Link to Steam" file into ~./wine/drive_c/Program\ Files
5- Delete your Linux steam folder, rename "Link to Steam" to "Steam".

Now just run steam via wine, I tested it with my TF2 installation, and it worked fine. (Don't forget the -dxlevel 81 launch option for TF2)

---

### Post by DrMelon on 2009-12-24
I already do this :P

---

### Post by beastrace91 on 2009-12-24
I'd just like to throw a warning out here for anyone who is doing a setup like this - running Steam games through Wine off of an ntfs partition is known to cause stability issues with many applications.

Just as a heads up - a good middle ground is to create a fat32 partition to dump all of your games onto.

Merry Christmas,
~Jeff

---

### Post by Lamellama on 2010-12-21
Thanks

---

### Post by cong06 on 2010-12-23
woo! Sweet fix!

beastrace91, I'm curious. I'm gonna stick to windows for playing games, but for downloading I like to do other stuff.
These stability issues, would I have any problems just downloading to ntfs (not running games off ntfs)?

---

### Post by cong06 on 2010-12-23
I just noticed that when I switch between Windows and Linux, Steam requests to update. (well, doesn't request) and so I have to wait 10 minutes for it download and install before I can use it.

Is there any way I can give both Ubuntu and Windows their own installation of Steam, but have them share settings?

---

### Post by cong06 on 2010-12-31
Ok, well, I installed Steam on both Windows and Linux, but instead of linking the whole folder I only linked "steamapps"

This seems to almost do the trick, but not quite. There's still a wait for updating between switching, though it does seem minimal in comparison.

---

