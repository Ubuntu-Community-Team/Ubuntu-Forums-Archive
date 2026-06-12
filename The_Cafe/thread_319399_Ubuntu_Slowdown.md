---
title: "Ubuntu Slowdown?"
date: 2006-12-15
forum: The Cafe
---

### Post by ahaslam on 2006-12-15
Why does Linux get slower the more you use it?

After installing applications, boot & app start times noticeably increase, the more I install & the longer I use the PC, the slower it gets. It's a significant slowdown, since the release of Dapper my laptops performance has halved, despite many optimisations from 'make ubuntu run like arch' (see sig).

It's not only Ubuntu, in the short time that I've used Zenwalk 4, it has also been apparent.

Has anyone else noticed this, any comments?

Tony.

---

### Post by DC@DR on 2006-12-15
Never encountered this problem before. I got a lot of stuffs installed in my laptops, from Eclipse, Anjuta, Blender 3D, Google Earth, Firefox 2.0 to Wine with WoW, Dreamweaver, etc....I still feel like my Dapper freshly installed, it works like a charm...But of course, Your Mileage May Vary ...

---

### Post by d3v1ant_0n3 on 2006-12-15
Very odd suggestion, but are the heatsinks/fans/airways in your laptop clean?

I have to blow the insides of my laptop out fairly regularly with an air can- when my laptop gets too hot, everything slows to a crawl or just plain hangs.

---

### Post by mcduck on 2006-12-15
no, it doesn't get any slower on my machines.

---

### Post by lyceum on 2006-12-15
> **Anthony Haslam said:**
> Why does Linux get slower the more you use it?

After installing applications, boot & app start times noticeably increase, the more I install & the longer I use the PC, the slower it gets. It's a significant slowdown, since the release of Dapper my laptops performance has halved, despite many optimisations from 'make ubuntu run like arch' (see sig).

It's not only Ubuntu, in the short time that I've used Zenwalk 4, it has also been apparent.

Has anyone else noticed this, any comments?

Tony.

The key word here is not the length of use, it is the more you install. Windows does the same thing. I have found that the more you have on the hard drive, the slower a PC will go. You can do things to spead it up, I have added fans and memory to help, but once you get the hard drive half way full, it really seems to loose steam. I could be wrong, but that is my experiance.

---

### Post by ahaslam on 2006-12-15
> **d3v1ant_0n3 said:**
> Very odd suggestion, but are the heatsinks/fans/airways in your laptop clean?

I have to blow the insides of my laptop out fairly regularly with an air can- when my laptop gets too hot, everything slows to a crawl or just plain hangs.

Clean as a whistle, it rarely leaves my desk & doesn't get too hot. 

It has seriously slowed down though. I did an Edgy server install on another partition & installed mostly just X & Xfce, it was way slower than what a full Dapper was upon release :-k 

Judging by the other replys, I guess something may be deteriorating in my crappy lappy :-? 

Tony.

PS. I'm currently typing from Zenwalk running Openbox, even this is slightly slower than what Dapper once was :-| 

Tony.

---

### Post by smoker on 2006-12-15
yeah, i think i would check the hardware, is your swap large enough, do a check on your hard drive and memory, and check it's getting all the power it needs, try a different power adapter and battery if you can.

---

### Post by ahaslam on 2006-12-15
> **lyceum said:**
> The key word here is not the length of use, it is the more you install. Windows does the same thing. I have found that the more you have on the hard drive, the slower a PC will go. You can do things to spead it up, I have added fans and memory to help, but once you get the hard drive half way full, it really seems to loose steam. I could be wrong, but that is my experiance.

That's what I was originally thinking, but it shouldn't half the performance. My disk is about 75% full with 2 distro's (ubuntu & zenwalk), spanning over 5 partitions. 

With little fragmentation & separate home/swap/root partitions, as long is there is free space, surely it shouldn't make that much difference [-( 

Tony.

---

### Post by ahaslam on 2006-12-15
> **smoker said:**
> yeah, i think i would check the hardware, is your swap large enough, do a check on your hard drive and memory, and check it's getting all the power it needs, try a different power adapter and battery if you can.

My swap is twice that of my RAM 
The usual check on every 30th mount never throws up any errors.
Regards the memory, would that mem thing in the grub menu suffice (I'll try it anyway)?
Unfortunately, I don't know anyone with the same piece of junk to swap batteries & leads over.

Cheers ;)

---

### Post by ahaslam on 2006-12-15
It seems that I have bad RAM, memtest86 gives an error on test 5 @ 00017ea0f18 - 382MB.

:(

---

### Post by dbbolton on 2006-12-15
habituation.

---

### Post by ahaslam on 2006-12-15
Does it not matter? 

Tony.

---

### Post by ahaslam on 2006-12-19
OK, I'd like some clarification if possible ;)

I've been told (by a windows power user) that if there's an error at a certain point in the memory, the computer will only use up to the error but still recognise the full amount. I've done a quick google, unable find confirmation but it makes sense, as it's now swapping  more frequently.

Is he correct, have I now got only 382MB of RAM (318 after my graphics)?

Cheers.

---

### Post by hopstah on 2006-12-22
i once had a bet section in my memory, and was told that you can actually tell linux to ignore just that part of your memory and you'd be fine.  but for me, it was in MB 1024 of 1024, so I rarely needed that physical real-estate and haven't researched it.  but maybe that will help you out.

---

### Post by ahaslam on 2006-12-22
Yeah, I believe that there's a 'BAD RAM' kernel patch. 

Since posting, I've read that Athlons often report false errors on test 5. Since I use a Sempron that is practically the same, there may be no problem at all. Especially as I've had no stability issues, but it's so slow atm, I'm using Zenwalk with Openbox.  Ubuntu will have to wait until I upgrade my computer next month - which will also solve any possible memory problem ;)

Tony.

---

