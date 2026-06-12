---
title: "Over Built"
date: 2023-06-18
forum: The Cafe
---

### Post by kinddolphin8827 on 2023-06-18
Preceding my relocation to Washington state I purchased a new old stock HP Z420 Workstation. My father and mother criticized me for  buying a "over built" machine, below are the  specifications.

OS: Red Hat Enterprise Linux 8.8 (Ootpa) x86_64
HP Z420 Workstation 
Intel Xeon E5-1603 0 (4) @ 2.800GHz 
Memory: 2721MiB / 15689MiB 
GPU: AMD ATI Radeon HD 5000/6000/7350/8350 Series

---

### Post by ian-weisser on 2023-06-18
Remember to lift it with your knees, not with your back.

---

### Post by kostkon on 2023-06-18
It may look "over built" to them, but I reckon it's been skipping leg day for the last 10 years.

---

### Post by coffeecat on 2023-06-18
@flporter88, what is your question?

---

### Post by kinddolphin8827 on 2023-06-19
I was wondering If people taught that the system that I'm currently using as my personal Daily-driver is over-built. This comes from a deep-seated and some may see it as me falling victim  to an others beliefs in this case that other person is my own father. I've  always thought of myself as a lesser person for both the fact that I'm not in the "99%" of daily-computer users of which I've long considered myself to not only be among the 1% of  computer users that culturally want to use their computers  and don't wont big technology analyzing the hell out of their every click.  

My question to the community as a whole is, do you think that I've over built my system for a "daily-driver"?  Of course I can  also understand where my fathers point lays, however I also feel like I'm being judged by my father  because I don't conform to the neat little box  of being a conformist computer user as it pertains to using Ma Cos X or Win tel rather than a "server operating system" I believe that I should  have the right to use my computer to do stuff as I please and use what ever operating system  use on my own machine.

---

### Post by aljames2 on 2023-06-19
“Overbuilt” is vague.  To do what?  That processor is about 11years old so it is not comparable to many newer CPUs.  But, you can still do a lot with an older computer, depends on what you want to accomplish.  “Server” usually means headless, hosting other guests in virtual machines perhaps.  However, you refer to this as you daily driver, so that implies you plan to use it as your everyday desktop either via bare metal or in a VM.  4 cores is not much for virtualization but still possible to a point.  Nothing at all wrong with learning Linux and all it has to offer.  Linux can run on servers and desktops.  Nowadays it runs well on even very new hardware.  If you pursue it in earnest and understand there is a learning curve, you may find you enjoy it.

---

### Post by ian-weisser on 2023-06-19
A family dispute, despite the fig-leaf of a technical question, does not seem like a question we can meaningfully help with. The actual technical answer won't matter to resolving the dispute.

Healthy families don't escalate minor opinions to the point of seeking outside opinions from the internet on minor matters. Consider that your family relationships might be less stressful and more rewarding with a bit of professional outside assistance (whom we are not). Wouldn't a happy, supportive family be nice?

---

### Post by coffeecat on 2023-06-19
Perhaps I'm missing something, but I don't even see the fig-leaf of a technical question. The strapline for the Hardware subforum, in which this thread was originally posted, reads:

> Problems getting your hardware to work with Ubuntu? Post your questions here.

I think this discussion is better suited to *The Cafe* to which I've moved this thread.

@flporter88, if you need specific technical support rather than moral support for the combination of that workstation and Ubuntu (or an official flavour), you are very welcome to start a new thread in an appropriate support sub-forum.

---

### Post by TheFu on 2023-06-19
Which version of Ubuntu is being run?  This was posted to an Ubuntu sub-forum, not to chat or "Other/OS" sub-forums.

Also, overbuilt is subjective.  It depends on what you do with it.

> OS: Red Hat Enterprise Linux 8.8 (Ootpa) x86_64
HP Z420 Workstation
Intel Xeon E5-1603 0 (4) @ 2.800GHz
Memory: 2721MiB / 15689MiB
GPU: AMD ATI Radeon HD 5000/6000/7350/8350 Series 
I'd never get an HP.  I've had bad experiences with their PC hardware on Linux. Both for desktops and servers.  Some of enterprise servers have very specific, odd, Linux requirements and only work for a few LTS releases.  Why that is, I don't know.

