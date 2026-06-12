---
title: "Thinking about getting a Wacom tablet..."
date: 2009-11-03
forum: The Cafe
---

### Post by Cam42 on 2009-11-03
Anyone here use one? What do you use it for?
I was looking at the bamboo, but there are a bunch of options. What should I look for?
Also, how well (if at all) do they work on Linux?

---

### Post by 23meg on 2009-11-03
Wacom supports driver development, and pretty much every Wacom tablet works very well. Recent ones may not (the Bamboo Touch doesn't at the moment) but every new model tends to get driver coverage within a few months. If in doubt, do a search and/or ask at the mailing list of the [Linux Wacom Project]("http://linuxwacom.sourceforge.net/").

I've been using an Intuos 3, for sketches, Blender, wireframes; pretty much everything I don't do with a mouse and keyboard. I'm about to buy a Cintiq 12WX.

[QUOTE=Cam42]What should I look for?[/QUOTE]

Depends on what you want to do. The defining features are levels of pressure sensitivity, and size.

---

### Post by AvixK7 on 2009-11-03
I have a wacom graphire 4 tablet. I use it for touch ups and occasional drawing. really enjoying it. the new Wacom tablets look fantastic as of late. 

As for which one you should use, it depends on what you need or what you want to get out of it. If you're doing professional art, use the Intuos or Cintiq models. if you're just doing simple stuff, occasional drawing, or photoshop, get the bamboo.

---

### Post by Cam42 on 2009-11-03
Yeah, I'm pretty new to graphic design, plus, I don't have much money. So, it would seem like the bamboo is my best option. What setup is there to go through before using it? Is it just a pop in the driver disc and go sort of thing? Or is it more complex than that?

---

### Post by 23meg on 2009-11-03
None. If it's supported, it just works. You may end up tweaking input preferences in GIMP and maybe some other applications, but that's usually optional.

---

### Post by spupy on 2009-11-03
> **23meg said:**
> None. If it's supported, it just works. You may end up tweaking input preferences in GIMP and maybe some other applications, but that's usually optional.

There is also the xsetwacom util, with it you can redefine the signals the buttons send. My Bamboo Fun (the smaller one), has some ridiculous touchpad-scroll-thingie, but it doesn't work correctly (it just sucks, I think, not a linux problem), so I use the buttons for zoom-in/zoom-out.

I got a Bamboo Fun, because I wasn't sure if a tablet is going to be my thing. I don't use it that often, but I enjoy when I do. If you are looking into the more expensive Wacoms, I recommend to do some sort of trial use, or make sure you can return it if you don't like using a tablet.

---

### Post by JDShu on 2009-11-03
I have a graphire 4, its more than enough for an amateur. SInce the bamboo should be better, thats probably good enough for your needs.

---

### Post by 1111peoy on 2009-11-03
Buy a Wacom i4. Not sure if pen pressure is supported in ubuntu. But think about this first "Will I feel comfy using gimp, or other linux graphic software?". Find out if Gimp or some other linux graphic software supports a wacom i4 good. And dont forget: Pen pressure! This is very important!

But go for it! You can always use windows with photoshop, it works great with a wacom and you will have a lot of fun with it.

---

### Post by Cam42 on 2009-11-03
I use both Windows and Ubuntu, on different computers. But I do use GIMP on both machines, I can't bring myself to pay for photoshop.

---

### Post by 23meg on 2009-11-03
[QUOTE=spupy]There is also the xsetwacom util, with it you can redefine the signals the buttons send.[/QUOTE]

You *can*, but in modern times, you usually don't *have to*, which was my point.

---

### Post by hessiess on 2009-11-03
Just get one;)

---

### Post by Random-penguin on 2009-11-03
The Wacom tablets I have tried work well, unlike other cheaper tablets. I currently have the Intuos 3 used with GIMP.

---

### Post by Favux on 2009-11-03
Hi Cam42,

Right now with Karmic all the models are fully supported, including pressure, except for the new Bamboos with touch.  Like the Pen & Touch, Craft, and Fun.  Models CTL460, CTH460, CTH461, and CTH661.  We've got the stylus, eraser, and stylus buttons working for those.

With the Intuos4 a new patch for the OLED's is now available.  So that would require patching and compiling the linuxwacom drivers.  They are planning on adding it to wacomcpl.

The xsetwacom commands aren't yet obsolete.  Wacomcpl and rotation etc. still require them.  But the LWP apparently has a new wacomcpl coming out that isn't hardcoded to require HAL to return stylus, eraser, pad, etc.  And I'm sure that will apply to xsetwacom.  So with Lynx everything should work out of the box.  It's very close to that with Karmic.

Hope this helps with your decision.

---

### Post by bonfire89 on 2009-11-03
I have a thinkpad x60 tablet that I haven't really used for a year now.

I used it when I was in engineering to take math/physics notes.

I wasn't impressed with the linux note taking apps. They may have improved by now. MS onenote sadly rocked.

And after far too many hours and months cut off my life due to stress I was still unable to get it to properly work with a second monitor under linux. Here is a video of the problem since it is too difficult to describe in words. [http://www.youtube.com/watch?v=dD1vKrbYNvQ](http://www.youtube.com/watch?v=dD1vKrbYNvQ) 

With all this said, things have probably improved now.


There are a couple issues converting to all digital other than paper. 

1. unless you are going to be saving weight by replacing textbooks for digital textbooks your bag will be heavier.
1.1 if you do make this replacement, you will be alt tabbing back and forth a lot.
1.2 the alt tabing can be remedied with an external monitor... if it works
2. you live by wall outlets
3. you live by wall outlets
3.3 your friends are like, lets go study here, and you're like... noo I gotta go recharge (as if engineering isn't isolating enough)
4. your bag just because a lot more fragile.
5. more scard to leave it places than a notebook
5.1 maybe you might have to take it to the bar if you go right from class instead of leaving it in a sketchy lockers or a sketchy dorm.
6. it isn't flexible
7. it gets hot
8. it can be awkward to use
9. you can't work outside in the sun


all in all, _it was an okay experience_. And if the power outlet issue and the linux compatibility issue were resolved _I would probably do it again_ if I ever went back to a math based program (dropped out of eng)

---

### Post by ajy0852 on 2009-11-03
I have a Bamboo Fun also, and every Ubuntu release brings improvements in the functionality. I also notice the scroll wheel doesn't quite work right but that's OK with me. The mouse works better on Ubuntu now than it did under Windows XP with the driver on the disc. Just plug it in and it's ready to go, Ubuntu ships with the wacom driver by default.

There's a wacom utility on GTK-apps.org that provides a gui of sorts to configure the buttons on the wacom tablet (the GUI is just a frontend for xsetwacom). If you use it, be aware that it will generate a xorg.conf file - and Karmic doesn't like this... So check first to see if you have /etc/X11/xorg.conf (not likely if you're using Karmic). If so, back it up - and if not, after you run the wacom utility you will need to delete the xorg.conf file that it generates. (this is to say - use it at your own risk, I'm not an expert at this stuff)

[https://help.ubuntu.com/community/Wacom]("https://help.ubuntu.com/community/Wacom") is a good resource with some tips on how to set up GIMP and Inkscape with a tablet, although it hasn't been updated for Karmic yet.

---

