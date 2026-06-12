---
title: "The New Apple M1 Chip"
date: 2021-04-11
forum: Ubuntu, Linux and OS Chat
---

### Post by bobnutfield on 2021-04-11
Hello Everyone

First and foremost, I am an Ubuntu user since 2006, and remain so.  A couple of years ago, I took up the hobby of drone photography.  I have a few drones in the Mavic series, and really do enjoy the hobby.  As I continued to upgrade, the cameras got better and I am now also learning some of the more sophisticated video editing software.  I had been using Shotcut with Ubuntu and it has been great.  But now that I have a drone which shoots in 4K, I want a more complete video editor.  I discovered DaVinci Resolve several months ago and tried to use it on my aging Ubuntu laptop, but it just wouldn't handle it.  I needed a minimum i7 processor, 32GB memory and a video card with at least 6GB of VRAM.  When I priced up what a rig like that would cost, I just could not afford it.  

Then, on another forum someone suggested the new Apple Mini with an M1 chip (just introduced about a year ago.)  This little computer could be purchased for less than the cost of a single high end video card.  I was suspicious of all the claims about it capability, but after weeks of research, I took the plunge and bought one.  It only has 8GB of RAM, but I have to tell you that all of the claims about the speed and power of this little computer are true.  Not only does it run DaVinci Resolve fast and smoothly, but the hardware test results (Blackmagic Speed Test) reveal I can edit, colour grade and add special effects up 8K resolution.  I am stunned by the speed and power.

I started imagining Ubuntu running on this machine, but I don't think it has been tried yet.  The M1 chip is an ARM64, similar to the chips in iphones.  It has 8 processing cores and 8 GPU cores, and 16 neural cores for machine learning (whatever that means, I have no idea.)  I know that Ubuntu (and many other Linuxes) have been ported to ARM processors in the past, and I believe it is only a matter of time before the traditional x86 Intel and AMD processors  become obsolete.  When you can get this much power for lower cost, lower power needs and smaller chips, I believe this is the future.

I am certainly not an expert but I would encourage anyone needing a powerful computer for lower cost to check it out.

Bob

---

### Post by rbmorse on 2021-04-11
I love my M1 Macbook Air, but right now it won't run Linux, mostly due to Apple policies toward sharing their IP.  They just don't want you to be able to run anything but Apple operating systems and software. 

There are a couple of ARM developers working to reverse-engineer support for the M1 processor into the Linux kernel, but as far as I know they haven't even started on getting the GPU to work, so even if the kernel will eventually boot and run on the M1, it will be of limited value for most people.

But yeah, it's one hell of a little machine.

---

### Post by CatKiller on 2021-04-11
> **bobnutfield said:**
> I started imagining Ubuntu running on this machine, but I don't think it has been tried yet.
[Work is underway](https://arstechnica.com/gadgets/2021/04/apple-m1-hardware-support-merged-into-linux-5-13/), but there's still a long way to go yet.

---

### Post by oldfred on 2021-04-11
There is also this experimental version:
Linux on M1
[https://corellium.com/blog/linux-m1](https://corellium.com/blog/linux-m1)

---

### Post by bobnutfield on 2021-04-11
Well, just like the hackentosh, it will eventually happen.  I've been an Ubuntu user for years and haven't used the macOS much at all.  But, I'm amazed at how similar they look and act.  They even, for the most part, share the same icon sets.  I tried a few Linux commands in the mac terminal, and some of them actually work.  I realize they are both based on different branches of Unix, but it's just a matter of time.  I am curious how Intel and AMD are going to respond to the M1.  

Bob

---

### Post by kurt18947 on 2021-04-11
I thought AMD had done some work in the non X86 world but don't have any specifics. Intel moving away from X86 which has made them $billions may be like Kodak moving away from film. The IT world really runs on X86 except for the phone/tablet segment. That may change with the ARM server chips.

---

### Post by bobnutfield on 2021-04-11
Well, I am just blown away by how powerful this little computer is.  But, the Mac Mini needs a monitor, and ironically I have mine connected to a 65 inch Sasmung Smart TV, which of course is run by Linux.  This particularly is useful because the only thing I use the Mac Mini for is running DeVinci Resolve and big screen real estate eliminates the need for a second monitor.  EVERYTHING else is done on my Ubuntu laptops.  And unfortunately, DJI has not ported anything to Linux, so my Drone firmware updates have to be done on a Windows laptop.

It won't happen any time soon, but my guess is that the next big breakthrough is going to come from AMD.  I know they are feverishly working on a ARM type chip.  Intel has dropped the ball in innovation and, since the Ryzen introduction, it may take years for them to catch up, if they ever do.

---

### Post by grahammechanical on 2021-04-12
If the past is any guide to the future it will not be long before some  programmers decide to take full advantage of the capabilities of this  chip design and slow the thing down to a snail's pace.  The commercial  enterprise that is marketing this chip has a policy of deliberately  making its hardware obsolete to force consumers to continue spending. 

OK.  So I am a misery-guts. It does not matter how fast the hardware is  humans are limited in how fast they can work a machine. I am looking  forward to the day when a super powerful machine takes control of that  commercial enterprise by deeming its human management as too slow to  keep up.

Regards

---

### Post by oldfred on 2021-04-12
There is a lot of RISC-V info. That may be a new processor that gets used if price comes down.

[https://hardware.slashdot.org/story/21/03/08/2117238/mips-technologies-joins-risc-v-moves-to-open-source-isa-standard](https://hardware.slashdot.org/story/21/03/08/2117238/mips-technologies-joins-risc-v-moves-to-open-source-isa-standard)

---

### Post by rbmorse on 2021-04-12
> **grahammechanical said:**
>  I am looking  forward to the day when a super powerful machine takes control of that  commercial enterprise by deeming its human management as too slow to  keep up.

Regards
Maybe Elon Musk will buy it. That could be really interesting.

---

