---
title: "Some issues that I'm not sure how to fix?!"
date: 2012-09-22
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by amjjawad on 2012-09-22
First of all, hello everyone :) it's been ages.

Second of all, I'm having some issues with Lubuntu 12.10 but _*from my not short experience with Lubuntu, these issues don't seem NEW at all (I have experienced some of them with the previous releases).*_ However, still no real fix, at least at my knowledge as of today.

My story is on:
Asus F3F Laptop, Intel Core Duo T2350 @1.86GHz, 512MB RAM, Graphics is Intel 945GM/GMS and it's Lubuntu 12.10 Beta1 32-bit.


_**Details:**_

**1- [https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/970758](https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/970758)**

Simply, it is still happening.
Usually, if you, for example:

Menu > System Tools > Task Manager

Once you click on "Task Manager", the application will start and the menu will disappear. Prefect so far.

BUT ...

Menu > System Tools > Task Manager > Right Click on Task Manager

Will produce the bug I posted above. The menu will NOT disappear UNLESS you go back and click on the menu icon. Clicking on the Desktop is USELESS.
Before, I thought "Add to Desktop" is the reason but I just found out that the trigger is actually the right click on any entry on any sub-menu.
By the way, Cairo-Dock and Compiz both have absolutely nothing to do with that bug. I have tested it before installing both applications and it is still happening :)

HOW to fix that?


