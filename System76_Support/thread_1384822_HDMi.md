---
title: "HDMi?"
date: 2010-01-18
forum: System76 Support
---

### Post by wrender on 2010-01-18
I have a Serp 5 and I was wondering if there is a way to enable sound to pass through the hdmi cable to a HDMi enabled tv. The video works flawlessly! However I can't seem to figure out the audio bit.

Any ideas?

ps. I have a geforce 9800M GTS

---

### Post by jdb on 2010-01-18
> **wrender said:**
> I have a Serp 5 and I was wondering if there is a way to enable sound to pass through the hdmi cable to a HDMi enabled tv. The video works flawlessly! However I can't seem to figure out the audio bit.

Any ideas?

ps. I have a geforce 9800M GTS

I think it's a driver problem, hdmi isn't quite ready for prime time in Linux.

jdb

---

### Post by wrender on 2010-01-19
It has been a little over a year and 2 versions of ubuntu later... everything on my laptop pretty much works without system 76 drivers and the system over all runs better.

So I figured I would check up on the whole hdmi situation hoping magical fairies got to it aswell or if there were any rumors. lol :P

---

### Post by Lee_Machine on 2010-01-19
Audio over HDMI works just fine on Ubuntu 9.10

Once you get the video configured go

System >> Preference >>  Sound

On the Hardware tab you will see Profile

Click that and choose Digital Stereo (HDMI) Output

Now it should work, you may have to change a setting in your video player.

Yeah, it's not as user friendly as other OS's, but you have more control. 


Audio over HDMI has been a probelm for a few years now, but it works. :D

---

### Post by miniyak on 2010-01-19
> **jdb said:**
> I think it's a driver problem, hdmi isn't quite ready for prime time in Linux.

jdb

hdmi isn't ready for the prime time period, and because of version changes and copy protection i doubt it ever will be.

a couple of problems ive found

In linux: 
panp5 + old version hdmi set = fail
panp5 + new version hdmi set or hdmi to dvi = ok (once you figure it out)
Plus for some reason even on newer sets overscan seems to also ruin the whole experience.

In general:
Blu ray players seem to rarely come w/ the cable... (try explaining to the lesser informed that they need a new cable if they can see the picture...)
It cost $50 for a hdmi cable at the store and $5 online (another fun thing to explain to the lesser informed)
hdmi input on a pc? good luck w/ that

well I could keep going.... but ill just sum it up w/, hdmi = disappointing

---

### Post by jdb on 2010-01-19
> **miniyak said:**
> hdmi isn't ready for the prime time period, and because of version changes and copy protection i doubt it ever will be.

a couple of problems ive found

In linux: 
panp5 + old version hdmi set = fail
panp5 + new version hdmi set or hdmi to dvi = ok (once you figure it out)
Plus for some reason even on newer sets overscan seems to also ruin the whole experience.

In general:
Blu ray players seem to rarely come w/ the cable... (try explaining to the lesser informed that they need a new cable if they can see the picture...)
It cost $50 for a hdmi cable at the store and $5 online (another fun thing to explain to the lesser informed)
hdmi input on a pc? good luck w/ that

well I could keep going.... but ill just sum it up w/, hdmi = disappointing

I don't mix Linux & HDMI :)

I connect my digital tuner to my monitor with an HDMI cable.
I connect the audio from the tuner straight to my stereo.
My computer connects to my monitor with a VGA cable.

If I want to compute while I'm watching TV, that's what my laptop is for :lolflag:


jdb

---

### Post by wrender on 2010-01-19
I am running Kubuntu 9.10 with all the latest updates...and backports.

I can't seem to figure out how to get the audio to work.

I found under Kmix there are channels relating to IEC958... I enabled them and made sure there was volume. However no luck still... sigh.

---

