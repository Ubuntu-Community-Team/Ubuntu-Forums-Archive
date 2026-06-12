---
title: "No conky display after today's updates"
date: 2011-12-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Quackers on 2011-12-20
Instead of running automatically at startup I'm getting no display. If I try using the terminal I get ```
mdoo@mdoo-VGN-AR51SU:~$ conky
Conky: forked to background, pid is 1870
mdoo@mdoo-VGN-AR51SU:~$ 
Conky: desktop window (1200023) is subwindow of root window (15a)
Conky: window type - normal
Conky: drawing to created window (0x2400002)
Conky: drawing to double buffer


```
but nothing happens. Occasionally I can get a pop-up saying that Conky stopped working unexpectedly - do I want to report it, etc.
Anybody else seeing this?
Thanks. :confused::confused::confused:

---

### Post by VinDSL on 2011-12-20
> **Quackers said:**
> Anybody else seeing this?
Thanks. :confused::confused::confused:
Well, not exactly the same problem(s), but...

When I upgraded to Conky-all 1.8.1-6 the other day, the Google Weather API wouldn't generate output on the initial startup, e.g. when I first started my PC in the morning.  The rest of the day, it worked fine.

I downgraded to 1.8.1-5 and pinned it.  Haven't had a problem since...

Personally, I think they have some regressions going on -- you know, they patch 10 bugs and 2-3 old bugs crop up again?!?!?

But, that's just a hunch...  :)

---

### Post by Quackers on 2011-12-20
Thanks VinDSL, I was thinking along those lines. Wasn't there a new conkyForecast lately too? I can't remember for sure.

---

### Post by VinDSL on 2011-12-20
> **Quackers said:**
> Wasn't there a new conkyForecast lately too? I can't remember for sure.
Yeah, but I think M just made it possible to use a data feed other than weather.com.

AFAIK, he didn't change the core program files.

---

### Post by Quackers on 2011-12-20
Ok thanks Vin, I'll revert to the previous conky :-)

---

### Post by VinDSL on 2011-12-20
> **Quackers said:**
> Ok thanks Vin, I'll revert to the previous conky :-)
Yeah, give that a try.

If it still doesn't work, you can go from there...

---

### Post by Quackers on 2011-12-20
Well, I downgraded to 1.8.1-5 and all was well again :-)
Then I tried something else and things didn't go well :-(
Now I can't downgrade again. It just breaks 1.8.1-6 which is still showing as installed. 
I guess I'll start again :-)

---

### Post by Quackers on 2011-12-20
It all seems odd to my small brain.
I removed conky and conky-all (1.8.1-6) then manually installed 
conky-cli_1.8.1-5_amd64.deb
and
conky-std_1.8.1-5_amd64.deb
and conky fired right up.
On restart the automatic startup script works and conky displays ok :-)

However, in synaptic conky shows as not being installed at all! That doesn't look right, but at least it's working now :-)  :confused:

---

### Post by philinux on 2011-12-20
Just updated via chroot and booted in and conky fine here.

---

### Post by Quackers on 2011-12-20
> **philinux said:**
> Just updated via chroot and booted in and conky fine here.

Interesting.
Was conky-all removed during the update?
Thanks.

---

### Post by philinux on 2011-12-20
> **Quackers said:**
> Interesting.
Was conky-all removed during the update?
Thanks.

Nothing removed at all.

---

### Post by Quackers on 2011-12-20
Thanks. Curiouser and curiouser!
It could be a gnome-shell thing, perhaps?

---

