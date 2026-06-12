---
title: "Galago UltraPro: Shutdown and Other Hardware Issues"
date: 2014-06-06
forum: System76 Support
---

### Post by Returning2_Linux on 2014-06-06
[LEFT]EDIT: Talk about ironic... The shutdown problem reoccurred moments after posting! That makes twice in less than one day. I will file an official support request, but your ideas would still be most welcome.

I am experiencing some hardware problems with my new Galago UltraPro. A System76 telephone representative suggested that I seek help here. I am running Ubuntu 14.04 64-bit with System76 drivers installed. Thank you in advance for your assistance:

_Shutdown Problem_
Earlier today, I was browsing the internet and my laptop suddenly turned itself off. There was no shutdown cycle. The laptop turned off like happens when a battery dies, but the laptop was plugged into wall power and the battery had a charge of 100 percent. There were no signs of power loss/surge in the room when this occurred. My experience sounds very similar to [this post]("http://ubuntuforums.org/showthread.php?t=2195525"). Using an Ubuntu 14.04 Live DVD, I ran Memtest (one pass of 16GB) and checked the SMART status of my SSD. The RAM test reported zero errors. SMART test also reported zero errors. I would obviously like to diagnose the cause of this before the refund period expires.

_No Caps Lock Light_
There is no Caps Lock light on the laptop. What is an on-screen app for Ubuntu that will show me when Caps Lock is turned on/off?

[U]Remap Touchpad
[/U]I find the touchpad difficult to use due to its size and because of the lack of real left/right buttons. Is it possible to remap the usable surface area of the trackpad in the operating system?
[/LEFT]

---

### Post by vze2449e on 2014-06-09
No Caps Lock Light:

  I use "indicator-keylock"

  sudo add-apt-repository ppa:tsbarnes/indicator-keylock 
  sudo apt-get update
  sudo apt-get install indicator-keylock

[[https://launchpad.net/~tsbarnes/+archive/indicator-keylock]](https://launchpad.net/~tsbarnes/+archive/indicator-keylock])

---

### Post by QPrime on 2014-06-25
> **Returning2_Linux said:**
> [LEFT]_Shutdown Problem_
Earlier today, I was browsing the internet and my laptop suddenly turned itself off. There was no shutdown cycle. The laptop turned off like happens when a battery dies, but the laptop was plugged into wall power and the battery had a charge of 100 percent. There were no signs of power loss/surge in the room when this occurred. My experience sounds very similar to [this post]("http://ubuntuforums.org/showthread.php?t=2195525"). Using an Ubuntu 14.04 Live DVD, I ran Memtest (one pass of 16GB) and checked the SMART status of my SSD. The RAM test reported zero errors. SMART test also reported zero errors. I would obviously like to diagnose the cause of this before the refund period expires.
[/LEFT]
[LEFT]
[/LEFT]
 
                        I have also, over the past 6 months, experienced the exact same issue more than 7 times - often using the PC (light to moderate CPU load) and sometimes while the machine is completely idle (CPU cool, with almost zero load).  All events appear to be completely random with respect to usage and non reproducible in a deterministic way.  I have stress tested the CPU with recovery distros (PRIME and Pi generation)  with no shutdown, and run memtest86+ numerous times with no failures.  All fans spin up and down in response to CPU temperature load, and even with  heavy load, the CPU remains in a reasonable temp. range.  This really does smell like a hardware issue (and not just with my particular machine)... **sigh**.
  
Anyway, a support ticket has been opened with System76.  We'll see how well they respond.

---

### Post by michael181 on 2014-06-25
I think I just had the same shutdown problem on the bonx8: suddenly turned completely off for no aparent reason.  Also had some slowdown/freezing issues as well.  I will post if it happens again.  Does anyone know if the galu1 and the bonx8 have the same manufacturer? (e.g. Clevo or Asus)

---

### Post by DaimyoKirby on 2014-06-26
I too have the Galago (bought it about a month ago) and have noticed this a few times and it's pretty irritating. Anyway, QPrime, you should let us know how your support ticket goes - I may open my own too at some point.

Also, thanks for the PPA [COLOR=#000000]vze2449e[/COLOR], it's nice that I'll be able to see the status of that key now.

**EDIT:** It's quite ironic that not even a minute after I posted this my laptop suddenly shutdown - and I still have 56% battery...

---

### Post by rsalveti on 2014-06-29
> **DaimyoKirby said:**
> I too have the Galago (bought it about a month ago) and have noticed this a few times and it's pretty irritating. Anyway, QPrime, you should let us know how your support ticket goes - I may open my own too at some point.

Also, thanks for the PPA [COLOR=#000000]vze2449e[/COLOR], it's nice that I'll be able to see the status of that key now.

**EDIT:** It's quite ironic that not even a minute after I posted this my laptop suddenly shutdown - and I still have 56% battery...

I also started to have such issues over the past 2 weeks. Got like 5 shutdowns, all happening without any specific reason. Today it was worse though, by battery seems to be dead, and while it says it's 100%, the laptop shutdown itself at the moment I unplug the power plug.

Seems to be hardware related.

---

### Post by QPrime on 2014-07-01
> **DaimyoKirby said:**
> I too have the Galago (bought it about a month ago) and have noticed this a few times and it's pretty irritating. Anyway, QPrime, you should let us know how your support ticket goes - I may open my own too at some point.

Also, thanks for the PPA [COLOR=#000000]vze2449e[/COLOR], it's nice that I'll be able to see the status of that key now.

**EDIT:** It's quite ironic that not even a minute after I posted this my laptop suddenly shutdown - and I still have 56% battery...

   While the web-based support was reasonable, I believe the telephone support was decidedly sub-par, and not what I expected from any company (particularly a company catering to a niche market). I ended up purchasing another laptop while I wait for my defective System76 unit to be RMA'd.  While I do not believe the details of my experience with System76 are appropriate for this forum, I am happy to relate them via private message to those interested or concerned.

My best advice to those having issues with System76 hardware is to open a ticket as soon as possible and get it RMA'd quickly if it does appear to be a hardware issue.  Best of luck to all.

---

### Post by Returning2_Linux on 2014-07-10
Thank you for your suggestion vze2449e. However, the laptop was defective and I had to switch to another brand.

---

### Post by Returning2_Linux on 2014-07-10
As "opinions" are not allowed in this section of the Forums, I have documented my experience regarding System76 and the shutdown/crash issue [here]("http://ubuntuforums.org/showthread.php?t=2233809").

---

### Post by Lemmywinks29 on 2014-07-19
I can start a new thread if necessary, but I'm having the exact same shutdown problem, and can't find a solution. This happens every other day or so, for the month since I got it.

---

### Post by Returning2_Linux on 2014-07-20
> **Lemmywinks29 said:**
> I can start a new thread if necessary, but I'm having the exact same shutdown problem, and can't find a solution. This happens every other day or so, for the month since I got it.

Before I returned my laptop within the 30 day return guarantee, two different System76 representatives told me that the cause of the problem was unknown and that the company was entering a "long term" testing phase. I wish you good luck with your situation.

---

### Post by isantop on 2014-07-21
Actually, go ahead and open a support case at the link in my signature. We'll go ahead and get you a replacement machine. That will solve your problem.

---