**2- [http://i48.tinypic.com/w8nor9.jpg](http://i48.tinypic.com/w8nor9.jpg)**

This one is a bit tricky so I hope I will explain it as easy as possible.

The main reason WHY I don't use Cairo-Dock on Lubuntu is the _**black box**_ that appears on the background as you can see on the above screenshot.
It doesn't matter whether I run Cairo-Dock (no OpenGL) or GLX-Dock (Cairo-Dock with OpenGL), I get exactly the same black box on both cases.

Every time I start my machine and login to Lubuntu 12.10, I see that Box.
I had this issue before with the previous releases of Lubuntu. However, I found out this time how to temporary fix it, or maybe I should use a more realistic word that fix it, I managed to get rid of that box and this will be explained in the next point.

**3- [http://i48.tinypic.com/w8nor9.jpg](http://i48.tinypic.com/w8nor9.jpg)**

I have installed: compiz, compizconfig-setting-manager, compiz-plugins, fusion-icon.
Everytime I login to the desktop, there is NO border for any window for any application I run. I found out that I can, yet again, temporary fix or get the border back by:
[http://i47.tinypic.com/2ynl3zc.jpg](http://i47.tinypic.com/2ynl3zc.jpg)

Reload Window Manager did the trick but everytime I login to the desktop, I have the same issue and I need to repeat that process over and over again.

[COLOR=Red]NOT SURE if this has any relation with Cairo Dock (with AND without OpenGL - as explained before in #2)[/COLOR] but everytime I do **Reload Window Manger**, the black box disappears. 

----------------
**AND**
----------------
[COLOR=Navy]I forgot to mention that I can NOT use my Keyboard at all. I can't type anything. Reload will fix this but again, I have to re-do the Reload everytime I face this issue[/COLOR] :/

So, it is NOT only the border of any window but the keyboard as well.
YES, my keyboard is fine because right after I Reload the Window Manager, it works perfectly.

My Questions here:
Why it is happening?
How to fix this? so that everytime I login to my Lubuntu 12.10 desktop, I don't need to Reload anything.

By the way, I have followed this: [https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager)
and I replaced OpenBox with Compiz as in this:
[https://help.ubuntu.com/community/CompositeManager#Lubuntu_11.04.2C_11.10_and_12.04](https://help.ubuntu.com/community/CompositeManager#Lubuntu_11.04.2C_11.10_and_12.04)


**4- [http://i46.tinypic.com/345fybs.jpg](http://i46.tinypic.com/345fybs.jpg)**

I'm aware that 12.10 will be shipped with GRUB version 2 but I'm still using GRUB 1.99 as shown in the above screenshot.

I was very surprised after I did the installation and updated GRUB from the main system that I have on that machine which is Lubuntu 12.04.

Why there are 3 entries instead of 2?
If I'm not mistaken:

[COLOR=#222222][FONT=arial][COLOR=#ff0000]Ubuntu' --class ubuntu  --class gun-linux  --class gnu  --class os  ....etc
[/COLOR][/FONT][/COLOR][COLOR=#222222][FONT=arial][COLOR=#ff0000]
Ubuntu, with Linux 3.5.0-15-generic' --class ubuntu --class gnu-linux  --class gnu --class os ....etc
[/COLOR][/FONT][/COLOR][COLOR=#222222][FONT=arial]
Ubuntu, with Linux 3.5.0-15-generic (recovery mode )'  --class ubuntu --class gnu-linux  --class gnu --class os ....etc 
[/FONT][/COLOR]When I choose the first two in red, _**I guess**_ I get the same result. But again, why there are two? are they different or the same? 


- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 

That is all for now.

Thanks a lot :)

---

### Post by dino99 on 2012-09-22
i'm also using Lubuntu quantal i386 but i've never seen that issue (1).Is it a clean install ?

---

### Post by funicorn on 2012-09-22
I opened system tools and couldn't find task manager, is this a bug ?

---

### Post by dino99 on 2012-09-22
> **funicorn said:**
> I opened system tools and couldn't find task manager, is this a bug ?

surely not, but a troll.

---

### Post by amjjawad on 2012-09-22
> **dino99 said:**
> i'm also using Lubuntu quantal i386 but i've never seen that issue.Is it a clean install ?

There are 4 issues so which one you are talking about? :)

Yes indeed, it is a clean install.

---

### Post by amjjawad on 2012-09-22
> **amjjawad said:**
> 
**2- [http://i48.tinypic.com/w8nor9.jpg](http://i48.tinypic.com/w8nor9.jpg)**

This one is a bit tricky so I hope I will explain it as easy as possible.

The main reason WHY I don't use Cairo-Dock on Lubuntu is the _**black box**_ that appears on the background as you can see on the above screenshot.
It doesn't matter whether I run Cairo-Dock (no OpenGL) or GLX-Dock (Cairo-Dock with OpenGL), I get exactly the same black box on both cases.

Every time I start my machine and login to Lubuntu 12.10, I see that Box.
I had this issue before with the previous releases of Lubuntu. However, I found out this time how to temporary fix it, or maybe I should use a more realistic word that fix it, I managed to get rid of that box and this will be explained in the next point.

**Update/Some Progress ...**

Right Click on Cairo-Dock > Configure > Advanced Mode > Behavior > System > Composition > Check "Emulate composition with fake transparency" > Apply.

Will actually remove the Black Box BUT ... ONLY ... if I run Cairo-Dock without OpenGL (***Cairo-Dock no OpenGL***).
Without OpenGL, as far as I have seen, the Dock will lose the effects.

I have tried it with GLX-Dock (Cairo-Dock with OpenGL) and ... still there is a box except it is light black or let's say dark gray or to be more accurate, Transparent Black box.

Too bad :(
But at least there is some progress :)

[http://i49.tinypic.com/a3jabr.jpg](http://i49.tinypic.com/a3jabr.jpg)

---

### Post by GeorgeVita on 2012-09-28
edit: read next post

---

### Post by amjjawad on 2012-09-30
It's been a week or more and there is no progress here!!!

I have reported the thread asking whether it's better to close it and start new 4 threads for each issue? or just split the 4 issues into 4 thread by admins? but there is no reply as of now.
Also, there is no one else posting so please advise!

Thanks!

---

### Post by kansasnoob on 2012-09-30
I highly recommend starting separate threads regarding each issue ;)

Regarding grub I'd started this a while back:

[http://ubuntuforums.org/showthread.php?t=2059108](http://ubuntuforums.org/showthread.php?t=2059108)

I've been using an incredibly sloppy hack on my mega-multi-boot box just to get by ATM. My abilities are just too limited to fight every battle so I'm just "working around" the grub issue out of pure selfishness :redface:

---

### Post by amjjawad on 2012-09-30
> **kansasnoob said:**
> I highly recommend starting separate threads regarding each issue ;)

Regarding grub I'd started this a while back:

[http://ubuntuforums.org/showthread.php?t=2059108](http://ubuntuforums.org/showthread.php?t=2059108)

I've been using an incredibly sloppy hack on my mega-multi-boot box just to get by ATM. My abilities are just too limited to fight every battle so I'm just "working around" the grub issue out of pure selfishness :redface:

I will definitely take that advice/suggestion into consideration :D thanks a lot, my friend :)

I don't have a problem with GRUB, it's a question more than a problem :)
As long as everything works, then there is nothing wrong or serious.
I will have a look at your thread ;)

---

### Post by MG&amp;TL on 2012-09-30
> First of all, hello everyone :) it's been ages.

It has indeed. Welcome back!


> **2- [http://i48.tinypic.com/w8nor9.jpg](http://i48.tinypic.com/w8nor9.jpg)**

This one is a bit tricky so I hope I will explain it as easy as possible.

The main reason WHY I don't use Cairo-Dock on Lubuntu is the _**black box**_ that appears on the background as you can see on the above screenshot.
It doesn't matter whether I run Cairo-Dock (no OpenGL) or GLX-Dock (Cairo-Dock with OpenGL), I get exactly the same black box on both cases.

My understanding is that openbox is not a compositing (i.e. things like transparency) window manager, thus things like cairo-dock don't work so well.

> **3- [http://i48.tinypic.com/w8nor9.jpg](http://i48.tinypic.com/w8nor9.jpg)**

I have installed: compiz, compizconfig-setting-manager, compiz-plugins, fusion-icon.
Everytime I login to the desktop, there is NO border for any window for any application I run. I found out that I can, yet again, temporary fix or get the border back by:
[http://i47.tinypic.com/2ynl3zc.jpg](http://i47.tinypic.com/2ynl3zc.jpg)

gtk-window-decorator is (I think) what compiz uses to draw window decorations by default. I think you my need to install the *compiz-gnome* package for it to be able to do that.

> [COLOR=Red]NOT SURE if this has any relation with Cairo Dock (with AND without OpenGL - as explained before in #2)[/COLOR] but everytime I do **Reload Window Manger**, the black box disappears. 

That's because compiz **is** a compositing window manager, and hence cairo-dock works fine.


> [COLOR=Navy]I forgot to mention that I can NOT use my Keyboard at all. I can't type anything. Reload will fix this but again, I have to re-do the Reload everytime I face this issue[/COLOR] :/

So, it is NOT only the border of any window but the keyboard as well.
YES, my keyboard is fine because right after I Reload the Window Manager, it works perfectly.

If the WM dies, then applications can't gain focus in the normal way, and as such your keyboard may appear to not work.

I hope I've shed some light on your problems, although how I have no clue how to fix it. :)

---

### Post by amjjawad on 2012-10-02
> **amjjawad said:**
> 
**1- [https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/970758](https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/970758)**

Simply, it is still happening.
Usually, if you, for example:

Menu > System Tools > Task Manager

Once you click on "Task Manager", the application will start and the menu will disappear. Prefect so far.

BUT ...

Menu > System Tools > Task Manager > Right Click on Task Manager

Will produce the bug I posted above. The menu will NOT disappear UNLESS you go back and click on the menu icon. Clicking on the Desktop is USELESS.
Before, I thought "Add to Desktop" is the reason but I just found out that the trigger is actually the right click on any entry on any sub-menu.
By the way, Cairo-Dock and Compiz both have absolutely nothing to do with that bug. I have tested it before installing both applications and it is still happening :)

HOW to fix that?

FOR THIS ISSUE, PLEASE SEE: [http://ubuntuforums.org/showthread.php?t=2065519](http://ubuntuforums.org/showthread.php?t=2065519)


> **amjjawad said:**
> 
**4- [http://i46.tinypic.com/345fybs.jpg](http://i46.tinypic.com/345fybs.jpg)**

I'm aware that 12.10 will be shipped with GRUB version 2 but I'm still using GRUB 1.99 as shown in the above screenshot.

I was very surprised after I did the installation and updated GRUB from the main system that I have on that machine which is Lubuntu 12.04.

Why there are 3 entries instead of 2?
If I'm not mistaken:

[COLOR=#222222][FONT=arial][COLOR=#ff0000]Ubuntu' --class ubuntu  --class gun-linux  --class gnu  --class os  ....etc
[/COLOR][/FONT][/COLOR][COLOR=#222222][FONT=arial][COLOR=#ff0000]
Ubuntu, with Linux 3.5.0-15-generic' --class ubuntu --class gnu-linux  --class gnu --class os ....etc
[/COLOR][/FONT][/COLOR][COLOR=#222222][FONT=arial]
Ubuntu, with Linux 3.5.0-15-generic (recovery mode )'  --class ubuntu --class gnu-linux  --class gnu --class os ....etc 
[/FONT][/COLOR]When I choose the first two in red, _**I guess**_ I get the same result. But again, why there are two? are they different or the same? 


FOR THIS ISSUE, PLEASE SEE THIS: [http://ubuntuforums.org/showthread.php?t=2065520](http://ubuntuforums.org/showthread.php?t=2065520)

---

### Post by amjjawad on 2012-10-02
> **amjjawad said:**
> 
**2- [http://i48.tinypic.com/w8nor9.jpg](http://i48.tinypic.com/w8nor9.jpg)**

This one is a bit tricky so I hope I will explain it as easy as possible.

The main reason WHY I don't use Cairo-Dock on Lubuntu is the _**black box**_ that appears on the background as you can see on the above screenshot.
It doesn't matter whether I run Cairo-Dock (no OpenGL) or GLX-Dock (Cairo-Dock with OpenGL), I get exactly the same black box on both cases.

Every time I start my machine and login to Lubuntu 12.10, I see that Box.
I had this issue before with the previous releases of Lubuntu. However, I found out this time how to temporary fix it, or maybe I should use a more realistic word that fix it, I managed to get rid of that box and this will be explained in the next point.

**3- [http://i48.tinypic.com/w8nor9.jpg](http://i48.tinypic.com/w8nor9.jpg)**

I have installed: compiz, compizconfig-setting-manager, compiz-plugins, fusion-icon.
Everytime I login to the desktop, there is NO border for any window for any application I run. I found out that I can, yet again, temporary fix or get the border back by:
[http://i47.tinypic.com/2ynl3zc.jpg](http://i47.tinypic.com/2ynl3zc.jpg)

Reload Window Manager did the trick but everytime I login to the desktop, I have the same issue and I need to repeat that process over and over again.

[COLOR=Red]NOT SURE if this has any relation with Cairo Dock (with AND without OpenGL - as explained before in #2)[/COLOR] but everytime I do **Reload Window Manger**, the black box disappears. 

----------------
**AND**
----------------
[COLOR=Navy]I forgot to mention that I can NOT use my Keyboard at all. I can't type anything. Reload will fix this but again, I have to re-do the Reload everytime I face this issue[/COLOR] :/

So, it is NOT only the border of any window but the keyboard as well.
YES, my keyboard is fine because right after I Reload the Window Manager, it works perfectly.

My Questions here:
Why it is happening?
How to fix this? so that everytime I login to my Lubuntu 12.10 desktop, I don't need to Reload anything.

By the way, I have followed this: [https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager)
and I replaced OpenBox with Compiz as in this:
[https://help.ubuntu.com/community/CompositeManager#Lubuntu_11.04.2C_11.10_and_12.04](https://help.ubuntu.com/community/CompositeManager#Lubuntu_11.04.2C_11.10_and_12.04)




Last night, I ran:
```
sudo apt-get upgrade && sudo apt-get dist-upgrade 
```
and apparently, the two issues explained above are no longer exist but I need to keep testing the system and check if it's 100% solved or what? will keep you posted :)

Thanks!

---

### Post by amjjawad on 2012-10-03
[http://i50.tinypic.com/2zf019j.jpg](http://i50.tinypic.com/2zf019j.jpg)

I thought it is fixed but NOT yet :(
I still have to click on "Reload Window Manager" right after I login to the Desktop so that the black box disappear and I get the window's border back.

---

### Post by MG&amp;TL on 2012-10-03
> **amjjawad said:**
> [http://i50.tinypic.com/2zf019j.jpg](http://i50.tinypic.com/2zf019j.jpg)

I thought it is fixed but NOT yet :(
I still have to click on "Reload Window Manager" right after I login to the Desktop so that the black box disappear and I get the window's border back.

I have no idea. I'm thinking that cairo-dock might be loading while openbox is still loaded and compiz hasn't replaced it yet. I don't know how you'd fix that, try putting "sleep 2;" in front of the cairo-dock command (where you put that).

---

### Post by amjjawad on 2012-10-03
> **MG&TL said:**
> I have no idea. I'm thinking that cairo-dock might be loading while openbox is still loaded and compiz hasn't replaced it yet. I don't know how you'd fix that, try putting "sleep 2;" in front of the cairo-dock command (where you put that).

[http://i46.tinypic.com/2croapg.jpg](http://i46.tinypic.com/2croapg.jpg)

I have already replaced Openbox with Compiz as per the Wiki Page I have mentioned before.

I have reported this: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1061282](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1061282)

I don't have any better idea as of now :(

---

### Post by MG&amp;TL on 2012-10-04
> **amjjawad said:**
> [http://i46.tinypic.com/2croapg.jpg](http://i46.tinypic.com/2croapg.jpg)

I have already replaced Openbox with Compiz as per the Wiki Page I have mentioned before.


My apologies. The wiki page I read basically said 'replace openbox with compiz as soon as the session loads', which is what I ended up doing.

Anyways, sorry I couldn't help more.

---

### Post by amjjawad on 2012-10-12
Well, so far so good. I was fine, after some updates, it back to misbehave and now, it's ok. Will keep watching.

---

