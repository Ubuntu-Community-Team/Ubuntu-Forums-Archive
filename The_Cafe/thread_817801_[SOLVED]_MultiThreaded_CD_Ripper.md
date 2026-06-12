---
title: "[SOLVED] MultiThreaded CD Ripper?"
date: 2008-06-03
forum: The Cafe
---

### Post by BassKozz on 2008-06-03
Are there any multi-threaded CD Rippers available for Ubuntu (Linux)?
I noticed that "Sound Juicer" (The ripper I've been using) isn't multi-threaded, and I was wondering if there is another CD ripper that is multi-threaded, or if it's just a wasted pursuit due to IO constraints?
Thanks in advance,
-BassKozz

---

### Post by FuturePilot on 2008-06-04
Grip allows you to specify the number of CPUs to use.

---

### Post by BassKozz on 2008-06-04
Thanks **FuturePilot**,
Any comment on whether or not multi-threading cd-ripping makes a difference?
Due to possible IO constraints of the CD Reader? My CD Reader has a 48x read speed.
 
**_EDIT_**: Scratch the above, I got confused between Ripping & Encoding... Obviously Multi-Threading will help in the Encoding Department but probably won't do anything for Ripping...

Also, I just ran a comparison of Grip vs. Sound Juicer, and Sound Juicer seems to have ripped & encoded **MUCH** faster then Grip, but this might be due to the "Paranoia" feature of Grip.  I noticed Grip was ripping at between 0~1x while Sound Juicer was ripping between 10~15x.

Now to check the quality of the two rip/encodes, any idea's on what app I can use to compare rip/encoded quality?

---

### Post by FuturePilot on 2008-06-04
You're welcome. :)

And yes you got it right. Multithreading won't help with ripping because you'll always be limited by your CD ROM's speed. But it will definitely help with the encoding speed.

Yes Grip might encode a bit slower because of the Paranoia. But I've found that Grip gives much better quality. Sound Juicer always gave me terrible encodings. I would have so many pops and skips and scratches, but with Grip I get a perfect encoding every time. :)

---

### Post by toupeiro on 2008-06-04
> **FuturePilot said:**
> Grip allows you to specify the number of CPUs to use.

:KS:KS:KS:KS:KS:KS:KS:KS

Thank you for this

---

### Post by BassKozz on 2008-06-04
I can't stand the extremely slow ripping speed 0.0x~1.5x is horribly slow... is there a way to speed it up w/ out sacrificing the "Paranoid" ripping feature?

Also I am not an audiophile, so it might be tough for me to spot pops & hisses that Sound Juicer might make that Grip otherwise wouldn't, are there any applications I can use to compare the quality of the two encodes (side-by-side) so I don't have to do the dirty work of analyzing the two encodes?

Also I noticed Grip defaults to Ogg 128kbs while Sound Juicer defaults to Ogg 160kbs, should I set Grip to 160 also or is 128kbs sufficient?

---

### Post by Lostincyberspace on 2008-06-04
You need to set the nice value to like -20 so it will go really fast. Also tell it to use all the cpus.

take a look [here]("http://nostatic.org/grip/doc/index.html") there are some more tips in the ripping and rip config sections.

---

### Post by BassKozz on 2008-06-04
> **Lostincyberspace said:**
> You need to set the nice value to like -20 so it will go really fast. Also tell it to use all the cpus.

take a look [here]("http://nostatic.org/grip/doc/index.html") there are some more tips in the ripping and rip config sections.
Thanks Lostincyberspace,
I bumped the priority to nice -20 and set it to use all 4 cores on my overclocked Q6600 (3.3ghz) and its still not going above 2x, I suppose the "Paranoia" feature must take alot out of it... I'll keep tweaking with settings and see if I can get it to go a bit faster...

Now does anyone know of any applications I can use in Linux (Ubuntu) or Windows to compare the two rip/encodes of Grip & Sound Juicer side-by-side to see which one provides better quality rip/encodes?:confused:

---

### Post by BassKozz on 2008-06-04
This thread is being marked as SOLVED, and follow up question has been moved here: [Encoding Quality - Sound Juicer vs. Grip (CDParanoia)]("http://ubuntuforums.org/showthread.php?t=818355")

Thanks for the help everyone :D

---

