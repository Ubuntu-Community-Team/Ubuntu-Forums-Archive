---
title: "Gnome Classic"
date: 2017-08-16
forum: Ubuntu Development Version
---

### Post by rrnbtter on 2017-08-16
Greetings,
Gnome Classic added to the Login Menu. FYI 
This should make some users happy. Takes me  back to the Lucid/Maverick days.

PS I just noticed upon update that Unity has been added to my wifes login, and it works.

---

### Post by rrnbtter on 2017-08-17
Greetings,
I added the Unity login to my system with "sudo apt install unity-session". It works just a good as usual, meaning when I opened it I immediately got a half dozen apport popups. After trying all six options I would have to say that for myself on my system Ubuntu on Wayland (Gnome Desktop) is the smoothest and fastest experience. I have yet to miss a thing after using Unity for six years.

---

### Post by ventrical on 2017-08-18
A lot of the apps now are functional (ie; vokoscreen) and it's really catching up to unity performance.
Nice and smooth in classic and wayland.

regards..

---

### Post by rrnbtter on 2017-08-18
Greetings,
Without question they are working on all of it. 
FYI, Unity Launcher has been added to the Ubuntu-Wayland-Gnome desktop.  Gnome-Wayland retains the Gnome Launcher. 
Just like most everyone here has been saying Ubuntu Gnome will adapt some Unity features.  
Looks like this will be an enjoyable dev cycle.

---

### Post by mc4man on 2017-08-18
> **rrnbtter said:**
> Greetings,
Without question they are working on all of it. 
FYI, Unity Launcher has been added to the Ubuntu-Wayland-Gnome desktop.  Gnome-Wayland retains the Gnome Launcher. 
Just like most everyone here has been saying Ubuntu Gnome will adapt some Unity features.  
Looks like this will be an enjoyable dev cycle.
Probably sessions, you can add gnome session to Ubunu image to expose all in log in options.

Info-  useful to ck. out from Day 1 to currently Day 5
[https://didrocks.fr/](https://didrocks.fr/)

---

### Post by rrnbtter on 2017-08-18
Greetings,
I earlier posted here that I have yet to miss a thing with Gnome-Wayland however I forgot that Luckybackup super user is non functional.  I have made a bash menu with all of my backups scripted for rsync which now is working with Wayland. Rsync works so well by itself I think I will stay with that and my homemade menu.  Reminds me of the old MSDOS days.

---

### Post by rrnbtter on 2017-08-18
Greetings,
@mc4man, thanks for the link.  In addition it appears that mir hasn't gone anywhere since we are still getting it in the downstream for Unity.  It will be interesting to see what Canonical has going on for Unity.

---

### Post by ventrical on 2017-08-18
> **rrnbtter said:**
> 
Just like most everyone here has been saying Ubuntu Gnome will adapt some Unity features.  
Looks like this will be an enjoyable dev cycle.
  This is real testament to the people who have worked on unity from the start. It's all good faith gestures that makes ubuntu the hottest and sleekest operating system on the planet.

Regards..

---

### Post by ventrical on 2017-08-18
> **rrnbtter said:**
> Greetings,
@mc4man, thanks for the link.  In addition it appears that mir hasn't gone anywhere since we are still getting it in the downstream for Unity.  It will be interesting to see what Canonical has going on for Unity.

Seen that from the beginning. One about thing this cycle is for sure and that is that it is certainly not boring :) and it keeps us guessing.

Regards..

---

### Post by Chanath on 2017-08-18
> **rrnbtter said:**
> Greetings,
Gnome Classic added to the Login Menu. FYI 
This should make some users happy. Takes me  back to the Lucid/Maverick days.

Do you have a menu like Gnomenu in Gnome Classic? If so, how did you install it?

---

### Post by Chanath on 2017-08-19
Installed Ubuntu 17.10 daily to find out how it would work with Gnome Classic. Ubuntu had Ubuntu dock extension installed by default, which cannot be configured or uninstalled (yet). Installed gnome classic, deleted the bottom panel, brought the top panel down, added window list etc to it. Looked quite all right for a while, but after rebooting and login to Gnome Classic, everything was messed up. Ubuntu dock was there, a new top panel had come that cannot be deleted, and Gnome panel was also there, a nice mess.


I went back to my 17.10 Unity without Gnome shell install and installed Gnome Classic there, deleted the bottom panel, brought the top panel down, added window list etc to it. Worked with it for a while, and rebooted. Everything is nice like the olden days. Looks like, if you want to use Gnome Classic, you have to uninstall Gnome-shell. 

Maybe someone would make a menu like Gnomenu to it, and it'd be simply perfect.:)

---

