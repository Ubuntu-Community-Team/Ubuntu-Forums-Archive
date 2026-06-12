---
title: "Ubuntu Frustrating, Me Doing Nothing - Broke On Me."
date: 2010-01-19
forum: Testimonials &amp; Experiences
---

### Post by AlexanderDGreat on 2010-01-19
Hi, this is my original post.

[http://ubuntuforums.org/showthread.php?t=1384993]("http://ubuntuforums.org/showthread.php?t=1384993")

And it's really saddening. I've been friends with Ubuntu for almost 8 months now, and this happened. Usually my problems are desktop related so I can Google search, [COLOR="RoyalBlue"]but why does it have to be hardware? My dvd is 100% OK as you will see in my post. And there's a bug that my hard disk has bad sectors, but I think the kernel update did this[/COLOR]. Forgive me if I'm wrong. Now this can be one of Ubuntu's deal breaker for me. What should I do? I've seen my life passed by constantly doing the laborious job of Googling all the time because of these bugs. Seriously, I'm losing my confidence in Ubuntu. Before, I always recommend it to my friends, but now, I think I'll keep my mouth shut.

---

### Post by Methuselah on 2010-01-20
How do you know the hardware is OK.
Do you dual boot with windows sand find it working there?

---

### Post by AlexanderDGreat on 2010-01-20
Sadly, yes. I installed Ubuntu 9.04 from a Live CD and man it took a lot of MY TIME just to test this. I'm starting to think this OS is a piec... Nevermind.

---

### Post by Methuselah on 2010-01-20
If you believe a kernel update broke it maybe you should try booting with an older kernel from the grub menu (with Grub2 I think you force the menu with SHIFT).
It is unfortunate thqt you had such a problem but these things sometimes happen since there is a lot of different hardware out there.

---

### Post by steveneddy on 2010-01-20
It is highly unlikely that a simple kernel update caused bad sectors on your HD.

It is actually more probable that Windows started the process of trashing the HD and installing and tweaking another OS finalized the process. You can't read/write/erase an infinite number of times on any HD. 

Hardware fails. Simple fact.

My suggestion: 

back up your data, if possible, install a new HD and reinstall and be done with the matter.

---

### Post by AlexanderDGreat on 2010-01-20
@Methuselah, @steveneddy - thanks for those comforting words. I think I will try this:

> If you believe a kernel update broke it maybe you should try booting with an older kernel from the grub menu (with Grub2 I think you force the menu with SHIFT).

But my hardware isn't failing! And I'm NOT using Windows, haven't seen it for 8 months now.

---

### Post by HappyFeet on 2010-01-20
> **AlexanderDGreat said:**
> 
**But my hardware isn't failing!** And I'm NOT using Windows, haven't seen it for 8 months now.

How do you know for sure if you are not a pc tech? Did you run the full gamut of hardware diagnostics?

A little word of advice: I *am* a pc tech, and see faulty hardware *all the time*.

---

### Post by AlexanderDGreat on 2010-01-20
Hi HappyFeet,

> How do you know for sure if you are not a pc tech? Did you run the full gamut of hardware diagnostics?

> I installed Ubuntu 9.04 from a Live CD and man it took a lot of MY TIME just to test this.

Jaunty installed from my dvddrive. Also, I used a bios hard disk scanner for the health of my hd, it comes with HP laptops, there were no problems found.

---

### Post by loell on 2010-01-21
> **AlexanderDGreat said:**
> 
But my hardware isn't failing! And I'm NOT using Windows, haven't seen it for 8 months now.

still, have you tried older karmic kernels as suggested?

---

### Post by armandh on 2010-01-21
just because it will play a DVD does not mean an optical drive is good.

old optical drives are my biggest install problem!

they will play a DVD but you never notice a isolated bad frame. not so with missing code.

my first move if the optical drive does not wind up and stay up or the install fails is to try a known good drive

---

### Post by HappyFeet on 2010-01-21
> **AlexanderDGreat said:**
> Hi HappyFeet,





Jaunty installed from my dvddrive. Also, I used a bios hard disk scanner for the health of my hd, it comes with HP laptops, there were no problems found.

There are many things to check besides your hard drive. A professional diagnostics tool will test every component on your motherboard, memory, video card, cpu, etc. A computer relies on more than just a hard drive to work.

---

### Post by HappyFeet on 2010-01-21
> **armandh said:**
> just because it will play a DVD does not mean an optical drive is good.


Very true. People fail to realize that hardware is susceptible to failure even more than software. Ask anyone who fixes computers and does diagnostics. But I know I'm wasting my breath, because "joe six pack" says: "it can't be my hardware!"

Get a job fixing computers, and you'll quickly change your tune.

---

### Post by AlexanderDGreat on 2010-01-22
> still, have you tried older karmic kernels as suggested?

Yes, I've tried it, I chose this 2.6.31-16-generic and 2.6.31-14-generic. My current one is 2.16.31-17-generic. All these kernels produce the error. SRST failed (errno=-16), link is slow to respond. I Googled and people have been telling there's a bug in SATA drives in Karmic.

---

### Post by AlexanderDGreat on 2010-01-22
> because "joe six pack" says: "it can't be my hardware!"

Get a job fixing computers, and you'll quickly change your tune.

Didn't mean to sound harsh mate. :)

By the way, I also fix computers. It's my hobby. I've fixed / assembled 30+ workstations and 2 servers in my lifetime. :)

---

### Post by AlexanderDGreat on 2010-01-24
Solved My Problem! DOWNGRADED to JAUNTY! -- It was a Sunday. ***_I want to rest, and spend time with my family this day, but NO!!!_*** I have to DOWNGRADE and INSTALL & REMEMBER ALL SOFTWARES I needed... Thanks Ubuntu!

Duh... I'm being sarcastic.

---

