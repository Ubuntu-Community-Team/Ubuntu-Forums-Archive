---
title: "What Unity Needs: Simple Configuration!"
date: 2011-04-30
forum: Testimonials &amp; Experiences
---

### Post by tristan on 2011-04-30
No doubt about it, Unity is one of the most polarising things the Ubuntu team have done in many years. There seem to be 3 camps out there at present:

1 - Hate Unity unreservedly and will either use classic gnome or defect to another DE or distro altogether.
2 - Love Unity unreservedly and can't understand what all the hate is about.
3 - Think Unity is a good and interesting start, but needs work to reach its full potential.

I'm firmly in category 3. I've clean installed Natty on a netbook and 2 desktops and it looks pretty nice and generally works well, if a little differently to what I'm used to, on all of them.

To my mind, what Unity has going against it at this stage is mainly down to two things:

1 - The "shock of the new". This is to be expected, and has been part of new OS releases since the first abacus. I adapted to it pretty quickly but don't necessarily think it's a revolutionary new and better way to use the same hardware, just a different and visually interesting way.

2 - **Almost complete lack of configurability.** OK, so I'm finally at the point of my post. Releasing an interface touted for its ease of use to attract linux newcomers, and then burying most of the (limited) configurability in arcane gconf/dconf and compiz configuration settings strikes me as a terrible own goal. Even linux newcomers want to take ownership of their computer interface, and denying or burying this essential functionality seems to be one of the root causes of so much negativity about Unity. Basically it smacks of arrogance - we know better than you how you'd prefer your computing experience.

In my opinion what Canonical need to do sooner rather than later is release a **Unity Configuration Tool**, integrated into the system settings or even the launcher itself, offering a simple way to change the settings that seem to irk every second unity user on these forums:

1 - Size of icons in launcher. (they are simply too big by default)
2 - Position of launcher (right/left/top/bottom)
3 - Position of panel (top/bottom)
4 - Size of the text and icons in the dash (on a big screen they are simply enormous and overwhelming)
5 - Ability to move and order the icons in the launcher
6 - Autohiding settings for launcher/panel
7 - Click on a running app's icon to minimise it
7 - Etc etc. None of these things change the essential Unity concepts, just help make the user more comfortable in front of their own computer. 

Perhaps if they'd had another few months to make this kind of tool the backlash might have been less severe. Here's hoping such a tool makes it into 11.10. I predict a bit of an exodus away from Unity or Ubuntu if not...

---

### Post by 3rdalbum on 2011-04-30
You don't need a tool to configure the order of icons in the launcher. Drag an icon outwards from the launcher, then drag it into where you want it to go.

The "click on a running app to minimise it" is really not going to work in Unity, sorry. It's an old, unintuitive, illogical throwback from Windows' taskbar and I think it should be killed with fire. The launcher is to open programs and show running programs; making it hide running programs is simply too confusing.

Otherwise, yes, I'd agree - there should be a good way of customizing it that doesn't require installing ccsm. Oh, and the icons are too big by default on a netbook, but they're perfect on a big desktop screen.

---

### Post by Perosteck on 2011-04-30
System Settings -> CompizConfig Settings Manager (CCSM) -> _Ubunty Unity Plugin_

This is your configuration tool. 

Other useful things:
"Super" key + w = show all open windows 
"Super" key + s = show workspaces
"Super" key + d = close all windows or make them come back
alt+tab = cycle through windows
click on app launcher icon = shows all open windows of this app, making the launcher icons double as "stacks".
strg+alt+arrow key = move to other workspace


To move launcher icons: click and drag it out of the bar to drag it back in at another position, or with click and hold you don't have to drag it to the right but can move it inside the bar. 

You can also create _any_ terminal command as a launcher with right click on desktop -> create launcher. E.g. you can have links to single documents, web pages etc on there. Example: "firefox ubuntuforums.org" in the command line.

---

### Post by Wiebelhaus on 2011-04-30
> **Perosteck said:**
> System Settings -> CompizConfig Settings Manager (CCSM) -> _Ubunty Unity Plugin_

This is your configuration tool. 

Other useful things:
"Super" key + w = show all open windows 
"Super" key + s = show workspaces
"Super" key + d = close all windows or make them come back
alt+tab = cycle through windows
click on app launcher icon = shows all open windows of this app, making the launcher icons double as "stacks".
strg+alt+arrow key = move to other workspace


To move launcher icons: click and drag it out of the bar to drag it back in at another position, or with click and hold you don't have to drag it to the right but can move it inside the bar. 

You can also create _any_ terminal command as a launcher with right click on desktop -> create launcher. E.g. you can have links to single documents, web pages etc on there. Example: "firefox ubuntuforums.org" in the command line.

Cool tips! thanks!

