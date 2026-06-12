---
title: "Minimum needed harddisk-space Ubuntu 9.04"
date: 2009-09-16
forum: Testimonials &amp; Experiences
---

### Post by Cadilac on 2009-09-16
:KS

[I][B]Hi there !

I just wonder if someone please could tell me the minimum-demand of harddisk-space for Ununtu 9.04, when I want to make a dual-boot with Windows XP or Windows Vista?

:confused:

I mean, Ubuntu 9.04 shall work as best as possible, but still not take up more needed space then possible, to work 101 % perfect.

As I, so far, have no plans of downloading a lot of stuff in Unbutu.
Well, perhaps some programmes, but no large pictures and music.

Maybe later on, when I am more used to Ubuntu.

Am still an newbite, an absolutely beginner.

:guitar:

Greetings to you from Cadilac in Copenhagen, Denmark
[/B][/I]

---

### Post by gordintoronto on 2009-09-16
I have installed Ubuntu on a 10 GB drive.  You can go smaller, but that's pushing things.

Bear in mind that you need a swap file, and the suggested size is double your memory.

---

### Post by Joshua Lückers on 2009-09-16
Ubuntu has a nice list with [system requirements](https://help.ubuntu.com/community/Installation/SystemRequirements).

---

### Post by Sef on 2009-09-16
> I have installed Ubuntu on a 10 GB drive. You can go smaller, but that's pushing things.

8 - 10 GB is as low you should go.

> Bear in mind that you need a swap file, and the suggested size is double your memory. 

That is not correct.  You should not make swap more than 1 GB.  If you do cpu intensive activities, then 2 GB is ok, but that is the maximum swap, you should have.   More than that, you need more ram.

---

### Post by armandh on 2009-09-16
on my wife's lap top I used the vista partition tool to reduce the main partition by 10Gb. then I installed Ubuntu selecting "use largest unpartitioned space" It did the rest including the swap and grub. 

on my mini9 it was a bit more complex I wiped dell-buntu and installed XP to half the 16G drive or a bit under 8Gb then the same Install to the largest unpartitioned space option for OOTB  ubuntu. [not dellbuntu] a 4 gig SD card for file storage.

the ubuntu only uses a bit over 3 Gb

---

### Post by Marflus on 2009-09-17
When I first installed Ubuntu to try it out through Wubi, I had no problems running it with 15Gb of space available. I can imagine 10 or even less would run fine though, especially since you're not going to be saving big files in that partition.

> That is not correct. You should not make swap more than 1 GB. If you do cpu intensive activities, then 2 GB is ok, but that is the maximum swap, you should have. More than that, you need more ram.

Really? From what I read in the wiki it said 1-2 times your RAM size was the best swap size to aim for. Maybe I should make mine a little smaller...

---

### Post by Joshua Lückers on 2009-09-17
> **Marflus said:**
> Really? From what I read in the wiki it said 1-2 times your RAM size was the best swap size to aim for. Maybe I should make mine a little smaller...

1-2 times your RAM is a good amount for swap when having not so much RAM (less then 1GB). If you have enough RAM there is no need for a huge swap file (unless you wanna hibernate your system, then your swap should be the same size as your RAM (a little bit more is better).

---

