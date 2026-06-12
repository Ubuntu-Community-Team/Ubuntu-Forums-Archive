---
title: "Brand New Starling Touchpad Issues..."
date: 2011-03-05
forum: System76 Support
---

### Post by TCWriter on 2011-03-05
Just took delivery of a brand new Starling netbook about a week ago (Star 4) 

Unfortunately, the touchpad is pretty flaky, yet there's no touchpad configuration in the preferences menu - and nothing in the "Mouse" settings either. 

A search for "touchpad" in Synaptics says the Xserver Synaptics Touchpad driver is installed (none of the others), but there's no way I can find to configure it.

It's extremely touchy and I'm constantly re-typing stuff because of grazes. 

I'd love to be able to:

[LIST]
[*]Turn it off when the mouse is attached
[*]Turn down the sensitivity (if possible)
[*]Enable the "smart" setting that turns it off when I'm typing
[/LIST]In a perfect world, somebody would rig up a keyboard shortcut which turned the thing on and off, but I'll settle for being able to configure it. 

Any ideas?

---

### Post by StephenDavison on 2011-03-05
I'd say something is wrong if you don't see a Touchpad tab in the dialog box produced by selecting the System->Preferences->Mouse menu option.  The Touchpad preferences includes options to "Disable touchpad while typing" and to enable two-finger scrolling.  Those are my favorites.  But then again, the Starling's Synaptics touchpad may not be the same as my MSI Wind's Synaptics touchpad.

---

### Post by jangat on 2011-03-06
I have had a Star1 for over a year and never found the "disable while typing" option for the touchpad to really work. I've seen some complicated work-arounds posted here, but when I have a mouse attached I use something pretty simple (but maybe not elegant). In a terminal window, type the following command:[INDENT]sudo modprobe -r psmouse
[/INDENT]which completely disables the touchpad. To reinstate it, type[INDENT]sudo modprobe psmouse
[/INDENT]Other than the touchpad, the I really like the Star1 keyboard. I would also like to thank whoever posted these suggested commands some time ago.

---

### Post by TCWriter on 2011-03-06
Sadly, you're probably right, but I was hoping to hear I was overlooking something obvious...

---

### Post by TCWriter on 2011-03-06
> **jangat said:**
> I have had a Star1 for over a year and never found the "disable while typing" option for the touchpad to really work. I've seen some complicated work-arounds posted here, but when I have a mouse attached I use something pretty simple (but maybe not elegant). In a terminal window, type the following command:[INDENT]sudo modprobe -r psmouse
[/INDENT]which completely disables the touchpad. To reinstate it, type[INDENT]sudo modprobe psmouse
[/INDENT]Other than the touchpad, the I really like the Star1 keyboard. I would also like to thank whoever posted these suggested commands some time ago.

Thanks for the tip. It should prove useful when I'm using a mouse.

I too like the keyboard, but the touchpad isn't recessed and butts right up against the spacebar, so I suspect it's going to remain a problem. 

I like the machine, but I'm having problems with the trackpad, wireless, battery indicator... 

Not exactly a solid start.

---

### Post by Speedwagon on 2011-03-06
> **TCWriter said:**
> Just took delivery of a brand new Starling netbook about a week ago (Star 4) 

Unfortunately, the touchpad is pretty flaky, yet there's no touchpad configuration in the preferences menu - and nothing in the "Mouse" settings either. 

A search for "touchpad" in Synaptics says the Xserver Synaptics Touchpad driver is installed (none of the others), but there's no way I can find to configure it.

It's extremely touchy and I'm constantly re-typing stuff because of grazes. 

I'd love to be able to:

[LIST]
[*]Turn it off when the mouse is attached
[*]Turn down the sensitivity (if possible)
[*]Enable the "smart" setting that turns it off when I'm typing
[/LIST]In a perfect world, somebody would rig up a keyboard shortcut which turned the thing on and off, but I'll settle for being able to configure it. 

Any ideas?

You can turn the touchpad on and off by FN+F1

I do find the touchpad to be a bit more sensitive than I like, but having the ability to turn it on/off while I type has made the starling incredibly more friendly to use.

---

### Post by TCWriter on 2011-03-06
> **Speedwagon said:**
> You can turn the touchpad on and off by FN+F1

I do find the touchpad to be a bit more sensitive than I like, but having the ability to turn it on/off while I type has made the starling incredibly more friendly to use.
Hey, now that's useful info. I'm an Emacs user, so don't really need the mousepad when I'm writing. 

Looked at the function icons on the top row when I got the thing, but didn't know what half were for.

---

### Post by EJJ on 2011-03-08
Fn+F1 is a MUST when I type. This touchpad is so sensitive that my headphone cable touching it makes it go nuts. The other day a I tossed an index card onto my desk and it landed on the touch pad: it woke it up from the screen saver.

---

