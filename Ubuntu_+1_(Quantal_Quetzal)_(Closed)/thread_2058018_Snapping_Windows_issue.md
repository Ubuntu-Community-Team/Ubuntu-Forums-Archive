---
title: "Snapping Windows issue"
date: 2012-09-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-09-14
Although I do not have the "Windows Snapping" plugin activated, windows snap anyway when I resize their upper border towards the Global Menu. Detaching them requires some "force". That is more easily detected by activating the "Wobbly WIndows" plugin: When you try to detach the window top from the Global Menu, you'll see it deform. 

See the video:
[http://www.youtube.com/watch?v=E-lGIIoVIiM](http://www.youtube.com/watch?v=E-lGIIoVIiM)

It is impossible to change settings in "ccsm / Snapping Windows", even though the plugin is disabled. Here's a video showing it:
[http://www.youtube.com/watch?v=2u02qEV8uI4](http://www.youtube.com/watch?v=2u02qEV8uI4)

Regards,
Effenberg

---

### Post by arpanaut on 2012-09-14
I too never figured out to stop that behavior entirely,
so I just leave the plugin enabled and reduce the values such
[ATTACH]224143[/ATTACH]

Relieves the irritation greatly!
I know it's a work around and not a solution,
but hey, works for me.  ;)

---

### Post by effenberg0x0 on 2012-09-14
> **arpanaut said:**
> I too never figured out to stop that behavior entirely,
so I just leave the plugin enabled and reduce the values such
[ATTACH]224143[/ATTACH]

Relieves the irritation greatly!
I know it's a work around and not a solution,
but hey, works for me.  ;)

That's a good workaround :) Did you see my second video? I can't even uncheck the config checkboxes (same ones you posted a screenshot). They automatically return to their previous status. 

Question: gnome-control-center -> Displays -> "Sticky Edges". Is it related somehow? 

Regards,
Effenberg

---

### Post by arpanaut on 2012-09-14
> Question: gnome-control-center -> Displays -> "Sticky Edges". Is it related somehow? That setting I had not seen before, ????
Probably has to do with dual monitors and resistance/ease of moving windows between them?
It would seem to me that if the plugin is disabled then one would not be able to change settings in it. Si? No.

---

### Post by cariboo on 2012-09-14
effenberg0x0, I'm confused, :) If your are running an Nvidia graphics card, why are you looking at the display settings in gnome-control-center?

---

### Post by arpanaut on 2012-09-14
It seems that with the settings, in ccsm, that one or the other must be enabled.
If you try to disable the selection without the one next to it enabled it will return as in video.

---

### Post by effenberg0x0 on 2012-09-14
> **arpanaut said:**
> That setting I had not seen before, ????
Probably has to do with dual monitors and resistance/ease of moving windows between them?

It's been there for a while. I use two monitors but resistance between screens is always on for me, with or without this setting.I sort of did something like the workaround you just posted here but in ccsm / Unity Plugin / Experimental to make it less "sticky".
> **arpanaut said:**
> 
It would seem to me that if the plugin is disabled then one would not be able to change settings in it. Si? No.
Yea, I also thought so... but enabling, disabling the plugin and its checkboxes is auto-reverted (as shown in the video) by Unity ghosts and the snapping behavior continues always on. Go figure...

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-09-14
> **cariboo907 said:**
> effenberg0x0, I'm confused, :) If your are running an Nvidia graphics card, why are you looking at the display settings in gnome-control-center?

Hey :) I'm just digging out a way to fix the small things that are bothering me in the current QQ state / UI/UX-related. 

"Snapping Windows", "Edge Resistance", or whatever the cool kids call it these days obviously wouldn't ever be in nvidia-settings as it's unrelated to the VGA itself. 

I have dissected dconf and even the settings we know and love in gconf, ccsm and the dot settings files, with no luck whatsoever.

I'm just shooting at all directions now to see if I hit something :)

Regards,
Effenberg

---

### Post by arpanaut on 2012-09-14
Ghosts?  :shock:

LOL I know what you mean! :biggrin:
They are everywhere...

---

### Post by effenberg0x0 on 2012-09-14
> **arpanaut said:**
> Ghosts?  :shock:

LOL I know what you mean! :biggrin:
They are everywhere...

LOL... But hey, you've seen my video. For me, checkboxes that check/uncheck themselves can only be under influence of espers and/or manifestations from beyond this reality. Disabled (as in "grayed") checkboxes would be much less spooky IMO. But then again I'm not sure if the degree of spookiness in the UI is a design decision.

Regards,
Effenberg

---

### Post by mc4man on 2012-09-15
I think this is because of the option in 'resize windows' -"Maximize Vertically if screen edge hit" 
Maybe a bug or maybe what happens with such 'Vert maxed' windows..

---

