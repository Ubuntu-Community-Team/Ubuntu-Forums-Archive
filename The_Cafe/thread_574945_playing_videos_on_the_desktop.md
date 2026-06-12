---
title: "playing videos on the desktop"
date: 2007-10-13
forum: The Cafe
---

### Post by lunamystry on 2007-10-13
I saw a friend of mine who is on mswin vista and he had this cool application that allowed him to play videos on the deskop instead of having a wallpaper. so I was wondering if there is a similar program that works on ubuntu. :)

---

### Post by -grubby on 2007-10-13
I saw that on my friend's laptop. I don't think there's anything available for Ubuntu but Rav Tux has "animated wallpapers" on E17

---

### Post by vishzilla on 2007-10-13
> **lunamystry said:**
> I saw a friend of mine who is on mswin vista and he had this cool application that allowed him to play videos on the deskop instead of having a wallpaper. so I was wondering if there is a similar program that works on ubuntu. :)

If your wondering what software it is, the player comes with K-Lite Codec Pack

---

### Post by TBOL3 on 2007-10-13
MPlayer could.  Or at least MPlayer:Mac could, I never tried it on Ubuntu.  (Actually I didn't 'try' it in mac, I just pressed a button, and I learned it had that feature).

---

### Post by lunamystry on 2007-10-13
What if i used wine to run the application? 

Where do i get RAV tux?

---

### Post by Steveway on 2007-10-13
You can use Xwinwrap to do this.
You can even use Xwinwrap to show screensavers on your desktop.

---

### Post by lunamystry on 2007-10-13
Where do I get xwinwrap then. This is not for begginers is it? :-\"

---

### Post by happy-and-lost on 2007-10-13
You could probably use something like devilspie to stick mplayer to the root window, but is it really worth all that effort ;)

---

### Post by Steveway on 2007-10-13
Trevino has it in his repos:
[http://3v1n0.tuxfamily.org/dists/feisty/eyecandy/index.html](http://3v1n0.tuxfamily.org/dists/feisty/eyecandy/index.html)
You should be able to find anything else with Google and the man command.

---

### Post by lunamystry on 2007-10-13
Thanks a lot everybody. i've just been disouraged (which means i'll probably try all this again when I dont have exams to study for). :)

---

### Post by milosz.galazka on 2007-10-13
Hi, I used mplayer to view videoclips on desktop. For example *mplayer -x 300 -y 200 -geometry 1:1 -rootwin example_file.avi*

---

### Post by Crashmaxx on 2007-10-13
> **milosz.galazka said:**
> Hi, I used mplayer to view videoclips on desktop. For example *mplayer -x 300 -y 200 -geometry 1:1 -rootwin example_file.avi*

He'll also need to do this so nautilus won't cover it up:
> 
Open gconf-editor, browse to /apps/nautilus/preferences and uncheck "show_desktop" key. This will disable nautilus desktop management.

From here:
[https://help.ubuntu.com/community/ScreensaverAsWallpaper](https://help.ubuntu.com/community/ScreensaverAsWallpaper)

---

### Post by rolando2424 on 2007-10-13
> **Crashmaxx said:**
> He'll also need to do this so nautilus won't cover it up:

From here:
[https://help.ubuntu.com/community/ScreensaverAsWallpaper](https://help.ubuntu.com/community/ScreensaverAsWallpaper)

Or he can type

> 
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false


After he's done messing with the Desktop, type:
> 
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop true && nautilus


---

