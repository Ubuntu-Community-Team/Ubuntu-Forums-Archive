---
title: "Custom Backgrounds not working"
date: 2015-11-26
forum: Ubuntu/Debian BASED
---

### Post by Shakermaker on 2015-11-26
Hey guys, I'm trying to change my background to some pictures I found online, and Elementary isn't allowing me. It just shows the background colour. 
See the screenshot below. These pictures are located in /home/pictures/wallpapers/....
I tried dropping them in to /usr/share/backgrounds/.... to see if that would help, but that didn't work.

[Screenshot Link]("http://i.imgur.com/uEOgGHl.png")

Not sure what other information I need to provide for this, if you need to know anything else about my setup, just let me know.

---

### Post by Portaro on 2015-11-27
Hum its strange do you have permission to read the content on /usr/share backgrounds?

And why you need to do this ? the tool of wallpaper config of Elementary dont have option to choose the wall on other paths different from /usr/share/backgrounds?

Very strange  that Elementary have this is a basic option.

---

### Post by Shakermaker on 2015-11-27
Thanks for the reply. Yes I've tried to change the wallpaper as root and it hasn't worked. I am able to change the background to default/elementary backgrounds that are installed with the OS. It just won't let me change it to a custom background. Very strange indeed!

---

### Post by Portaro on 2015-11-27
Well tyr this open your window manager (nautilus ) I think is the name of your , but open it with sudo on a terminal and navigate to inside your /usr/share/backgrounds , when you do this click on one of your walls that you put inside and choose properties and see permissions and change it to access all users.

Ok when you do this, close your terminal.
Open your background manager and choose the wall that you change permissions and see if work or not , if dont work please repeat the process and delete the background or rewirte the permission to the default value.

And if not work maybe the default backgrounds of Elementary can be placed on other location like /usr/share/Elementary/Wallpapers or other try to see where  placed the background.

If you already do this steps I only have one idea , maybe you choose color use on your background manager and always you need is find this option and choose image .

I dont have Elementary but this basic option is not complicated maybe you need find a short option of any manager of Background or Desktop of your Elementary.

---

### Post by williamtl on 2016-07-19
I know this is very old, but I thought I'd post something I discovered. If I sudo move my custom backgrounds into the /usr/share/backgrounds/ folder it does work in freya as of today (on my machine :o).

I'm wondering if this could be a permissions issue of some kind since the desktop wallpaper is also used as the greeter background?

---

