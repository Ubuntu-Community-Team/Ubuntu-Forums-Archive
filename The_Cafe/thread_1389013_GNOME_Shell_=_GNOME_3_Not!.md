---
title: "GNOME Shell = GNOME 3: Not!"
date: 2010-01-23
forum: The Cafe
---

### Post by k64 on 2010-01-23
Many people have made the mistake that just installing GNOME Shell on top of GNOME 2 creates GNOME 3.0. It doesn't.

Case in point: Who knows what the GNOME 3 artwork and icons will look like? Who knows what apps will be in GNOME 3, if they will change and how?

These are questions to ask before making that assumption.

First of all, GTK+ will also be rewritten from the ground up (well, sort of: It will be based on Clutter) and all GNOME apps will probably look different and have such cool things as RGBA as well as transparency. I wouldn't be surprised if the final GNOME Shell also has RGBA.

Secondly, who knows what fully new apps will come with GNOME 3 that are totally revolutionary? You really have to wait and see.

These are all points to consider.

---

### Post by juancarlospaco on 2010-01-23
*If you install Dolphin on gnome you obtain KDE 4.x*
XD

---

### Post by dragos240 on 2010-01-23
> **juancarlospaco said:**
> *If you install Dolphin on gnome you obtain KDE 4.x*
XD

If you install nautilus on KDE you obtain GNOME.

---

### Post by k64 on 2010-01-23
Exactly what I told you guys *NOT* to do!

---

### Post by n0dix on 2010-01-23
> **k64 said:**
>  You really have to wait and see.
These are all points to consider.

I not find much info about it. I expect to see the new Gnome 3, but i won't expect very excited because it is not my head Desktop Enviroment. ;)

---

### Post by juancarlospaco on 2010-01-23
Development of Gnome is slower than KDE because dont have too many people coding,
but if the final result is good, its great considering the effort of these people.
*And more code is not allways better software...*

---

### Post by k64 on 2010-01-23
> **juancarlospaco said:**
> Development of Gnome is slower than KDE because dont have too many people coding,
but if the final result is good, its great considering the effort of these people.
*And more code is not allways better software...*

As I said: GTK 3 is supposed to be a Clutter fork.

---

### Post by Frak on 2010-01-23
I think a lot of people are already very aware of this. Any time anybody says Gnome Shell = Gnome 3, somebody always jumps out from the shadows and says NUH UH, ITS NOT.

---

### Post by n0dix on 2010-01-23
> **Frak said:**
> I think a lot of people are already very aware of this. Any time anybody says Gnome Shell = Gnome 3, somebody always jumps out from the shadows and says NUH UH, ITS NOT.

Well i think, it is because they think that a new version come with  real innovation of the interface or functionality. I look gnome with the same interface since 2 years. :( . However, meanwhile i try other DE and stuffs.

---

### Post by Skripka on 2010-01-23
> **k64 said:**
> As I said: GTK 3 is supposed to be a Clutter fork.

This post is unintentionally funny.

---

### Post by Mr. Picklesworth on 2010-01-23
> **k64 said:**
> First of all, GTK+ will also be rewritten from the ground up (well, sort of: It will be based on Clutter) and all GNOME apps will probably look different and have such cool things as RGBA as well as transparency. I wouldn't be surprised if the final GNOME Shell also has RGBA.No, it isn't.
GTK is making a major release (3.0) because it represents a decisive API change; dropping direct access to properties in favour of getters and setters, amongst other small things that can break compatibility.

This leads in to possibilities for a nice animation framework (on the roadmap for some point soon during the 3.x series).

Gnome Shell already does RGBA, since it uses Clutter *as opposed* to GTK+ to draw the majority of its user interface. GTK+ already does RGBA, too; it's just that it is not enabled by default, so only a few apps enable it on their own end (for no apparent reason). The client-side window decorations patch would have enabled RGBA by default, but it looks like that will be sitting this release out due to some possible breakage.

Here you go: [http://live.gnome.org/ThreePointZero/Plan](http://live.gnome.org/ThreePointZero/Plan)

---

### Post by aviedw on 2010-01-23
Will i always have to disable my Compiz to run Gnome Shell. I think its a cool interface. But i hate the idea of having to start it the way that i do.  I wish it could automatically load up when i turn on the system. It might already have that function and im just showing my novice ways lol.

---

### Post by MooPi on 2010-01-24
What ?

---

### Post by Frak on 2010-01-24
> **MooPi said:**
> What ?
inorite?

---

### Post by k64 on 2010-01-24
> **aviedw said:**
> Will i always have to disable my Compiz to run Gnome Shell. I think its a cool interface. But i hate the idea of having to start it the way that i do.  I wish it could automatically load up when i turn on the system. It might already have that function and im just showing my novice ways lol.

System > Preferences > Startup Applications > New Startup Appliation

Name: GNOME Shell

Command: "gnome-shell --replace"

If you don't yet have it installed you can install it [here]('apt:/gnome-shell')

---

### Post by lisati on 2010-01-24
> **Frak said:**
> inorite?

Que?


BTW, the Lisati household has enough clutter without a garden gnome messing with our forks or other cutlery.

---

### Post by symon1980 on 2010-05-27
> **k64 said:**
> 

First of all, GTK+ will also be rewritten from the ground up (well, sort of: It will be based on Clutter) 


1) GTK is not being rewritten at all.. it is getting a cleanup and removing deprecated libraries no longer needed

2) Clutter is a window manager with compositing... like what compiz is... Clutter is merely replacing the current window manager "metacity"

Although I'm also eagerly awaiting gnome3... don't get too excited... There isn't a whole lot of exciting ideas coming.... 

we'll see....

---

### Post by TheNessus on 2010-05-27
> **Frak said:**
> Any time anybody says Gnome Shell = Gnome 3, somebody always jumps out from the shadows and says NUH UH, ITS NOT.

Any time anybody says Gnome Shell = Gnome 3, a kitten dies.

---

### Post by Frak on 2010-05-27
Sad Kitten

---

### Post by julio_cortez on 2010-05-27
> **TheNessus said:**
> Any time anybody says Gnome Shell = Gnome 3, a kitten dies.
I just found [THIS]("http://files.myopera.com/eitaps/albums/289962/Dust-Photobucket.iminursrvrstelinurdataz.jpg") in my server room and seem to be unable to send him out..

So, let's try to get the server room clean:
[SIZE=4]**Gnome Shell = Gnome 3**[/SIZE]

**[SIZE=5]DIE, DIRTY BEAST.. DIEEEE!![/SIZE]**

*No cats were harmed during the making of this post. No, seriously. I checked outside and [the cat of my neighbour is still there staring at me]("http://www.hidden-anime.com/images/bancats/I_IZ_SERIUS_ADMNIM_THIZ_IZ_SERIUS_BIZNIS_lolcat.jpg").*

---

### Post by ssj6akshat on 2010-05-27
> **symon1980 said:**
> Clutter is a window manager with compositing... like what compiz is... Clutter is merely replacing the current window manager "metacity"


Uh no.Clutter is a toolkit(like Qt and GTK) and the one replacing Metacity is Mutter(which is Metacity with Clutter).

---

### Post by 23meg on 2010-05-27
> **ssj6akshat said:**
> Uh no.Clutter is a toolkit(like Qt and GTK) and the one replacing Metacity is Mutter(which is Metacity with Clutter).

Clutter isn't a toolkit in the sense that Qt and GTK+ are; it's more of a graphics library. GNOME Shell uses (alongside some GTK+) a custom Clutter-based toolkit called ST (Shell Toolkit) that was derived from the Moblin UI Toolkit (nowadays known as Mx).

---

