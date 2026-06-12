---
title: "minimize, restore, close in both corners ..... ugh"
date: 2016-05-12
forum: Ubuntu, Linux and OS Chat
---

### Post by fugu2 on 2016-05-12
Just need to vent. Has anyone else noticed that about 1/2 the apps have the minimize, restore, and close in the left hand corner of the window, while the other 1/2 have them in the right hand corner? When I need to close a bunch of open windows, I'm going back and forth between both side of the screen just to close all the windows. I'm finding a lot of "features" with 16.04 are very inefficient. Not that its hard to close, but not as fast or as easy as it used to be.

---

### Post by vasa1 on 2016-05-12
I've stopped bothering about where these buttons are located. I've even removed them from the title bar. I just use Alt+Space, C to close windows. That's pretty universal.

---

### Post by fugu2 on 2016-05-12
Does anyone know if its possible to tell gnome to set them all to one side of the screen?

---

### Post by mc4man on 2016-05-12
Here all buttons on all apps are only on the left & have been for several years.

---

### Post by user1397 on 2016-05-12
same as mc4man, not sure what OP is talking about

---

### Post by fugu2 on 2016-05-13
In firefox and gnome-terminal the minimize,restore,close buttons are on the right. In gedit and nautilus they are on the left. These are apps that I use quite a bit too.

---

### Post by coffeecat on 2016-05-13
> **fugu2 said:**
> In firefox and gnome-terminal the minimize,restore,close buttons are on the right. 

Not in Ubuntu 16.04, they are not. What exactly are you talking about? Which desktop? Which flavour?

---

### Post by fugu2 on 2016-05-13
This is my computer: ```

$ uname -a
Linux username-computer 4.4.0-22-generic #39-Ubuntu SMP Thu May 5 16:53:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial

```

[ATTACH=CONFIG]269027[/ATTACH]

[ATTACH=CONFIG]269028[/ATTACH]

---

### Post by grahammechanical on 2016-05-13
The only application I have seen with buttons on the right is Chrome. I just now noticed that if I use a Firefox menu to go full screen the buttons move to the right. This does not happen if I use the maximize button.

Unity.

Regards.

---

### Post by goofprog on 2016-05-13
I just assume it is unity.  I actually installed gnome and all the buttons are on the upper right corner of their window.

---

### Post by vasa1 on 2016-05-13
@fugu2, please post the output of```
ls /usr/share/xsessions
```

---

### Post by fugu2 on 2016-05-13
Yes, I did install gnome-core, because I'm not a fan of Unity, but I would *think* all the windows should be handled by a window manager, which should be what dictates all the windows features in a uniform way, including the close button. I feel that Unity is more condusive to a smart phone or tablet, and the traditional gnome environment works better in a desktop computer. 
```
 
$ ls -1 /usr/share/xsessions
gnome-classic.desktop
gnome.desktop
  ubuntu.desktop
  
```

---

### Post by vasa1 on 2016-05-13
> **fugu2 said:**
> Yes, I did install gnome-core, because I'm not a fan of Unity, but I would *think* all the windows should be handled by a window manager, which should be what dictates all the windows features in a uniform way, including the close button. I feel that Unity is more condusive to a smart phone or tablet, and the traditional gnome environment works better in a desktop computer. 
```
 
$ ls -1 /usr/share/xsessions
gnome-classic.desktop
gnome.desktop
  ubuntu.desktop
  
```
If you're not a fan of something, there's no real need to install it. Install the flavor you like. Or start off with a minimal install and install exactly what you want. 

Several users are of the opinion that having multiple desktop environments can cause unpredictable situations. In any case, developers of a particular flavor have enough on their plates and I'm not sure they take into account the possibility that other desktop environments may be present on the same system.

---

### Post by deadflowr on 2016-05-14
If I get the gist of this, maximized open windows have the button-layout on the right side, but non-maximized open windows  are on the left.
I think that's a deficiency of gnome-panel not understanding unity's maximized window design. 
Where as unity's max window state in integrated into the panel. Gnome flashback does not do that and so it cannot understand it and reverts to it's hard coded design of placing them in the right side.
I think the solution is simple, you need to forgo unity's button-layout altogether and put 'em all in the right side.
Kansasnoob has a thread on xenial, and moving the button-layout is describe in the first post:
[http://ubuntuforums.org/showthread.php?t=2302432]("http://ubuntuforums.org/showthread.php?t=2302432")

That's my rambling two cents.
Right or wrong

---

### Post by fugu2 on 2016-05-14
> **deadflowr said:**
> Kansasnoob has a thread on xenial, and moving the button-layout is describe in the first post: [http://ubuntuforums.org/showthread.php?t=2302432](http://ubuntuforums.org/showthread.php?t=2302432)   Thank you, I will definitely take a look at this.

---

### Post by user1397 on 2016-05-16
Definitely sounds like this was caused by installing some gnome components.  I'm using default ubuntu unity 16.04 here and buttons are always on the left (except for google chrome)

---

