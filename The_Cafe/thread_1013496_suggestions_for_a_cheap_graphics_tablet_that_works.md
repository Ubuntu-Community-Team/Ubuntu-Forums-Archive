---
title: "suggestions for a cheap graphics tablet that works in linux"
date: 2008-12-16
forum: The Cafe
---

### Post by Bubs on 2008-12-16
I've looked at a wacom and although they are rumored to be awesome, I can't afford one.  or can't justify the $300 for one.  I had a hanvon but it never worked with linux and I lost the pen.  And if you lose a hanvon pen.  well...  you can't get a replacement, you have to buy a new setup.

So!  Does anyone have experience with an inexpensive graphics tablet that works with linux?  and a mac.  but I'm assuming that if it works with linux it would work with a mac too.  since the order of operation is usually windows, mac, linux...  

I don't want a tiny tablet since they are set up so that top right on the tablet is the top right on your screen. (I don't know the term for that) and I have a widescreen monitor so I would like a widescreen tablet.

I would like the options to work too.  Like pressure sensitivity and tilt if the tablet supports it.  Actually this is important.  I do a lot of graphics work and would like to have this working.


but cheaper than a wacom...

Ready...  GO!

---

### Post by igknighted on 2008-12-17
I got a 4x6 wacom bamboo for $60 from best buy... suits every need I've ever had.  If you are doing hobby work that's really all you need (I don't feel I would benefit at all from a larger tablet), and if you are a pro, then suck it up and drop $300, you won't find anything cheaper that's comparable.

---

### Post by Bubs on 2008-12-17
> suck it up and drop $300 :lolflag:  Nice!

I guess I should.  but I don't have the cash now. so I'll wait.  I would do most of the more involved graphics work on the mac with photoshop and zbrush.  So most graphics pads would work out the box on that.  

but I would kind of like it to work with the linux box too.  maybe get a pen workflow going with maya or something.  and do a few quick sketches with Pencil, the app, before I do CG animation.  Gimp work..

simple ****

---

### Post by ssam on 2008-12-17
[http://linuxwacom.sourceforge.net/](http://linuxwacom.sourceforge.net/) lists some tablets that should work.

however intrepid currently has an old version of wacom-tools, which is causing problems for many tablet users [http://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/291908](http://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/291908) . It is already fixed for jaunty, but hopeful the it will be fixed in intrepid soon.

---

### Post by red_Marvin on 2008-12-17
I have a wacom bamboo and love it, and it's far below $300 or you're being ripped of and mugged at the same time.

---

### Post by Swagman on 2008-12-17
Both of my daughters use this [**Graphire 4**](http://www.tablet4u.co.uk/products/en/graphire4-tablets.html) tablet in Ubuntu with ArtRage2 under Wine.

---

### Post by Bubs on 2008-12-17
> I have a wacom bamboo and love it, and it's far below $300 or you're being ripped of and mugged at the same time.

No..  I was thinking more along the Intuous line of talets.  they're more expensive than the bamboo.

---

### Post by simtaalo on 2008-12-17
DON'T get a trust/aiptek, i recently acquired one and haven't managed to [get it working yet.](http://ubuntuforums.org/showthread.php?t=1011582)

---

### Post by red_Marvin on 2008-12-17
> **Bubs said:**
> No..  I was thinking more along the Intuous line of talets.  they're more expensive than the bamboo.
I know, it was just me marking the quite vast price difference between a bamboo and an intuous models. However, if you aim specifically for an intuous instead of, "any graphic tablet, preferably a wacom", I expect you'll have to pay.

---

### Post by nkri on 2008-12-17
I've been using Genius Mousepen 8x6 tablets (around 50USD on Amazon) at school for a couple months now and they've been great...I just ordered one last night and it should be in by the weekend.  I haven't tried one yet in Ubuntu (we use Vista at school:(), but I'll try when I get it and post if it works.

If you're looking for cheap, Genius tablets are great for the price and probably the best you'll get, since they work just like Wacoms.

Good luck!
-nkri

---

### Post by Bubs on 2008-12-17
you know I may get a bamboo fun.  they are pretty inexpensive and they are wacom brand so I at least know they are from a reliable company and would work on linux and the mac.  I just looked and they come in a small and medium format.  I may look and see if the medium will go on sale sometime.  Currently they are almost double the $ than that of the small.

Unless nkri comes back and says the genius tables are wonderfull with linux.

---

### Post by nkri on 2008-12-26
So I finally got my Genius tablet last night, and after a very easy setup, following [_this_]("http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html") guide, the tablet works beautifully in Intrepid:D

If you do end up getting one of these and use the above link, don't forget to add the tablet name in the HAL script where the author wrote "NAME OF YOUR TABLE OBTAINED FROM PREVIOUS STEP;" if you forget this as I did, the tablet will not function.  As for pressure sensitivity in GIMP, you have to go into Edit>Preferences>Input Devices>Configure Extended Input Devices, then change the device to the tablet (which should be at the bottom of the list), and change Mode to 'screen.'

Good luck, and hopefully this will save you time and money with your tablet!
-nkri

EDIT: attached is a .deb of the Wizardpen driver, if anyone's interested:)  Before you install, though, you have to run the command
```
sudo mkdir /usr/local/share/man
```

---

### Post by Bubs on 2008-12-26
@NKRI

You mind if I ask what tablet you have?  the G-pen m609 looks nice and I was just wondering which one you got?

---

### Post by Islington on 2008-12-27
to all of you with tablets, I have a tablet pc myself, do try out the Easystroke Gesture Recognition Program.:)

---

### Post by nkri on 2008-12-27
> **Bubs said:**
> @NKRI

You mind if I ask what tablet you have?  the G-pen m609 looks nice and I was just wondering which one you got?

I have a [_Mousepen 8x6_]("http://www.amazon.com/Genius-MousePen-6-Inch-Graphic-Tablet/dp/B000LEI95I/ref=pd_bbs_sr_1?ie=UTF8&s=electronics&qid=1230388459&sr=8-1").

According to [_this_]("https://help.ubuntu.com/community/TabletSetupWizardpen") page, the G-Pen has been tested and is supported...I assume that if one Genius tablet works with this driver, the others should as well:)

Good luck!
-nkri

---

### Post by Angry_Mushi on 2009-01-03
> **nkri said:**
> So I finally got my Genius tablet last night, and after a very easy setup, following [_this_]("http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html") guide, the tablet works beautifully in Intrepid:D

If you do end up getting one of these and use the above link, don't forget to add the tablet name in the HAL script where the author wrote "NAME OF YOUR TABLE OBTAINED FROM PREVIOUS STEP;" if you forget this as I did, the tablet will not function.  As for pressure sensitivity in GIMP, you have to go into Edit>Preferences>Input Devices>Configure Extended Input Devices, then change the device to the tablet (which should be at the bottom of the list), and change Mode to 'screen.'

Good luck, and hopefully this will save you time and money with your tablet!
-nkri

EDIT: attached is a .deb of the Wizardpen driver, if anyone's interested:)  Before you install, though, you have to run the command
```
sudo mkdir /usr/local/share/man
```

I had been following the guide, but when I try to put the .fdi in file sistem/etc/hal/fdi/policy it says I don't have permission, what do I do?

---

### Post by red_Marvin on 2009-01-04
Angry Mushi: You need to copy it with super user rights, if you are doing it through nautilus, press alt+F2 and type [FONT="Courier New"]gksudo nautilus[/FONT] and press enter, or if you are doing it through the terminal, prepend a [FONT="Courier New"]sudo[/FONT] before the copying command.

---

### Post by Angry_Mushi on 2009-01-04
> **red_Marvin said:**
> Angry Mushi: You need to copy it with super user rights, if you are doing it through nautilus, press alt+F2 and type [FONT="Courier New"]gksudo nautilus[/FONT] and press enter, or if you are doing it through the terminal, prepend a [FONT="Courier New"]sudo[/FONT] before the copying command.

thanks, this may be a dumb question, how do I movea file through terminal (I was doing it in the graphic interface....

---

### Post by nkri on 2009-01-04
> **Angry_Mushi said:**
> thanks, this may be a dumb question, how do I movea file through terminal (I was doing it in the graphic interface....

You would have to change into the directory where you saved the file; for example, if you saved it to the desktop, you'd type
```
cd Desktop
```

You would then have to copy or move the file.

If you want to move the file to /etc/hal/fdi/policy without keeping the original copy (the one on the desktop), you'd type
```
sudo mv 99-x11-wizardpen.fdi /etc/hal/policy
```
*(Pulled apart, this command means: with root privileges, move 99-x11-wizardpen.fdi to /etc/hal/fdi/policy)*

If you want to copy the file to /etc/hal/policy but keep the original on the desktop, you'd type
```
sudo cp 99-x11-wizardpen.fdi /etc/hal/policy
```

Good luck!
-nkri

PS: when it asks for your sudo password, just type your regular login password (nothing will show up while you're typing) and press enter.

---

### Post by Angry_Mushi on 2009-01-04
@nkri: I have some problems, I just rebooted and it's not working, I went into xorg to see the errors that might have occured, see, whe I saked for a name for the tablet it gave me a list of about 10 names, I used the one that sounded the most logical to me "UC-LOGIC Tablet WP8060U" but right now it's not only seeing that one but also another one from the list: "Macintosh mouse button emulation" and I don't know what to do

---

### Post by nkri on 2009-01-04
Angry_Mushi-

Would you mind posting the make and model of your tablet?  Also, could you post the outputs of the following commands?
```
grep -i name /proc/bus/input/devices
```
```
lshal | less
```

Thanks!
-nkri

---

### Post by Angry_Mushi on 2009-01-04
it's the same as yours, a genius mousepen 6x8, yeah, I did that, and this is what it toldme:
N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="Power Button (FF)"
N: Name="Power Button (CM)"
N: Name="PC Speaker"
N: Name="ImPS/2 Generic Wheel Mouse"
N: Name="UC-LOGIC Tablet WP8060U"

and with lshal | less it dumps 87 devices from the global device list

---

### Post by mysticrider92 on 2009-01-04
If you are like me, there is always the cheaper and much more fun way to interact with your computer that is the multitouch table. See here: [http://nuigroup.com/](http://nuigroup.com/). You can "technically" make any size, shape, or configuration you want, and spend as much or as little as you want. I've been playing with that on my desktop, really cool stuff.

---

### Post by Angry_Mushi on 2009-01-04
> **mysticrider92 said:**
> If you are like me, there is always the cheaper and much more fun way to interact with your computer that is the multitouch table. See here: [http://nuigroup.com/](http://nuigroup.com/). You can "technically" make any size, shape, or configuration you want, and spend as much or as little as you want. I've been playing with that on my desktop, really cool stuff.

...but like thaqt you can't really draw like you would on real life... I suppose Bubs needs the tablet for that purpose

---

### Post by mysticrider92 on 2009-01-04
> **Angry_Mushi said:**
> ...but like thaqt you can't really draw like you would on real life... I suppose Bubs needs the tablet for that purpose

Well, if it is purely for drawing, the accuracy of a tablet is better. But for anything else, multitouch is just so much fun. It can be used for drawing, but it takes some practice and a good bit of work to make the screen accurate. Using a camera and an IR 'pen' (as a stylus) is pretty close to using a tablet, when set up correctly.

---

### Post by nkri on 2009-01-04
Hmm...that's awfully strange...I used the same name as you in the HAL script, and it seems to work fine.  I attached mine for comparison, but I dunno how much it'll help:(

Were there any errors when you installed the driver?

---

### Post by Angry_Mushi on 2009-01-04
I think I know what the mistake was, it saved itself as "policy" in etc/hal instead of going into the policy folder...
How do I Change the title of something with sudo rights?
how do I delete something? (I didn't find those on help, I found "kill" but wasn't sure it was the same thing)

I finally Configured it right Thanksalot

---

