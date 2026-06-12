---
title: "When did system76 switch to 64 bit Ubuntu?"
date: 2008-01-30
forum: System76 Support
---

### Post by user1397 on 2008-01-30
I see now that all system76 laptops and desktops come with ubuntu 7.10 64 bit by default.

when did this happen, and why?

---

### Post by Aug Leopold on 2008-01-30
Yeah, this is the first I've heard anything about this as well. What's the deal Tom? It would have been cool to have an announcement that this was happening and that system76 is now supporting 64-bit. Should system76ers start switching to 64-bit now? Also, I noticed that now all the wi-fi adapters have been switched to draft-n, I would assume the Intel 4965. Would I be right? I'm personally glad I bought my computer earlier as I'm not touching an 802.11n-anything until the standard is finalized.

---

### Post by Odd-rationale on 2008-01-30
I read that 64-bit on hardy is going to be pretty good:

[http://www.outflux.net/blog/archives/2008/01/15/full-aslr-in-hardy/](http://www.outflux.net/blog/archives/2008/01/15/full-aslr-in-hardy/)

---

### Post by user1397 on 2008-01-30
any input, crichell?

---

### Post by imhavoc on 2008-01-30
That is interesting!

Questions:
 - Is the new BIOS required/preferred for running 64-bit Ubuntu? (or will the BIOS that shipped with the original Daru2's good to go? I know I'm limited to 2 GB RAM without the update.)
 - Are there any issues/pitfalls that we should be aware of if we chose to hazard the migration to 64-bit?
 - Will the 64-bit version help with some of the odd system pauses and glitches we see with the dual core chips? Or is that just gonna be something we have to continue to live with for the near future?

Looking forward to the official S76 replies.

---

### Post by thomasaaron on 2008-01-31
Yeah, how do you like that!

That's a bunch of questions. Here we go:

1. We switched to Ubuntu recently (within the last few weeks).
2. It works darn good.
3. You don't have to do anything with your BIOS.
4. We are having a lot of success with suspend in 64-bit.
5. 64-bit supports 4GB of RAM 
6. We will be putting out some directions for those who want to switch to 64-bit. But for all of the **CURRENT** line-up, it should be no problem.
7. For **OLDER** System76 computers, we're NOT done testing yet. If you make the leap, we might not have all of the answers to any problems that might occur (though I suspect there will be very few of them).
8. There will probably be some annoucements forthcoming in various venues.

I think that covers everything.

---

### Post by Gonzell on 2008-01-31
The last time I tried 64bit (which was quite awhile ago) I had some issues, but it wasn't a System76 machine. The one issue that sticks out was Flash. Will it be easy to get flash working on a System76?

---

### Post by palintheus on 2008-01-31
Just installed Hardy Alpha 3 on my daru2 and flash was as easy as installing it in Gutsy

---

### Post by user1397 on 2008-01-31
> **Gonzell said:**
> The last time I tried 64bit (which was quite awhile ago) I had some issues, but it wasn't a System76 machine. The one issue that sticks out was Flash. Will it be easy to get flash working on a System76?if you follow this guide, it is incredibly easy to get flash working on 64 bit ubuntu and 64 bit firefox: [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

---

### Post by Gonzell on 2008-02-01
That's great to hear! I actually just ordered my laptop yesterday, so I guess I'll be keeping 64bit Ubuntu on it.

> 4. We are having a lot of success with suspend in 64-bit.

You said you are having a lot more success....what does this exactly mean? Does the suspend work for the laptop or not? lol
I'd really like to be able to just shut my laptop closed and then open it up later on and have it resume perfect...how well does this work?

Thanks

---

### Post by thomasaaron on 2008-02-01
It's much better with 64-bit.

Also on the DarU2, we now have S1 suspend!!!

---

### Post by DomIncollingo on 2008-02-01
How do you deal with the Java plug-in for Firefox?  I understand that there still is no 64-bit Java plugin.

---

### Post by thomasaaron on 2008-02-01
Ah, there's some kind of work-around for it. I'm not sure what it is yet, but Carl's figured it out. I'll be messing with it more next week.

Bump this if you haven't heard from me by Tuesday.

---

### Post by palintheus on 2008-02-01
> **thomasaaron said:**
> Also on the DarU2, we now have S1 suspend!!!

:guitar:

/me reinstalls the Gutsy partition with amd64 Gutsy

---

### Post by DomIncollingo on 2008-02-01
Thanks.  I have a two-month old Serval (which I really love) running 32-bit Gutsy, but I'd really like to upgrade to 64-bit when Hardy is released in a few months.  I'm looking forward to helpful instructions on how to do this.  :)

---

### Post by ewg on 2008-02-02
Sys76 Sable performance
2 GB ddr2
AMD 64x2 Athlon 4600 2.4 GHz
Gusty 7.10

For those of us still on 32 bit. Will we be affected by future updates to the Sys76 drivers? Ubuntu upgrades? Will there be separate ones for 32 bit and 64 bit? Will it be easy for us to move to 64 bit?

Thanks,

---

### Post by thomasaaron on 2008-02-04
We still have a lot of testing to do before I can answer all of those questions.

Ultimately, 64-bit will probably run quite well out of the box on the Sable.
It will not matter to the System76 driver which (32/64) you have on your computer, it would apply the right patches.

---

### Post by Squish on 2008-02-07
Oh boy oh boy oh boy!

Hardy is going to be such a huge release!
Finally it will have a decent video editor - Jahshaka
It will have long term support
and it will have the new xorg, among a ton of other things !

---

### Post by Peneus on 2008-02-08
Hello all,

I have a Daru2 and considering whether I should install Hardy as 64 bit or not. However, I am not really familiar with this. So can someone explain to me what are the advantages and disadvantages of having 64bit system.

Thanks a lot

---

### Post by thomasaaron on 2008-02-08
Well, it's supposed to be faster, taking advantage of the full power of your System76 processor. On the DarU2, it will fix S1 suspend and the screen-dimming bug.

---

### Post by Peneus on 2008-02-08
That sounds nice. But are there any reason not to install 64bit? Can I get all the programs I have in 32bit? 

Thanks.

---

### Post by thomasaaron on 2008-02-08
The only think I've heard of lately is Flash. But I think they've either got that ironed out or have a easy work-around.

---

### Post by user1397 on 2008-02-08
> **Peneus said:**
> That sounds nice. But are there any reason not to install 64bit? Can I get all the programs I have in 32bit? 

Thanks.the easiest work around is here: 
[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

---

### Post by Vadi on 2008-02-09
Just to note, I ordered my serval about a week ago, it arrived today - it's a 64bit Ubuntu, and java (icedtea) & flash worked out of the box. I'm really pleased.

---

