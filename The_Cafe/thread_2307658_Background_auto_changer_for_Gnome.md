---
title: "Background auto changer for Gnome"
date: 2015-12-27
forum: The Cafe
---

### Post by marouane87 on 2015-12-27
Hello,

The automatic periodic background changing is popular by now. It is introduced in Windows and Linux Mint (I don't know about KDE). So I was wondering why Gnome community didn't think of integrating it yet, and still relying on third applications for this feature. 
Since it is already implemented in Cinnamon, I think it would be "easy" (I know this is a very relative description) to fork it and implement it for Gnome.

Has there been any feedback about this kind of features from gnome developers in the past?

Thank you :)

---

### Post by grahammechanical on 2015-12-27
I am not sure what you are talking about but I have been using Ubuntu + Unity for several years and as we know, Ubuntu is built on Gnome 3 DE and I am able to set the background wallpaper to cycle through all the default available wallpapers in a periodic manner. And I have been able to do this for several years now.

There are 10 default wallpapers and they cycle through every 1,795 seconds. This feature is also present in Ubuntu Gnome which uses Gnome 3 shell instead of Unity.

Are we talking about the same thing?

Regards

---

### Post by marouane87 on 2015-12-27
I think it is called Bakcground wallpaper SlideShow, and as far as I looked, it can only be done by thrid party software like "variety" and [others]("https://help.ubuntu.com/community/Photos/Slideshows")

After a little digging, Cinnamon is using a built in module: [http://segfault.linuxmint.com/2014/09/cinnamon-2-4-background-slideshows/](http://segfault.linuxmint.com/2014/09/cinnamon-2-4-background-slideshows/)

---

### Post by Dragonbite on 2015-12-27
Gnome and Unity do not have one built in, which has irked me so much.

In Gnome there ws "slideshow" extension but it looks to not be rated to work in the newer versions of Gnome and I have had hit-or-miss with using it.  For example, I could not open the windows to set which wallpapers to cycle through until I tried to run it via the gnome extension web browser.

Unity does not include one, but there is an application called **Wallch** which allows you to rotate between backgrounds from local folders or other places.  I have had it run on start up but not be "started" (not cylcing through the pictures) but otherwise when it works it works.

Xfce and KDE include wallpaper changing built-in.  On my 2 devices I have Xfce on one rotating between one of my folder's contents, and another running Unity and Wallch. 

Like I've said.. it is irksome.

I have been tempted to go through the code for backslide and see if I could fork it into something that works and is very simple, it has irked me so much.

Even Windows 7 & 10 have background changing built in (just sayin'...)

---

### Post by marouane87 on 2015-12-28
Yes, I wanted to see through code also, but for Cinnamon it is written in python, which is "beyond my powers".
I've also found this package: [https://launchpad.net/gnome3-background-slideshow](https://launchpad.net/gnome3-background-slideshow) and I don't know why it was discontinued and if it ever seen the light really.

---

### Post by Dragonbite on 2015-12-28
I get annoyed from the background changers making things so complicated.  I just want something to cycle through my locally stored pictures and don't care about the whiz-bang "pic of the day" or "daily NASA pics" or funky things like that.

A basic one should be included in the environment and then if you want something fancier you install one of these other applications.

---

