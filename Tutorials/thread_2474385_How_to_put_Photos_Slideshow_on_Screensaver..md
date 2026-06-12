---
title: "How to put Photos Slideshow on Screensaver."
date: 2022-04-27
forum: Tutorials
---

### Post by kagashe on 2022-04-27
One of my close friend likes to see Photos Slideshow on Screensaver and therefore uses old versions of Ubuntu. I have big collection of photos on my Laptop and thought why not try it on the brand new Ubuntu Jammy Jellyfish and also my current os Ubuntu 20.04. Ok here it goes:
```
$ sudo apt install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra

$ sudo apt remove gnome-screensaver
```

Add xscreensaver to Startup Applications by putting xscreensaver -nosplash in the command
[IMG]https://kagashe.blogspot.com/2022/04/photo-slideshow-on-screensaver-on-ubuntu.html[/IMG]

Open Screensaver Preferences choose only one screensaver on Mode and tick on GLSlidesshow
[IMG]https://kagashe.blogspot.com/2022/04/photo-slideshow-on-screensaver-on-ubuntu.html[/IMG]

On Advanced Tab tick on Grab Desktop images, Choose Random Image, click on Browse button and select the Folder containing the photos
[IMG]https://kagashe.blogspot.com/2022/04/photo-slideshow-on-screensaver-on-ubuntu.html[/IMG]

and it works on reboot.

---

### Post by ajgreeny on 2022-04-28
Yes, it still works very well in spite of being a gtk2 application.

I use it, and have done so for many years, with all the thousands of photos from holidays showing completely randomly for about 20s each, and also very slowly panning and zooming just to add interest.
I have looked for more up to date screensavers, perhaps using gtk3, but have not yet found anything quite so configurable as xscreensaver.

---

### Post by yetimon_64 on 2022-04-29
> **ajgreeny said:**
> Yes, it still works very well in spite of being a gtk2 application...
For those on Xubuntu 22.04 there is xfce4-screensaver installed already with the screenshow screensaver available by default, not sure if it is gtk2 or gtk3 though. **Edit**: just found it depends on libgtk-3-0 so it seems to be gtk3.

There were only about 5 or 6 shows installed initially so I tried kagashe's command omitting the xscreensaver package, just the gl and data packs and they work well. See screenshot attached, the picture is in my home folder; the settings can be adjusted for accessing any folder.

---

### Post by ajgreeny on 2022-04-29
I'm aware that the xfce4-screensaver can use sideshows but it will not have all the interesting extras that xscreensaver does such as the panning and zooming of the images, or i couldn't find them so for now will stick with xscreensaver.

---

### Post by yetimon_64 on 2022-04-29
> **ajgreeny said:**
> I'm aware that the xfce4-screensaver can use sideshows but it will not have all the interesting extras that xscreensaver does such as the panning and zooming of the images, or i couldn't find them so for now will stick with xscreensaver.
Ah, I understand now. Just double checked here, you are right about that. Those settings aren't available on xfce4-screensaver.
Regards, yeti.

---

### Post by kagashe on 2022-04-29
> **yetimon_64 said:**
> For those on Xubuntu 22.04 there is xfce4-screensaver installed already with the screenshow screensaver available by default, not sure if it is gtk2 or gtk3 though. **Edit**: just found it depends on libgtk-3-0 so it seems to be gtk3.

There were only about 5 or 6 shows installed initially so I tried kagashe's command omitting the xscreensaver package, just the gl and data packs and they work well. See screenshot attached, the picture is in my home folder; the settings can be adjusted for accessing any folder.

I know it is available on Xfce Desktop since I have Manjaro Xfce on one partition.

My post is for Ubuntu users who are missing the Slideshow on Screensaver since Ubuntu adopted gnome desktop and regards to my friend who told me that he uses old Ubuntu version just for this feature and I told him I could do this on Ubuntu Jammy Jellyfish by removing gnome-screensaver and installing xscreensaver through the above commands.

Kamalakar

---