That Xeon E5-1603 is far from powerful.  But does appear to use at least 2x more electricity than recent generation (2015 and later) CPUs. If you aren't paying for power, that might not matter.  I upgraded a Core i7 to a Ryzen a few years ago and the lower power costs alone paid back the cost of the new system in about 2 yrs. That Xeon has a passmark of just 3400 which is pretty low for a "server-class" system. There are Chromebooks with higher passmarks.  A $100 CPU these days will have a passmark over 16000.

16G of RAM is fine for most people not doing Java development. 8G is the new "minimal" RAM amount for a daily use desktop.  I have a laptop with a Core i5-8250U CPU (5800 passmarks) with 8GB of RAM from 2018. Does everything I want.

I have a Radeon 5450 from 2012. It doesn't do h.265 decoding and never will.  If you don't watch or edit videos that doesn't matter.  I suspect the h.264 vcodec capabilities are limited too.

I think there are very capable systems for $100 that would be at least 2x faster. Without knowing the specifics of the cost and proposed use, there's no way to know if this system is a deal and/or overbuilt.  About 3 yrs ago, I sold a Core i7 (1st gen) to a friend for $30 which was about 30 % slower than this Xeon.

Saw a used Acer Aspire XC Desktop: i3-10105, 8GB DDR4, 256GB SSD for** $140** yesterday. Not a powerhouse, but at 8700 passmarks [https://www.cpubenchmark.net/cpu.php?cpu=Intel+Core+i3-10105+%40+3.70GHz&id=4259](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Core+i3-10105+%40+3.70GHz&id=4259) , more than 2x faster than the Xeon. I'd trade a 1st-gen Xeon for a 10th-gen Core i3 any day of the week if just because it uses half the power. Being 2.5x faster is just a bonus.  All the other aspects of the system will be less expensive, easier to replace and have a longer service life than an old Xeon.

In short, old servers are seldom the best option.

---

### Post by CharlesA on 2023-06-22
> **TheFu said:**
> 
That Xeon E5-1603 is far from powerful.  But does appear to use at least 2x more electricity that regent generation (2015 and later) CPUs. If you aren't paying for power, that might not matter.  I upgrades a Core i7 to a Ryzen a few years ago and the lower power costs alone paid back the cost of the new system in about 2 yrs. That Xeon has a passmark of just 3400 which is pretty low. There are Chromebooks with higher passmarks.  A $100 CPU these days will have a passmark over 16000.

This is so true.

While my use case is different - server vs desktop, I went from a Xeon E3-1270 V2 on an x8 Supermicro mobo to a Xeon E-2336 on an x12 Supermicro mobo and the power consumption dropped a bit for me.

Granted, this was a massive upgrade and quite expensive, I went from a 6K passmark to a 16K passmark while lowering the amount of energy I use with everything else the same.

@OP: I do not believe this system to be "overbuilt" but you probably could have gotten something better for around the same amount of money, depending on the market in your area.

Since you did not mention what you are using it with, I cannot give you any more feedback on it.

---

### Post by exploder on 2023-06-25
I have a few Dell's in the closet with dual Xeon procesors, they are still very capable systems but they are like picking up a cinder block! They consume a fair amount of energy for sure but then look how much power new graphics cards use! Overbuilt, maybe, but they can really hold up and maintenance is very easy. RAM for these is really cheap so I maxed a couple of them out. You can run a lot of VM's on one of these effortlessly! I picked all mine up on eBay for $100.00 - $150.00. Cost all of $8.00 to add a second processor to one of them, lol.

Having something overbuilt is too your advantage. The HP Z420 Workstation has a good reputation for reliability and your choice of OS should have all your bases covered in my opinion. Your system still has an inexpensive upgrade path if you are ever inclined to do so. "New Old Stock" is good. I would consider new thermal paste on the processor because it is likely dried up from age. I would do the same with the graphics card also. At the least, look at the temps with lm-sensors to make sure they are not too high. Better safe than sorry!

Overbuilt in this case is more, built to last.

---

### Post by agentl074 on 2023-06-25
I wouldn't worry... overbuilt is a good thing -- even if it was overbuilt a few years ago lol. 

On the latest major distributions -- especially Ubuntu -- you should be just fine. Interestingly, on one of my former machines using Linux Mint 20.3, I had to get a newer kernel in order for the GPU to work, but even then, it wasn't quite right. I switched to Ubuntu 22.04, and all was well. 

Machines are picky, but Canonical has done a great job at making most things work -- at least using 22.04+ LTS.

---

