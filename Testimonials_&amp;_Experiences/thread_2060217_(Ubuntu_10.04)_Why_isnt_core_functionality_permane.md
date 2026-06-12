---
title: "(Ubuntu 10.04) Why isnt core functionality permanent?"
date: 2012-09-19
forum: Testimonials &amp; Experiences
---

### Post by geirknappen on 2012-09-19
So I decided to put a dvd into the drive, but ubuntu 10.04 would not recognize it. [This guide]("http://ubuntuguide.org/wiki/Ubuntu:Lucid#DVD_Playback_Capability") worked for me in the past on 10.04, but now it does not. I understand that coding and stuff must be difficult, but I must admit I think such things should work permanently.

---

### Post by MG&amp;TL on 2012-09-19
> **geirknappen said:**
> So I decided to put a dvd into the drive, but ubuntu 10.04 would not recognize it. [This guide]("http://ubuntuguide.org/wiki/Ubuntu:Lucid#DVD_Playback_Capability") worked for me in the past on 10.04, but now it does not. I understand that coding and stuff must be difficult, but I must admit I think such things should work permanently.

In two words: "things break". The problem is that it's very hard to tell when things have broken. You're unlikely to run an entire test of your program if you only corrected a spelling error and accidentally broke DVD support for a release you're not currently using.

The problem with "core functionality" being permanent: define "core functionality". Bootloader? Kernel? Whatever it is that handles the DVD drive (still the kernel, I think). Whatever it is that reads the DVD (libdvdread, I think)? Plays the DVD?

So yeah. IMO, that's why. :)

---

### Post by geirknappen on 2012-09-19
I am not entirely sure if I understood that response. Did you just say: "Stuff stops working because there is a number of things that could cause it to stop working". If thats the case, It may be I who caused the problem by running the update manager, I guess. (I always thought update= improvement)

---

### Post by kostkon on 2012-09-19
Ubuntu doesn't support the playback of encrypted DVDs by default for legal reasons. Try following [this how-to]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs").

---

### Post by MG&amp;TL on 2012-09-19
> **geirknappen said:**
> I am not entirely sure if I understood that response. Did you just say: "Stuff stops working because there is a number of things that could cause it to stop working". If thats the case, It may be I who caused the problem by running the update manager, I guess. (I always thought update= improvement)

Okay, simpler scenario (sorry, probably been out of human contact too long!):

1. Developer finds bug.

2. Developer fixes bug, but inadvertently introduces a new, subtle bug.

3. We get problems like yours with the updates.

---

### Post by QIII on 2012-09-19
> **MG&TL said:**
> Okay, simpler scenario (sorry, probably been out of human contact too long!):

1. Developer finds bug.

2. Developer fixes bug, but inadvertently introduces a new, subtle bug.

3. We get problems like yours with the updates.

The endless cycle, the bane of our lives.

Maybe I should have been a circus clown instead of a software developer.

Sigh.

---

### Post by geirknappen on 2012-09-21
I did not intend to introduce any negativity. I think the responsibility for it to work should not be blamed on one sole developer. Shouldn't there be like at least 2 or 3 persons to revise the planned upgrades? And though not everything works bugfree, a lot of things have been clearly improved through updates. Wireless connection is one of them.

---

### Post by MG&amp;TL on 2012-09-21
> **geirknappen said:**
> I did not intend to introduce any negativity. I think the responsibility for it to work should not be blamed on one sole developer. Shouldn't there be like at least 2 or 3 persons to revise the planned upgrades? And though not everything works bugfree, a lot of things have been clearly improved through updates. Wireless connection is one of them.

Of course you didn't. We didn't mean to either, but we like a moan every once in a while, right QIII? :)

There is of course a patch review process, but inevitably things slip through. If you intend to keep using 10.04 for any serious length of time, I suggest reporting the bug before EOL (April 2013).

Yeah, most of the time we try and fix stuff. ;)

---

### Post by geirknappen on 2012-09-22
> **MG&TL said:**
> If you intend to keep using 10.04 for any serious length of time, I suggest reporting the bug before EOL (April 2013).

Yeah, most of the time we try and fix stuff. ;)

Yeah... I think I will (though I've never done something like that before), unless a obvious distro choice present itself within the year.

---

### Post by vexorian on 2012-09-22
It could be an issue with the DVD drive, you know. A computer I repeaired as work had the exact issue you mention (forgetting the DVD drive) but with windows 7 and a LG drive. Could only fix it after installing another drive.

---

