---
title: "Okay this is ridiculous do we even need swap ?"
date: 2010-10-20
forum: The Cafe
---

### Post by MooPi on 2010-10-20
I deleted my swap partition today and created a swap file. It is activated and is showing in htop but I can't get my computer to even attempt to start to use the swap. Here is the scenario I have Chromium open with six tabs open, three with flash video. Also I have a dvd being encoded and a music cd being ripped and encoded. I'm playing music just for frosting and I still haven't touched the swap. This is a fast computer and it didn't even break a sweat on this. I'm going to find a stress test just to see if I can get my computer to access swap. Otherwise why even have it right ? 
Here are my system specs: AMD Athlon X4 620 , 2 gig ram. Modest quad core and not top of the line.
Does anyone go without swap ?

---

### Post by red_Marvin on 2010-10-20
You should be happy that you don't need to use swap, as accessing it is magnitudes slower than accessing ram. However, there are times when you do need it, no matter how much ram you have, as when hibernating, as the content of the ram is copied down to the harddrive so that the computer can be powered off without memory loss.

---

### Post by NightwishFan on 2010-10-20
You might not always "need" swap, though it is good to have. The kernel likes to have it available, and you need it for hibernation. A swap file is as good as a swap partition. Also, if you make a mistake and load somethig too big (say on GIMP) and it uses all your ram, swap will kick in and you can cancel it etc.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)


I like using as much swap as possible so my system generally caches more even if it does not touch swap.

---

### Post by juancarlospaco on 2010-10-20
You can go without Swap, its a normal Linux feature.

*But you will fail to Hibernate, and its normal too.*

---

### Post by MooPi on 2010-10-20
If you don't hibernate then do you ? I don't (desktop)

---

### Post by NightwishFan on 2010-10-20
If you do not hibernate you do not really need swap, but I would still use some.

---

### Post by FuturePilot on 2010-10-20
It seems you're mainly doing a bunch of CPU intensive tasks and not so much memory intensive. Start up a few virtual machines and then see what happens.

---

### Post by juancarlospaco on 2010-10-20
> **FuturePilot said:**
> It seems you're mainly doing a bunch of CPU intensive tasks and not so much memory intensive. Start up a few virtual machines and then see what happens.

Maybe on recent Ubuntu it dont make the effect because of K.S.M. on Kernel. Maybe not... depends on VM config
:)

---

### Post by NightwishFan on 2010-10-20
I love playing with vms, takes my ram to the roof. :D

---

### Post by MooPi on 2010-10-20
Okay I just fired up prime95 and finally got the system to touch swap barely. A measly 9 Mb of swap, but it used it :)

---

### Post by alexandari on 2010-10-20
It's like saying "Geez do we humans really need eyebrows? I mean,they just stand there...hairy and stuff..."

---

### Post by nerdopolis on 2010-10-20
AFAIK You need swap for hibernation...

---

### Post by NightwishFan on 2010-10-20
> **alexandari said:**
> It's like saying "Geez do we humans really need eyebrows? I mean,they just stand there...hairy and stuff..."

Yes we do. Like Gandalf eyebrows to the max.

---

### Post by 3Miro on 2010-10-20
I make math programs under Linux and when I mess something up and create a huge memory leak, the swap gives me enough time to kill the bad program without crashing the entire machine. If I don't have swap, then the system will probably crash as soon as I start the bad program.

I also heard you need it for hibernation, but I rarely use that even on my laptop, so I am not sure.

I heard a story once for an old computer with kernel that would swap the opcode requited to retrieve something from the swap. Funny story.

---

### Post by anupcshan on 2010-10-21
> **3Miro said:**
> I make math programs under Linux and when I mess something up and create a huge memory leak, the swap gives me enough time to kill the bad program without crashing the entire machine. If I don't have swap, then the system will probably crash as soon as I start the bad program.

I also heard you need it for hibernation, but I rarely use that even on my laptop, so I am not sure.

I heard a story once for an old computer with kernel that would swap the opcode requited to retrieve something from the swap. Funny story.


If the system runs out of memory (RAM + swap), kernel tries to kill some program(s) to free up some memory. This is called [[COLOR="DeepSkyBlue"]OOM killing[/COLOR]]("http://linux-mm.org/OOM_Killer"). So, even if there is no swap allocated, the system should run fine if it runs out of memory for a period of time.

---

