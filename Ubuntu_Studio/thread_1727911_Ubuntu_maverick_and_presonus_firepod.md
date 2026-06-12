---
title: "Ubuntu maverick and presonus firepod"
date: 2011-04-13
forum: Ubuntu Studio
---

### Post by Torque313 on 2011-04-13
Ok here's the deal....

A while back i installed ubuntu studio and had my system running with the firepod using ardour and it was super low latency and sweet. I had to rebuild a new studio computer and was out of linux for a while but now i need to fire it up again. The problem is that i can't remember how i got it to run the last time and none of the tutorials i found are doing me any good, maybe i missed something.

Here's what i need in order to make this thing usable again:

I need it to run on plain jane ubuntu maverick ( i just like the look and feel of it way better than ubuntu studio and i know it can be done)

I would like a way to be able to use the firepod as the main soundcard for everything not just a mutitracker

If i can get it to work i would be happy to compile all the steps in a very straight forward tutorial so you guys don't have noobs like me blowing up the forums for this stuff all the time.

I would really like to get this working so i can show it off to some of my friends in the electronic music buisness as a decent alternative to their pro tools, cubase and ableton live setups. I love everything about ubuntu except what a pain in the *** stuff like this can be. There are a ton of firewire setups out there that can be extremely useful in a system like this.

Any help you guys can give me would not be forgotten and i would be glad to talk about ubuntu as a great alternative in magazine and web interviews to help the cause because i really do believe that open source is the future of audio production.

---

### Post by kayosiii on 2011-04-13
Maverick has a new firewire stack and some issues with default compilation and apps getting realtime privelages.
The first thing you want to try is the lowlatency version of the kernel. I also found I had better luck with jackdbus than straight jack but that might be coincidental. 
If that fails you might be able to blacklist the new firewire stack and unblacklist the old one (not sure on how to do that). Possibly switch back to jack1 (if maverick is on jack2 - not sure).

Otherwise I suggest moving forward to Natty (working well for me here) or back to Lucid (or one of the derivatives like KXStudio).

---

### Post by AutoStatic on 2011-04-13
Hello Torque313,

> **Torque313 said:**
> I need it to run on plain jane ubuntu maverick ( i just like the look and feel of it way better than ubuntu studio and i know it can be done)That's perfectly possible, check here: [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

> **Torque313 said:**
> I would like a way to be able to use the firepod as the main soundcard for everything not just a mutitrackerGood luck on this one, this is probably not going to work because neither JACK nor the FirePod are designed for normal desktop usage.

> **Torque313 said:**
> I would really like to get this working so i can show it off to some of my friends in the electronic music buisness as a decent alternative to their pro tools, cubase and ableton live setups.This is not such a good starting point imho. It will lead to disappointment and does no good for the cause of Ubuntu.

> **Torque313 said:**
> Any help you guys can give me would not be forgotten and i would be glad to talk about ubuntu as a great alternative in magazine and web interviews to help the cause because i really do believe that open source is the future of audio production.Which magazines would this be about? And what web interviews?

Best,

Jeremy

---

### Post by kayosiii on 2011-04-13
> Quote:
[I]Originally Posted by Torque313  
I would like a way to be able to use the firepod as the main soundcard for everything not just a mutitracker[/I]
Good luck on this one, this is probably not going to work because neither JACK nor the FirePod are designed for normal desktop usage.

This actually works reasonably well. At least everything that can go through either PulseAudio or Phonon can now be configured to run through jack. In practice this means I get audio for everything except flash and some games.

Pulse Audio needed a little hacking to get working properly.

---

### Post by AutoStatic on 2011-04-13
> **kayosiii said:**
> In practice this means I get audio for everything except flash and some games.So it doesn't fully work ;)

Best,

Jeremy

---

### Post by trulan on 2011-04-13
Hey, I used to use my firepod as my only soundcard when I ran Windows!  Boy those were the days...All those countless hours trying to hunt down pops and clicks in my recordings and clean them up with Audacity...At least Ubuntu never had me wishing I was still using 4-track tapes.

I did actually get things running stably with the firepod as my main soundcard on Linux using thorgal's [alsa-loopback setup](alsa.opensrc.org/Jack_and_Loopback_device_as_Alsa-to-Jack_bridge), and yes, everything was working.  (As in, using a mic/headphones through the firepod, make a call with Skype and record it in Ardour.  Or feed the output of Ardour into Skype - you get the picture.)  That setup took way too much CPU power though to be practical, and I never actually found a real use for it.  It was basically just a toy, but it worked.

I did try the pulse-jack bridge setup too but found that frustrating and unstable, to put it mildly.  Not fun at all.

---

