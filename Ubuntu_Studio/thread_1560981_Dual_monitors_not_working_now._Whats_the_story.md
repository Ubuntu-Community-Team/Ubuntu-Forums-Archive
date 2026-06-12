---
title: "Dual monitors not working now. Whats the story???"
date: 2010-08-25
forum: Ubuntu Studio
---

### Post by evanm457 on 2010-08-25
Hi, im after getting ubuntu through wubi. because my laptop screen is broken i couldnt install it through boot.. but i had a secondary monitor so vista ran through this and i was relieved yesterday when ubuntu worked perfectly in my secondary monitor also, running as a duplicate screen default. But then when i installed to ubuntu studio it only recognises the broken laptop screen. As far as i can tell the problem is something with the app under system> preferences> monitors as it shows up with a box saying 'unknown' in the top right of the screen instead of opening the app. Is there anything I can write in the terminal to make the software work or anyway i can just directly config the 2nd monitor. I must say it is very though to use half a screen but thankfully the top right of it still works so i can use most of the apps, places and system stuff. I would appreciate any answers as i am completly confused. Thanks :)

---

### Post by K9. on 2010-08-27
I'm using Ubuntu 9.1, Karmic Koala, and don't even have any 'monitor' option in 

system > preferences >  

I have 'display preferences' but when I click on 'detect monitors' - it only detects the netbook monitor I'm using. The other monitor I've plugged in doesn't show.

And the monitor I'm using only shows up as 'unknown monitor'.

What's the trick to get ubuntu to see more monitors in that case?

I know the same PC but under Vista Basic shows the other monitor without problems...

Thanks.

EDIT: :D okay I just needed to restart :P

---

### Post by RaumTrug on 2010-08-27
evanm: besides trying to use the <fn> key, that autostatic suggested in the other thread (for some laptops it's <fn>+<f7> or the like...), trying to toggle the monitor modes, as ubuntu should be preconfigured to listen to such a key, you could dig up in the net, searching it for the "xrandr"-tool. I can't give you a foolproof step-by-step myself, as I haven't had to use it myself yet, and also it involves knowledge of the exact hardware in your box. but be aware that it might involve "serious hackery" on the console and modifying the xorg.conf, so I guess it's better be done by someone who knows what he/she's doing, and not by a noob, sorry. maybe x could also be configured to treat the external monitor as primary, and ignore the broken internal this way, who knows, but all you need is I guess a "clone"-mode. that's why I suggested hooking the hd to another machine for install & configuration, as it'll probably be very hard to do without an intact screen. also sorry again: the way everything is preconfigured for a laptop, is to have a working internal screen, and use the external as secondary, auxiliary etc. you can't expect a generic distro to take care of cases like broken primary hardware ;)

also: if normal ubuntu worked with the external without hassles, and ubuntu studio didn't, why don't you just install normal ubuntu again, and install the nessicary packages for studio work manually? you'll basically have the same as ubu.studio then, you'll just have to manually install some packages & configure one or another thing. I think many people using ubuntu for video/audio work as well as normal desktop things go this way, no need to have 2 different ubuntus installed then.

cheers, good luck! :D

---

