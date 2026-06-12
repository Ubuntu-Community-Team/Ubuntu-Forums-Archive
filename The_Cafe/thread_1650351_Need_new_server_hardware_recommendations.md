---
title: "Need new server hardware recommendations"
date: 2010-12-21
forum: The Cafe
---

### Post by kill4killin on 2010-12-21
So this kind of crosses over a lot of the forums here but I thought I would start here so I don't step on toes.

I'm working on upgrading my Minecraft beta server. It runs Ubuntu server 10.04. The hardware is currently a dual processor P4 era Xeon with 1GB of RAM. I've observed it running consistently at 100% CPU load on CPU0 and sometimes up to 80% on CPU1 with 800MB of the RAM being used up just by the minecraft program alone. Needless to say the performance on the server has been pretty terrible and a lot of my regular players have stated that since the update to Minecraft beta things have gotten substantially slower. To see if it was hardware I put it on a 10.04 virtual machine on my 3.0Ghz C2D and it was significantly faster, even with only 1GB of RAM still so I'm definitely at a hardware bottleneck and I need recommendations on a new processor for the new system I'm putting together.

I am already set on the RAM (4GB of DDR3) and a 500GB RAID 0+1 and it will still be running Ubuntu 10.04 server. However, I would like to virtualize the different servers that I will be running (I.E. seperate the web server, game server, music server, etc.).

I'm between a AMD PhenomII X4 925 or an Intel C2D (haven't decided on the model). Both have advantages over the other, the Phenome have 4 cores and more L3 but I've heard from some people that the C2D will perform better at the same speed per core. Either way I would like to stay in or around the $130 range on the processor.

I'm looking for recommendations and I'm also looking to see if anyone has any thoughts on what the advantages of each would be.

---

### Post by TSJason on 2010-12-21
You'll probably see a pretty good increase no matter which way you go, but I personally believe the AMD Quad core just sounds sexier and I would go with that. 

Out of curiosity, did you try recompiling your kernel on that old Xeon box with processor optimizations to see if that helped at all?

---

### Post by CharlesA on 2010-12-21
Generally AMD and Intel are about equal. More cores are usually better.

If/when I upgrade my server, it'll be getting an AMD processor.

---

### Post by kill4killin on 2010-12-21
Does anyone happen to know if minecraft's server application is multithreaded? I do notice multiple instances of the .jar file in htop when it's running so I think it might be, in which case the X4 could be my best route...thoughts?

---

### Post by TSJason on 2010-12-21
> **kill4killin said:**
> Does anyone happen to know if minecraft's server application is multithreaded? I do notice multiple instances of the .jar file in htop when it's running so I think it might be, in which case the X4 could be my best route...thoughts?

I believe it is multi-threaded, yes - though you won't see that in the output of htop since that's just listing processes. I don't believe it's multi-core though.

---

### Post by 3Miro on 2010-12-21
Phenom II X4 outperforms Core 2 Duo and it is in the same range with i5. Phenom II X6 competes with i7. In performance per dollar, AMD beat Intel, however, the high end Intel CPUs would outperform AMD. Especially if you are running something multi-threaded, Pehnom II X4 is the right choice.

---

### Post by kill4killin on 2010-12-21
Thank you 3Miro, you have sort of affirmed what I was thinking.

So as it stands, and I'll let this simmer for a bit, but the list is:

PhenomII X4
4GB of DDR3 (would anyone recommend more for virtualization with either QEMU or Virtualbox?)
4 x 500GB drives in RAID 0+1 (still waffling though)

Thanks for the input everyone

---

### Post by CharlesA on 2010-12-21
For virtualization, I'd recommend getting as much RAM as you can afford/as your board can support.

The Box I am using at home for VMs has 6GB of RAM atm, but it's only a Dual core, so there's a limit as to how many VMs I can run at a time.

---

### Post by 3Miro on 2010-12-21
> **CharlesA said:**
> For virtualization, I'd recommend getting as much RAM as you can afford/as your board can support.


+1. The way Linux HDD cache works is that any "free" RAM will be occupied by cached HDD data, so nothing gets wasted. Basically, more RAM = smoother HDD operations, so depending on exactly you are doing, more RAM can be better than RAID.

---

### Post by kill4killin on 2010-12-21
In that case I might go with the single 4GB stick because it's a little more expensive than the 2 2GB sticks to leave more room to expand later. The motherboard I'm looking at is an ECS board that supports up to 32GB of RAM.

---

### Post by kill4killin on 2010-12-21
> **3Miro said:**
> +1. The way Linux HDD cache works is that any "free" RAM will be occupied by cached HDD data, so nothing gets wasted. Basically, more RAM = smoother HDD operations, so depending on exactly you are doing, more RAM can be better than RAID.

The RAID is primarily for redundancy. I'm going to be running some applications on it that will be rather I/O intensive so that was the thinking behind the 0+1, drop the write times down as much as I can while still keeping the data redundancy. I want one of the VMs to hold my home media (at least that's the plan) and losing all that is not really an option I want to think about.

---

