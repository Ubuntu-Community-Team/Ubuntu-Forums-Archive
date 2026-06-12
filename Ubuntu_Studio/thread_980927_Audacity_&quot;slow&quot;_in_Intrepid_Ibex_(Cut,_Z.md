---
title: "Audacity &quot;slow&quot; in Intrepid Ibex (Cut, Zoom, Playback, etc)"
date: 2008-11-13
forum: Ubuntu Studio
---

### Post by tim__b on 2008-11-13
My problem is some how strange: I used to use Audacity (v1.3.4-beta from the ubuntu backports) on my Hardy Heron (all updates, 2.6.24-21-generic) system (1,8 GHz Sempron + 1024mb ram). For the system specs it worked flawless.

Now I bought a new system (2x2.5 GHz Core 2 Duo + 2024mb ram), installed Intrepid Ibex (incl. all updates) on it and tried Audacity v1.3.5 from the backports and v1.3.6 from GetDEB. Both versions are really slow in interface handling, like clicking a audio stream (to make a selection) it takes half a second to actually have the marker at that position.

Also audio prelistening is nearly impossible: on my "old" machine there was no problem in prelistening to for example a crossfade. On my new machine I got gaps/skips of silence when changing from one to the other stream, even so there's no gap between the tracks.

Both system have pulse audio and alsa set as output modul in Audacity. Audacity settings on both systems are default.

Does anyone have simular problems with Audacity in Intrepid and maybe know how to fix them?

PS: Next thing I try is to compile Audacity myself.

---

### Post by prshah on 2008-11-13
> **tim__b said:**
> (1,8 GHz Sempron + 1024mb ram)

Now I bought a new system (2x2.5 GHz Core 2 Duo + 2024mb ram)

, installed Intrepid Ibex (incl. all updates) on it and tried Audacity v1.3.5 from the backports and v1.3.6 from GetDEB. Both versions are really slow in 

Is it possible that you were using the amd64 (64-bit) version of Ubuntu earlier and are now using the i386 (32-bit) one?

In any case, I use Audacity from the Intrepid/i386 repos (1.3.5-beta) and face no problems with it, especially nothing like what you describe. (Though sometimes, during heavy editing, it just suddenly closes by itself, probably core-dumping, so I need to save regularly).

---

### Post by tim__b on 2008-11-13
Thanks for your answer, prshah.

I'm using 32bit Ubuntu on both systems. Hardy installed from a pressed ship-it cd, Intrepid installed from *ubuntu-8.10-dvd-i386.iso*. It's really strange because every other application is as fast as expectet and even Audacity isn't using 100% cpu power when *hanging*.

---

### Post by tim__b on 2008-11-14
As Audacity 1.3.5-beta is now available in Ubuntu Hardy Heron backports I updated it on my Hardy/old machine. Everything still works fine, from editing to prelistening. :confused: so it seems it's not about the audacity version, must be something with my machine/setup... just can't get what wrong...

---

### Post by smd0665 on 2008-11-16
Since upgrading to Intrepid, Audacity hangs when I try to export. Canceling doesn't work; I have to log out, log back in and try again. Occasionally, exporting will work, but most of the time, the elapsed time and remaining time both stay at 0:00:00 and the progress bar doesn't move. I never had this problem in Hardy.

---