### Post by rrnbtter on 2017-08-19
Greetings,
I never used gnomenu. I switched to Unity desktop when it was presented with the Natty dev cycle.  I think that gnomenu is a Gnome Shell extension. If you install the extensions you should be able to get the menu. Or not!  Its all a toss up right now.

---

### Post by kurt18947 on 2017-08-19
I've been using Ubuntu Gnome for some years now. I haven't missed the classic menu but there are shell extensions that should add menus. A lot of extensions don't work with developmental gnome versions without version editing and perhaps more.

---

### Post by Chanath on 2017-08-19
> **rrnbtter said:**
> Greetings,
I never used gnomenu. I switched to Unity desktop when it was presented with the Natty dev cycle.  I think that gnomenu is a Gnome Shell extension. If you install the extensions you should be able to get the menu. Or not!  Its all a toss up right now.

Greetings!

Quite some time ago in Natty days, there was a searchable menu called Gnomenu, which was used as an applet for Gnome panel. Later this was used in Zorin as Zorin Menu on AWN dock. There is a Gnomenu extension in Gnome shell, which might be forked from the former Gnomenu. It won't work with Gnome Classic. I was thinking how to use the Natty days Gnomenu in 17.10 Gnome Classic. There are some dependencies missing. Maybe, someone with coding abilities might look and make it working for Gnome Classic as its now available in Ubuntu. 

This Gnome Classic works quite well with Unity (dual DE), but quite a mess up with Gnome shell. I'm keeping both installs to see the difference. I'm awaiting the next development cycle with 18.04 to see how far Unity would work, and now--thanks to your post--also how Gnome Classic would work. Its nice to be back in former Ubuntu days. :)

---

### Post by Chanath on 2017-08-19
Went back to the Natty days and installed Slingshot of those days in 17.10. Not the Slingscold (nothing to do with hot and cold). Slingshot as a launcher of things. Had to play a bit with old and forgotten dependencies. The executive and the dependencies can be kept anywhere. The screeny is below. It is a full screen menu, but a nicer one.

---

### Post by Chanath on 2017-08-20
In this 17.10 install, got rid of gnome-shell, unity, but kept unity greeter. Now I have only Gnome Classic with Compiz and Metacity. If this (promised ?) Gnome Classic would stay on in 18.04 and further, it'd be quite a competitor to Mate.

---

### Post by muktupavels on 2017-08-20
It is **not** a GNOME Classic... Compiz & Metacity sessions are GNOME Flashback. GNOME Classic is GNOME Shell with extensions. :)

---

### Post by Chanath on 2017-08-21
> **muktupavels said:**
> It is **not** a GNOME Classic... Compiz & Metacity sessions are GNOME Flashback. GNOME Classic is GNOME Shell with extensions. :)

Okay, but as it takes us back to pre-Natty days, we might just call it Gnome Classic.  :)
Have a nice day!

---

### Post by kansasnoob on 2017-08-21
> **muktupavels said:**
> It is **not** a GNOME Classic... Compiz & Metacity sessions are GNOME Flashback. GNOME Classic is GNOME Shell with extensions. :)

+1!

It's important that we differentiate between the two. I need to get a hard drive swapped before I can test 17.10 - something I can't do by myself because a surgery and a stroke left me with only one poorly working hand - but I'm anxious to see how the flashback session (with Metacity) has progressed. It was great in 16.04 but underlying OS stability issues caused me to stick with 14.04 and wait to see how well 18.04 works with my largely prehistoric hardware.

---

### Post by amano on 2017-08-22
I don't even know what this thread is about. Some mysterious hidden session from the natty days? Featuring the gnome2 gnomepanel?

---

### Post by kansasnoob on 2017-08-22
> **amano said:**
> I don't even know what this thread is about. Some mysterious hidden session from the natty days? Featuring the gnome2 gnomepanel?

This Trusty thread has some links to the history of the "Flashback" session(s):

[https://ubuntuforums.org/showthread.php?t=2220264](https://ubuntuforums.org/showthread.php?t=2220264)

It actually began with Oneiric in Ubuntu while it was supported by GNOME, and was named "Classic", but later on GNOME began using the name "classic" to describe a GNOME Shell session with panels that can't be changed as easily as gnome-panel. Flashback truly does still use 'gnome-panel' but it's been changed (I'd say improved) since GNOME jumped from version 2 to version 3.

---

### Post by amano on 2017-08-22
But neither is installed by default now? I just know about the gnome-flashback-session package in Universe. What package does install the different “Gnome Classic“ session that you mention?

---

### Post by jbicha on 2017-08-23
> **amano said:**
> But neither is installed by default now? I just know about the gnome-flashback-session package in Universe. What package does install the different “Gnome Classic“ session that you mention?

gnome-shell-extensions

But it might make sense to split the GNOME Classic session into a separate package with a more obvious name!

---

