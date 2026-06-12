---
title: "old laptop as a server - turning off screen?"
date: 2007-07-21
forum: Server Platforms
---

### Post by sunset_studies on 2007-07-21
Hi, 

I've just started using an old laptop as an occasional server. It's cool, but one thing I can't work out is how to turn off the screen. The screen is just sitting there, blanked due to inactivity, but not 'off' in the 'using no electricity' sense. 

Does anybody know how I can turn the screen 'off'? The server is, and will remain, command line only.

Thanks

---

### Post by ajehals on 2007-07-21
I do this a lot with old kit - and usually its just a case of closing the laptop and making sure that any BIOS power management features (like suspending when the lid is closed :) ) are disabled.

---

### Post by sunset_studies on 2007-07-21
hi & thanks for the reply,

it's been that long since I'd used this laptop that I'd forgotten the old 'place something heavy on the lid sensor' trick. Of course :)

Is it safe to fully close the lid? I always imagined it would cause overheating.

---

### Post by p_quarles on 2007-07-21
Only if the vents are in between the keys :) If they're on the sides or the back, it should be fine.

Plus, my understanding is that running the monitor is actually one of the bigger power tasks on a laptop. If you get it to switch off, it might run cooler.

---

### Post by sunset_studies on 2007-07-21
The 'vents' are on the bottom of the laptop, but I think the laptop also relies on air escaping through the circular holes between the keyboard and the screen. If I knew how to measure the cpu temp I would try it with the lid down but I think this laptop (produced circa 2001) is a bit too old for those temperature sensor software things.

Oh, one more thing, getting it to suspend to RAM is of course possible via SSH, but is it also possible to get a computer (I don't think it has wake-on-lan) to resume via SSH?

Thanks!

---

### Post by kerry_s on 2007-07-21
xset dpms force off

is what i use " man xset "

---

### Post by sunset_studies on 2007-07-21
hi kerry_s, yes that's what I've used in the past too, but only on machines with GUIs. I can't seem to get this to work otherwise, the error is 'xset:  unable to open display'.

Not to worry though as I'm now using the 'closed lid' solution instead as I realised I can monitor the temp from '/proc/acpi/thermal_zone/THZN/temperature'

---

### Post by p_quarles on 2007-07-21
> The 'vents' are on the bottom of the laptop, but I think the laptop also relies on air escaping through the circular holes between the keyboard and the screen. If I knew how to measure the cpu temp I would try it with the lid down but I think this laptop (produced circa 2001) is a bit too old for those temperature sensor software things.
D'oh. You're totally right. I just checked my laptop, and saw that it too has heat vents in the location you mentioned. That's what I get for shooting from the hip.

Cool that you got the temp sensors to work, though. I'm curious to know what it's running with the lid closed. I'd guess it wouldn't be that hot usually, but what about large file transfers?

---

### Post by sunset_studies on 2007-07-22
background info: a few torrents running are running (Torrentflux) and Apache is serving a page every 1 min... so really, very little processing atm.

With the lid closed the temp got up to 45 C.

After 5 minutes with the lid open (but the screen off) the temp dropped to  44 C. So, using my fantastic scientific method, I'd conclude that having the lid open makes very little difference with this particular laptop :popcorn:

Outside temp is currently 17 C.

edit: results from large file transfer to come...

---

### Post by p_quarles on 2007-07-22
That's not bad at all. 

That said, you might get it to run cooler by using an underclocking application. My laptop runs between 22 and 27 C idling, but it uses BIOS-based underclocking. I'm pretty sure there's Linux software available to do this, though, and you might want to look for it. Save on energy bills, and keep it cool in preparation for any heavier jobs.

---

### Post by sunset_studies on 2007-07-22
results from a large file transfer:

lid open: 51 C

lid closed: 53 C

Might have to rethink my initial conclusion.


Underclocking sounds good, I think that might be possible using laptop-mode too. Will have to read up about that.

Any idea about the remote 'resume'  without wake-on-lan?

---