### Post by TCWriter on 2011-03-08
> **EJJ said:**
> Fn+F1 is a MUST when I type. This touchpad is so sensitive that my headphone cable touching it makes it go nuts. The other day a I tossed an index card onto my desk and it landed on the touch pad: it woke it up from the screen saver.
Yeah, I'm finding that to be very true. Maybe if the pad had been recessed a little, it would be less prone to false alarms. 

The wireless is also pretty frustrating, which is too bad; aside from those two things, it's a great little machine.

---

### Post by EJJ on 2011-03-09
Wireless issues seem to be a common thing with the Starling. However I will point out that I've heard about 'Wireless' problems with nearly every single type of computer device I've ever heard of. From Macs, to other PC's, to PSP's, iPad's, all kinds of things. So many people use so many different kinds of routers, and so many different security set ups, etc. that I think its just the nature of wireless internet to have some problems. Technology is made by humans, which have their flaws, expecting things to work perfectly all the time is a little much....especially if you expect to fling a device across the room and not have the screen crack ;)


That aside, here are some of the things I've noticed with the wireless.

Always make sure that the card is ON. Press Fn+F11. It takes a second or two, but you will see the light for the wireless either turn on or turn off. Then of course make sure that you have 'networking enabled' I have seen this option sometimes turn itself off. Then if you still have troubles, just delete the 'Auto' router settings and reconnect. That seemed to solve a near two week wifi problem I was having, which now I have zero problems with.

---

### Post by TCWriter on 2011-03-09
> **EJJ said:**
> Wireless issues seem to be a common thing with the Starling. However I will point out that I've heard about 'Wireless' problems with nearly every single type of computer device I've ever heard of. From Macs, to other PC's, to PSP's, iPad's, all kinds of things. So many people use so many different kinds of routers, and so many different security set ups, etc. that I think its just the nature of wireless internet to have some problems. Technology is made by humans, which have their flaws, expecting things to work perfectly all the time is a little much....especially if you expect to fling a device across the room and not have the screen crack ;)


That aside, here are some of the things I've noticed with the wireless.

Always make sure that the card is ON. Press Fn+F11. It takes a second or two, but you will see the light for the wireless either turn on or turn off. Then of course make sure that you have 'networking enabled' I have seen this option sometimes turn itself off. Then if you still have troubles, just delete the 'Auto' router settings and reconnect. That seemed to solve a near two week wifi problem I was having, which now I have zero problems with.
My wireless problems revolve around frequently dropped connections and difficulty connecting - even as my old "g" series laptops connect perfectly to my "n" series router (and at greater distances).

For some reason, the Starling's wireless is balky, and at times it even drops the connection when I'm 15 feet away from the router.

Frustrating, but not terminal.

---

### Post by buynada on 2011-03-20
> **Speedwagon said:**
> You can turn the touchpad on and off by FN+F1

I do find the touchpad to be a bit more sensitive than I like, but having the ability to turn it on/off while I type has made the starling incredibly more friendly to use.
thanks so much! this has been bugging me for many months. It would be great if one could just deactivate the top ~5 mm of the mousepad to compensate for the poor design.

---

### Post by silverhammermba on 2011-03-22
My issue isn't the touchpad being on, it's that the tap-to-click is too sensitive.

There is a way to disable tap-to-click in the touchpad config, but (as far as I can tell) there's no way to load the touchpad config on startup. My workaround: I made a keyboard shortcut that loads the touchpad config manually.

Each time I use my netbook, I just have to press the key combo if I'm getting accidental taps.

The wiki tells you how to set up the config [http://knowledge76.com/index.php/Star3](http://knowledge76.com/index.php/Star3)

---

### Post by pocklecod on 2011-04-11
Wow.  I've got a Star4 and I've been fighting with the touchpad since I got it.  When I'm actually using the touchpad, I really like the feel of it, the sensitivity is good, and I like the way it scrolls (I prefer the corner tap to a two-finger).  So, I've been very happy with the pad itself, except that I bump it all the time while typing.  Over time, I've trained myself not to brush it too often when typing, but that does require holding my hands at a funny angle and it isn't perfect.  I just got a nice wireless mouse to go with the starling, and was hesitantly thinking of turning off the touchpad permanently...

Now I read this thread and realize that all I needed to do the whole time was use Fn F1.  Frankly, I feel pretty sheepish - but I did want to post to say one thing, especially if System76 actually reads this thread:  It would be nice to include just a little bit of documentation with these machines to tell me this kind of basic thing.  Maybe it's supposed to be self-evident, but to me it wasn't, and I would have been even happier with my purchase had I been saved the hassle here.

---

### Post by isantop on 2011-04-12
Sorry for all of the issue your having. We do provide a welcome manual for our systems on our knowledge base, here: [http://knowledge76.com](http://knowledge76.com)

For your Starling, the information is available here: [http://knowledge76.com/index.php/Star4](http://knowledge76.com/index.php/Star4)

---

