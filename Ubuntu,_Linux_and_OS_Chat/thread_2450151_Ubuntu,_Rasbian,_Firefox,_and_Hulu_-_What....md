---
title: "Ubuntu, Rasbian, Firefox, and Hulu - What..."
date: 2020-09-08
forum: Ubuntu, Linux and OS Chat
---

### Post by captclearleft2 on 2020-09-08
I got so excited when I was able to get Hulu to work in Firefox on my Ubuntu 20.04.1 LTS  Desktop - WooHoo...  I immediately went out and got a Raspberry Pi 4, loaded up the common Raspbian, launched Hulu in Firefox, and 'Thud' - It still doesn't support it.  Im guessing its a flash issue, and a Firefox version issue (That is beyond my understanding)...  But...


Can someone explain the difference between the Firefox I am running in Ubuntu and the Raspbian version of Firefox - OR why Hulu now works on Ubuntu, and not Raspbian?

Thanks!!!

---

### Post by TheFu on 2020-09-08
They are compiled for completely different CPUs.  Most desktops are using the Intel x64 instruction set while most Raspberry Pis are using an ARM 32-bit instruction set.  The Pi4 has a 64-bit OS if you loaded 64-bit Ubuntu, but I don't know if raspian is 64 or 32-bit. Because the pi4 has a 64-bit ARM CPU, means it can run either a 32-bit or 64-bit OS, but which you loaded will determine the version of firefox loaded. Compiled programs can't be copied between these do very different systems.

And since hulu is heavy into DRM, they will require video drivers that support some minimal level of DRM in the drivers and in the hardware.

When I got my first raspberry pis years ago, I hoped DRM streaming sites would work, but wasn't supprised when they didn't.  After a few weeks of screwing around, knowing that at least quarterly, the sites would update their DRM to combat all the Linux hackers, I just bought a Roku which is used for watching DRM streams. For everything else, I use OSMC on either a Raspberry Pi v2 or v3.

I've always has slight issues with video in Firefox, but that's probably because firefox is my daily driver browser, used for trusted sites only.  For untrusted sites or any sites that require massive click tracking to work, I use a different browser, running inside a sandbox, that isn't allowed to write anything to storage, ever. Every time I start up those other browsers inside that sandbox, it is like the very first time it was run with all the defaults.

Flash is deal. If hulu is still using it, they will learn quickly how dead it is in just a few months when Windows browsers end it.

Since this was posted to a _chat_ subforum, not a _help_ forum, I assume you don't really want someone with any solutions. I don't have any answer to make hulu work on raspberry pi hardware. Sorry.

---

### Post by captclearleft2 on 2020-09-08
Thank You, That is what I was looking for.  Just a little knowledge on the subject, and maybe some future insight - All of which you provided.  Thanks.  I know there are some Rpi hacks to kinda get it to work, but ... eh...  I will just use my Ubuntu for now.

---

