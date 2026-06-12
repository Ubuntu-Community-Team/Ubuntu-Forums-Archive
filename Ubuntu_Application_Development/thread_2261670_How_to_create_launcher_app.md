---
title: "How to create launcher app"
date: 2015-01-20
forum: Ubuntu Application Development
---

### Post by stefanschepers48 on 2015-01-20
Hello,

How can I create an application like this:

I have a window with icons, icons like Firefox, Chrome and Rhythmbox. When I click on an icon, like Firefox, an application will launch.
When I click on the Firefox icon, Firefox will launch. Is this easy to create?

An example: [http://4.bp.blogspot.com/-Cv4sVr1YyXs/UJZB6xZG4dI/AAAAAAAABdI/J1Rw8vJiIG0/s1600/capture14572.png](http://4.bp.blogspot.com/-Cv4sVr1YyXs/UJZB6xZG4dI/AAAAAAAABdI/J1Rw8vJiIG0/s1600/capture14572.png)

---

### Post by kerry_s on 2015-01-20
that is rox-filer with apps in it. so you copy apps from /usr/share/applications to a folder then launch that folder.
sudo apt-get install rox-filer
go into preferences disable the toolbar, add your folder of apps, launch it-> rox /path/to/folder

if you want to remake that it would be nice to know what de/wm your using & ubuntu version. then there could be some other way to do it with what you already have installed.

---

### Post by stefanschepers48 on 2015-01-20
I have Xfce installed, with Thunar as file manager. But I like the way it is in Rox, just a window with icons, and not menus and icons at the top of the window. Is that possible with Thunar?

---

### Post by kerry_s on 2015-01-20
i don't recall thunar being able to do that. you can use rox in xfce though, rox does many things from panel to desktop icons.
what xubuntu version?

xfce-panels are top notch. it's funny i had a idea once of using the panel in just that way. because you can pick your rows for the panel and you can move the panel where ever you want. all you would need was a script to start & kill just that panel, but never got around to playing with that idea. only today you made me think about it, do the panels even still allow floating panel?

---

### Post by stefanschepers48 on 2015-01-20
Ok, but how can I do that in rox-filer? Because standard you have menu's in rox-filer, and in the example that I posted, there are no menus. I am using Xubuntu 12.04 LTS.

---

### Post by kerry_s on 2015-01-20
right click in the rox window, go into preferences, look for the section where you can customize whats on the toolbar, there should be something for no tool bar. then just create your folder you want your apps in, use xfce app browser & drag drop apps into rox, right click on your xfce panel, add launcher, in command just put rox /path/to/folder/folder, remember rox is a file manager so what ever you create in rox will show in thunar, i suggest you create 1 folder & add as many folders as you want in there.

i also think rox comes with a manual you can read on line. you can also do "rox --help" in terminal to see the command switches.

---

### Post by kerry_s on 2015-01-20
i got time let me install rox & ill put some pics up you can follow. give me a sec be back.

---

### Post by kerry_s on 2015-01-20
okay pics for you:

you'll also want to read this page.
[http://rox.sourceforge.net/desktop/node/117.html](http://rox.sourceforge.net/desktop/node/117.html)

---

### Post by stefanschepers48 on 2015-01-20
Thank you!

---

### Post by kerry_s on 2015-01-20
> **stefanschepers48 said:**
> Thank you!

your welcome!
you sure it's worth all that just to launch a single app? you know xfce panel has a drawer app where you can stack several launchers.

---

### Post by paddy5 on 2015-01-20
I am thinking about getting it but how well does it work.

[http://thephotographerlocal.com](http://thephotographerlocal.com)

---

### Post by kerry_s on 2015-01-20
> **paddy5 said:**
> I am thinking about getting it but how well does it work.

[http://thephotographerlocal.com](http://thephotographerlocal.com)

ya lost me there? if your talking about the drawer it should already be in your add to panel list.

---

