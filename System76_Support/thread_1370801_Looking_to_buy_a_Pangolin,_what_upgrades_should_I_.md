---
title: "Looking to buy a Pangolin, what upgrades should I get?"
date: 2010-01-02
forum: System76 Support
---

### Post by ubunchu on 2010-01-02
I have been an Ubuntu user for two years now, and have been using a Thinkpad T60 for my schoolwork, and now I am thinking about a new laptop. I am sure that I want a Pangolin Performance, but I am unsure on whether to upgrade the ram and processor and anything else.

I would be using it for what a typical student uses it for: watching movies, surfing the net, maybe a little pspp, and a little openarena or tremulous. So far my T60 has done me just fine in what I need it to do for school, so I'm not looking to shell out a bunch of money for speed that I will never use. So what upgrades do you think I should get?

---

### Post by jml on 2010-01-02
ubunchu, some of my suggestions would depend on your intended use for this computer.  If I were going to buy this laptop for myself, here is what I would order.

I would upgrade to one of the core 2 Duo chips.  I would get the T6500 if this was primarily a desktop replacement.  I would get the P8700 if I was going to use this on battery power because it draws less power and would give you better battery life.

I would get 4 gigs of RAM, 8 gigs if you were planning to run VM with Windows.  But only if you are planning to run 64 bit Ubuntu.  32 bit only supports 4 gigs of RAM max.

I would specify a 500GB HD for storage, unless you planned to run the laptop primarily on battery.  Then I would consider a solid state drive (SSD).  You will have to decide if the increased cost is justified.

Since the laptop only gets about 2.5 hours of battery life, I would buy a spare battery if I planned to use the laptop on long plane/train trips.  If you are going to use this laptop in two specific locations,  work and home for example, you may want to buy a second AC adapter.  This will reduce the weight and the amount of stuff for your daily commute.

Special considerations:  If you are planning to run multiple resource intensive applications at the same time, multiple virtual machines (VM,) or GPU intensive applications like rendering animations, then I would buy the most powerful CPU and the most RAM that you can afford.  In fact, if you plan do do this kind of work, you might want to consider the Serval Professional.

Now if you want the most "bang for the buck" I would specify:  Core 2 Duo T6500, 4 Gigs RAM, 500GB HDD.  This is what I would buy for myself.  Hope that this helps.

Joe

---

### Post by Eldera on 2010-01-03
[quote=jml]ubunchu, some of my suggestions would depend on your intended use for this computer.[/quote]

I agree. 

Do you need Windows for any of your studies? Are you going to dual boot or run Windows in a VM? If you are going to use any virtualization, you probably do not want the T4200 or the T6500. They lack VT-x, Intel's hardware support for virtualization.

A good site for more details on the specs of the processors is
[http://www.intel.com/consumer/index.htm?iid=subhdr+chome](http://www.intel.com/consumer/index.htm?iid=subhdr+chome)

Whatever you get, I hope you enjoy it as much I have enjoyed my panp4n.

Best wishes, Eldera

---

### Post by satsujinka on 2010-01-03
> **Eldera said:**
> Do you need Windows for any of your studies? Are you going to dual boot or run Windows in a VM? If you are going to use any virtualization, you probably do not want the T4200 or the T6500. They lack VT-x, Intel's hardware support for virtualization.

I disagree.

My T5250 1.50 ghz dual core without vt-x runs XP in vbox just fine.

From the sounds of it ubunchu, you really don't need anything more than the default. But if I was buying the computer, I would probably go with the P8700, the 80gb ssd, and an extra battery (which is around $1,270.) However, if you virtualize Vista or 7 then you may want the 4gb ram.

---

### Post by bill516 on 2010-01-09
Well this is interesting because I have a PanP4 with a CPU that lacks vt-x.  I run 64 bit Ubuntu, currently 9.10.  If I install a VM I can run 32 bit guest systems very nicely.  If I attempt to run any 64 bit guest a message pops up to the effect that my "32 bit system" cannot support a 64 bit guest.  So without vt-x the VM sees and uses only one side of my dual-core CPU?  Don't know, but it seems that way.

In any event if a person is going to use VMs extensively the only fix is to write down the CPU choices, go over to Intel and make sure that the preferred CPU has vt-x.

If you do not want to spend a lot of money then the Serval is not an option.  It does get pricey.

BTW I do not run Windows at all.  I must say I have been pleased with System 76 and the support they offer.  I would purchase another System 76 machine if I needed one.

I run multiple Linux systems on my laptop and they work.  So if Ubuntu is not entirely to your taste you do have options, but Ubuntu is a fine choice.

---

### Post by Flyers2391 on 2010-01-09
I was also looking at the Pangolin (leaning toward the lemur now but still haven't made a decision) and was planning on the following upgrades:

Core 2 Duo P8700 2.53 GHz 1066 MHz FSB 3 MB L2 (25 Watt) ( +$149.00 )
4 GB - DDR2 800 MHz - 2 DIMMs ( +$65.00 )
320 GB 7200 RPM SATA II ( +$27.00 )

that comes in at $970 with the current discount, pretty good price point in my opinion.  I use an XP VM at work giving it 512 MB RAM and it runs fine (mostly just for outlook, visio and web conferencing that doesn't work on linux).
Depending on your personal use you may want another adapter and/or battery ... I find carrying around another battery not worth it because it is never charged when I actually need it.

---

### Post by 3Miro on 2010-01-09
I have a panp4n, very close to the configuration that you give (Core 2 Duo 2.4 + 4GB RAM). I use virtual box a lot and when I was writing my dissertation I used it for some scientific computations (RAM + CPU came in handy). The RAM upgrade is pretty cheap anyway and Linux does good job with cashing so you will not waste much of it, thus RAM upgrade is nice.

The CPU is also nice to upgrade, but the cost is more, so you will have to make that call. Same for the HDD, 250 is plenty for me, but you might need more. I also go with 5400RPM on a laptop because with good Linux cashing 7200RPM isn't worth the battery life and extra cost (again this is for me).

Speaking about battery life, mine is an older version, but I can get only little short of 2 hours on it. Getting to 2.5 will require some tweaking. The main reason for that is the GPU, it is powerful, but it also eats the battery.

For the difference between Lemur and Pangolin, I would give all the advantage of performance to the Pangolin especially the graphical one. You can play 3D video games with wine on the NVIDIA video card of the Pangolin. On the other hand, Lemur wins in compactness and probably battery life. Also, I am not sure if the weight is an issue, it is nuisance for me sometimes, but then I do need the extra workout.

BTW I don't own a Lemur, nor do I know anyone with a Lemur beyond this forum, so I might be completely wrong in the comparison.

---