---

### Post by jblah on 2011-04-30
I think I am also in #3. Unity still needs a lot of work. I do not understand why when I have firefox on full screen it shows the minimize, close, maximize buttons on the panel bar. Also every program that is running has their toolbar options available on the panel at the top...that is very strange. 

I also do not understand why we cannot disable the launcher bar on the right and just have a normal panel up at the top similar to gnome. We also don't seem to be able to change the color of the launcher bar. I use cairo-dock..so I do not really need the launcher since I already have a launcher that I like why can we not disable this? 

I'll keep with ubuntu for a few more releases and see where unity goes. I do think that they have potential but like all things it needs work. Nothing is perfect the first time around.

---

### Post by Perosteck on 2011-04-30
The left side gnome top panel transforms into the application menu bar when you launch an application. This has been done for space saving reasons.

The functionality of the then inaccessible top-left side can also be found in the launcher panel on the left, except the change desktop background function which can be accessed normally by right-clicking on the main area of the desktop itself. The functions that handle any links on the desktop itself can not be accessed as long as an app is open. But that's no problem since you don't see much of them anyway. You can still access them via the homefolder launcher.

Basic documentation for unity here: 
[http://theravingrick.blogspot.com/](http://theravingrick.blogspot.com/)

---

### Post by jblah on 2011-04-30
> **Perosteck said:**
> The left side gnome top panel transforms into the application menu bar when you launch an application. This has been done for space saving reasons.

The functionality of the then inaccessible top-left side can also be found in the launcher panel on the left, except the change desktop background function which can be accessed normally by right-clicking on the main area of the desktop itself. The functions that handle any links on the desktop itself can not be accessed as long as an app is open. But that's no problem since you don't see much of them anyway. You can still access them via the homefolder launcher.

Basic documentation for unity here: 
[http://theravingrick.blogspot.com/](http://theravingrick.blogspot.com/)


i think the problem is that individuals like myself customize ubuntu to make it look and behave like we want to. i think the base model for unity is nice for people who are new to linux or utilize the default settings. 

I think that is where the main problem is. Unity is not as flexible for people who like to customize their settings. I can clearly see the strength of unity for netbooks but for desktops and advanced laptops..it is really not customizable yet for individuals like myself.

---

### Post by Perosteck on 2011-04-30
> **jblah said:**
> i think the problem is that individuals like myself customize ubuntu to make it look and behave like we want to. i think the base model for unity is nice for people who are new to linux or utilize the default settings. 

I think that is where the main problem is. Unity is not as flexible for people who like to customize their settings. I can clearly see the strength of unity for netbooks but for desktops and advanced laptops..it is really not customizable yet for individuals like myself.



Apart from putting the launcher on bottom, what would you customize personally and why? The color of the launcher bar? Really? My taste flipped 180&#8242; after a couple of minutes with unity, I suspect so can yours. I had been dead set to install gnome 3 as soon as possible.

---

### Post by jblah on 2011-04-30
> **Perosteck said:**
> Apart from putting the launcher on bottom, what would you customize personally and why? The color of the launcher bar? Really? Try to give a rational answer, not burning emotion. Because my burning hateful emotions flipped 180&#8242; after a couple of minutes with unity, I suspect so will yours.

well you got the "maximize" problem where all the "minimize" "maximize" and "close" icons appear across the top panel rather than with the open application. I really do not like that. 

I also do not like the fact that I cannot just disable the launcher bar if i so wish. I mean seriously why would i go with this default launcher and not something like docky or cairo-dock which is much more aesthetically pleasing. 

and yes why can I not change the color? Isn't that the appeal of Linux? You can customize it however and whatever way you want to customize it. We are not windows or mac where you get what you get. If you don't like it then tough. That is not where Linux should be at.

I do not hate unity, I just think that it still needs a few more release to be better. It just doesn't seem desktop ready for me. Would I still recommend this to people who use Windows? Absolutely because I think it will be easier and safer from them to utilize than the alternative but for me..i like flexibility and customization.

update: one more thing i need to add that is not easy to do (or perhaps i haven't learned to do) is add apples. in the previous version you would just click on the panel and add a new applet. we can't conveniently do that in this version.

---

### Post by tristan on 2011-05-01
> **3rdalbum said:**
> You don't need a tool to configure the order of icons in the launcher. Drag an icon outwards from the launcher, then drag it into where you want it to go.

Thanks for that tip 3rdalbum.

---

### Post by nourathar on 2011-05-01
I *completely* agree with Tristan; i´m still relatively new to Ubuntu, and I´ve come to like it very much because of its almost unlimited customizability (and great community). 
Now I see a new item that is much less customizable than usual, and I see discussions in which people are almost telling others what to like ? That is strange..

---

