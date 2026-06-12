---
title: "Battery Discharge Not Detected on PanP6"
date: 2010-02-16
forum: System76 Support
---

### Post by Noah0504 on 2010-02-16
I've tried to do some searching on these forums, but never came across quite the same issue.  This morning I resumed my PanP6 at work.  I had yet to plug in the power adapter as I was just trying to get a few things printed out before I became settled.

I noticed that the battery icon was not in the top right corner.  I went into the preferences to make sure I had it enabled.  It was.  When I checked the option to always display it, it showed up, but it didn't show that it was discharging.  It just said the battery was fully charged.  When I did finally plug in the power adapter, it showed that it was charging and exactly what percent of a charge it had...

Not really sure what the issue would be... in fact, I've never seen that happen on any notebook I've loaded Ubuntu or Linux in general on.

---

### Post by thomasaaron on 2010-02-16
I believe that is the same issue as this...

[http://ubuntuforums.org/showthread.php?t=1404628](http://ubuntuforums.org/showthread.php?t=1404628)

??

---

### Post by Noah0504 on 2010-02-16
> **thomasaaron said:**
> I believe that is the same issue as this...

[http://ubuntuforums.org/showthread.php?t=1404628](http://ubuntuforums.org/showthread.php?t=1404628)

??

I did come across that thread, but it looks like that user's problems were fixed with the standard 9.10 kernel (which I'm using now).  I don't really feel like compiling a new kernel, so it might just be something I live with.  :P

Who knows, maybe I'll get bored later once I'm home from work.  So far, this is the only issue I have run into.  Other than that, everything is working just as or even better than I expected.  A fine piece of hardware it is!

I'll mess with the problem more when I get home, but I was trying to see if it was a know problem in hardware newer than the P5.

---

### Post by revlimiter on 2010-02-16
I have the same problem with my PanP6. Exactly. If I suspend while plugged in and resume on battery, I don't get the battery icon. But when I plug power back in, it gives me the charging icon and tells me how far the battery was discharged. 

It doesn't bother me very much, so I hadn't made a thread.

---

### Post by miniyak on 2010-02-17
i guess this is an issue with the 6 also..

Noah, where did you find that info about the kernel?

I really have yet to look into this more, ive been more concerned w/ my new bamboo pad and monitor. Like revlimiter was implying this is really just a minor annoyance.. but i do find it funny though, that is, when i plug in, my panp tells me that the battery is "discharging", lol its like every thing is backwards or something

---

### Post by revlimiter on 2010-02-26
I seem to have discovered a work-around. I disabled the battery icon in the gnome panel and enabled Battery Monitor in Gnome Do's Docky panel. The newest version of Do for Karmic has a handful of things called "docklets" that are pretty useful. Among them is a fairly nice battery app. 

Maybe not a good fix for everyone, but I'm a huge fan of Gnome Do, so it works for me.

---

### Post by Noah0504 on 2010-02-26
> **revlimiter said:**
> I seem to have discovered a work-around. I disabled the battery icon in the gnome panel and enabled Battery Monitor in Gnome Do's Docky panel. The newest version of Do for Karmic has a handful of things called "docklets" that are pretty useful. Among them is a fairly nice battery app. 

Maybe not a good fix for everyone, but I'm a huge fan of Gnome Do, so it works for me.

Seems to be working!  :P  I wonder why the Gnome applet is broken?  Oh well.  I use Gnome Do, so this two works for me.  And if you haven't tried this great application... you probably should!  :P

---

### Post by miniyak on 2010-03-08
haha, i just tried "Do" and like it also, funny how this type of stuff pops up when looking over problems.

One issue though.. and i think this might just be me, but whenever i try to go into Do settings it crashes...

Say things were working right where would i get a hold of the setting for adding "docklets"?

---

### Post by revlimiter on 2010-03-10
right click on the Gnome Do icon on the far left of the dock, hit Preferences. 
Go to Appearance tab (far right). On the bottom is the docklet selector. Select Battery monitor. 

And as an aside, if you want to get the weather to work, you also select it from the Appearances tab to turn it on. 
THEN you go to the Plugins tab and select Docklets on the drop box. From there you can configure the weather. 
Very straight-forward, eh? I struggled with this for minutes before finding a posted walkthrough solution. 

If you're having problems with crashing, try making Docky smaller. It sounds strange, but there's a problem rendering graphics of exactly the default Docky size. If you make it smaller (grab the separator between the apps and the docklets, the mouse turns into an up-down arrow), it'll become much more stable.

---

