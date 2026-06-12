---
title: "How to Reset or fix the XFCE Panel back to Setting I had"
date: 2016-10-27
forum: Ubuntu/Debian BASED
---

### Post by UltimateCat on 2016-10-27
[LEFT]I'm running Voyager which was Ubuntu 14.04. VLC and other programs and things became unstable so  I upgraded to Ubuntu 16.04.[/LEFT]
 [LEFT]The Upgrade took about 4 hours.[/LEFT]
 [LEFT]
 [/LEFT]
 ```
 cat /etc/os-release
NAME="Ubuntu"
VERSION="16.04.1 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.1 LTS"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
UBUNTU_CODENAME=xenial
 
```


 [LEFT]The Terminal Emulator used to be in my Panel among, Back Up, Synapse, The American Flag and other Icons.[/LEFT]
 [LEFT]After playing with the settings in the XFCE Panel Switch somehow I choose the wrong thing didn't know I should of saved the configuration and now all the Icons that were there are gone.[/LEFT]
 [LEFT]
 [/LEFT]
 [LEFT]Here's what the Panel looked like before I made a mess with the XFCE Panel Swich:[/LEFT]
 [LEFT][http://i1052.photobucket.com/albums/s447/Ultimatecat/Voyager%20Panel.png](http://i1052.photobucket.com/albums/s447/Ultimatecat/Voyager%20Panel.png)[/LEFT]
 [LEFT]
 [/LEFT]
 [LEFT]I tried right clicking on the Panel> Add new item but Terminal Emulator isn't in the list and using the search bar it doesn't come up.I also tried XFCE Terminal and that didn't show in the search.

How do I set the Panel back to what I originally had?

[/LEFT]

---

### Post by howefield on 2016-10-27
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by yetimon_64 on 2016-10-27
As a bit of a long shot, I would suggest you have a look in ~/.config/xfce4/panel amongst all the launcher folders. Try setting the executable bit on all the launchers in each folder and see if you can find the old panel launchers/items there. You will need to select each folders contents and set the executable bit just to see what the items in the folder are (that is, to show their icons).

If you do find them you may be able to drag and drop them and "Create Laucher" from them directly on the new panel. I just tried here on an xfce4 panel and I can do so, but in your case it all depends if the old items are still in the ~/.config/xfce4/panel/launcher-# folders. 

If they are not I don't see how you will be able to recover the old set up without a backup of the configuration. Good luck, yeti.

---

### Post by ajgreeny on 2016-10-27
If your original was the default that you had when first installed you can simply rename the **~/.config/xfce4/panel** folder mentioned above by yetimon_64 and let the system create a new panel config the same as default, but if you had configured it yourself to something different and you have no backup of your files and folders, I'm afraid you will have to go through all the configuration again.

At least you have the image of the old panel so can easily remake it as it was.

A lesson learned perhaps? Always keep backups!

---

### Post by UltimateCat on 2016-10-27
Thank You both for the quick reply.

I'll look in the config of xfce4/panel and see what's going on.

I'll let you know what happens.

---

### Post by vasa1 on 2016-10-27
Duplicate thread with some responses here: [https://ubuntuforums.org/showthread.php?t=2341314](https://ubuntuforums.org/showthread.php?t=2341314)

---

### Post by UltimateCat on 2016-10-27
I found the launcher folder's via the terminal but I don't get how to get into each individual folder to see what's set--

```
bash-4.3$ ls ~/.config/xfce4/panel 
launcher-10  launcher-11  launcher-12  launcher-9
bash-4.3$ 

```

How do I have a look inside each folder to see the config?

---

### Post by yetimon_64 on 2016-10-27
> **UltimateCat said:**
> I found the launcher folder's via the terminal but I don't get how to get into each individual folder to see what's set--

```
bash-4.3$ ls ~/.config/xfce4/panel 
launcher-10  launcher-11  launcher-12  launcher-9
bash-4.3$ 

```

How do I have a look inside each folder to see the config?

Use the file manager (GUI method), open your home folder and press the "Ctrl + h" keyboard combination to show hidden files and folders in your home folder. 

Go to .config > xfce4 > panel then open all the folders named launcher-# (# is any number) one by one to look for any of your old items/launchers etc. There are usually a few folders there, depending on how the panel is set up. In any specific launcher-# folder left click and drag a selection over the contents, right click any of the selected icons and choose Properties > Permissions and tick the box at the bottom of the permissions tab (may take a couple of clicks to get a full tick in the box with a multiple selection). 

When you set the executable bit the icons will show up for the launcher/item, this way you may be able to find your older, now missing, items being stored there (hopefully they are still somewhere in there). If they are there you may be able to drag and drop them back onto the new panel to rebuild your old set up.

---

### Post by UltimateCat on 2016-10-28
Thanks Yeti!

I figured it out. Those files were hidden:-

Sadly there are 45 individual launcher files. Some are for the desktop while others are for the browser and etc.
I'll go through them and see if I see any of my old items.

I suspect I won't find any old items as I didn't know to save the configuration:-
If I'm not able to follow your instructions...........

I think I'm better off performing a fresh installation of Voyager (Ubuntu and Xubuntu 16.04.1)

Yup, a lesson well learned:-

I had a backup, that wasn't the problem.
I needed to save the configuration and didn't know that until it was too late:-:(

---

### Post by ajgreeny on 2016-10-29
Great! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by UltimateCat on 2016-10-29
A fresh install was a complete success:-
[http://voyagerlive.org/index.php/tuto-voyager-16-04-lts/comment-page-1/#comment-73647](http://voyagerlive.org/index.php/tuto-voyager-16-04-lts/comment-page-1/#comment-73647)

---

