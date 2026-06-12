---
title: "[Laptop] Upgrade Dual-Core CPU to Quad-Core possible?"
date: 2014-05-04
forum: The Cafe
---

### Post by GameX2 on 2014-05-04
Hi,

I own a Lenovo laptop, Thinkpad E420, which work really well; I recently read that this CPU is not soldered so according to the Lenovo forums, *is* upgradable. =)
Here are the officially listed, and supported CPU.  I have a Intel Core i3-2350m :

Intel Core i3-2310M Processor (2.10GHz)
**Intel Core i3-2350M Processor (2.30GHz)**
Intel Core i5-2410M Processor (2.30GHz)
Intel Core i5-2430M Processor (2.40GHz)
Intel Core i5-2520M Processor (2.50GHz)
Intel Core i5-2540M Processor (2.60GHz)
Intel Core i7-2620M Processor (2.70GHz)
Source: [https://forums.lenovo.com/t5/ThinkPad-Edge-S-series/Upgrading-my-Lenovo-E420/td-p/744517](https://forums.lenovo.com/t5/ThinkPad-Edge-S-series/Upgrading-my-Lenovo-E420/td-p/744517)

While I *could* upgrade to the i7, pretty sure the price won't worth it.  Even the i5 would have a better value for his price.  Here's a benchmark:

[IMG]https://dl.dropboxusercontent.com/u/67605655/Capture%20d%27%C3%A9cran%202014-05-04%2020.17.05.jpg[/IMG]
According to this, the i7 difference wouldn't worth it, possibly being a lot more pricey (And maybe the computer store will add an extra charge to that, I should ask.  It's not soldered, but I still have to reach for the motherboard and I'm not comfortable - yet - of dissasembling it myself).

So I wondered if it was considerable of putting a Quad-Core CPU in that Dual-Core laptop - assuming it's possible at all, that would probably be a more reasonnable price for the performance boost.  I searched, and found a few CPU that had the same socket type as mine (Which is PGA988B for the i3 and BGA1023 for the i5.  Weird since these 2 CPUs are supported, but are listed with different socket types?).

While Quad-Core CPU with the same socket type seem hard to find, I did found a few.  Link:

My CPU: [http://www.techpowerup.com/cpudb/1312/core-i3-2350m.html](http://www.techpowerup.com/cpudb/1312/core-i3-2350m.html)
A Quad-Core i7: [http://www.techpowerup.com/cpudb/987/core-i7-2670qm.html](http://www.techpowerup.com/cpudb/987/core-i7-2670qm.html)

The problem is the TDP, all the officially supported CPU I listed are 35W, while the Quad-Core is 45W.  Is this problematic?  Seems like it's not "dramatic", but I have to watch out for overheating.  This guy managed to stick a quad-core inside of a dual-core, with a higher TDP than the original CPU.  And someone else suceeded with a Dual-Core inside a Single-Core: [http://forum.notebookreview.com/hardware-components-aftermarket-upgrades/618059-your-experiences-swapping-lower-tdp-cpu-higher-tdp.html](http://forum.notebookreview.com/hardware-components-aftermarket-upgrades/618059-your-experiences-swapping-lower-tdp-cpu-higher-tdp.html)

There are other similar CPU than this one, but most of them are Intel IvyBridge while mine is SandyBridge.  Read that both seem compatible...

So, what is the probability of that CPU to work?  Will the BIOS reject it?  Most of what I read say "You never know until you try".  The problem is the TDP...  I don't know, don't have much experience with hardware (mostly software).

I ask this since "officially", the RAM limit of this laptop is 8GB, although users tested and succeeded with inserting 16GB of RAM in.

EDIT: Interestingly, the Lenovo Ideapad Y570 has this Quad-Core CPU: [http://www.newegg.com/Product/Product.aspx?Item=N82E16834246324](http://www.newegg.com/Product/Product.aspx?Item=N82E16834246324)

Thanks for your answer.

---

### Post by tgalati4 on 2014-05-04
Thinkpads have a history of whitelisting hardware, so it is possible that the BIOS will complain if you change the CPU's.  TDP should be OK, it's only 10 watts.  It would be an issue if you put a 75-watt processor under a 35-watt heat sink.

The greater risk is not getting the assembly correct and having a non-functioning laptop.  You need to keep track of each screw and location.  Putting a long screw in a short screw hole can short out the motherboard.  I tape my screws on a white sheet of paper in the approximate location that they were removed.  Be careful with the ribbon cables and connection headers.  Thankfully thinkpads are little more robust and easier to take apart than most disposable laptops.

As far as PGA vs BGA, perhaps you can put a Ball Grid Array chip in a pin socket--I don't know, I've never done it.

---

### Post by GameX2 on 2014-05-04
> **tgalati4 said:**
> Thinkpads have a history of whitelisting hardware, so it is possible that the BIOS will complain if you change the CPU's.  TDP should be OK, it's only 10 watts.  It would be an issue if you put a 75-watt processor under a 35-watt heat sink.

The greater risk is not getting the assembly correct and having a non-functioning laptop.  You need to keep track of each screw and location.  Put a long screw in a short screw hole can short out the motherboard.  Rip a ribbon cable and your keyboard or hard disk fails.  

As far as PGA vs BGA, perhaps you can put a Ball Grid Array chip in a pin socket--I don't know, I've never done it.

Thank you.
I don't plan on doing the upgrade myself, too risky for me - at the moment.

2 years ago, the store changed the laptop motherboard, because there were several complains that the E420 had a faulty motherboard that would commit suicide after a certain period.  The store replaced the motherboard just-in-case for free (When it was still under warantee), and the laptop returned just like normal.  I don't know if my new motherboard still has the bug, but what else can I do about that. :/

---

### Post by RichardET on 2014-05-04
Who needs this trouble?   Either live with an i3, not a bad processor, really, or buy a new laptop.

---

### Post by GameX2 on 2014-05-04
> **RichardET said:**
> Who needs this trouble?   Either live with an i3, not a bad processor, really, or buy a new laptop.

I consider a SSD at least, that would probably worth it, but I agree with you - I will still call the store on thuesday to see if they have any theory/experience with this, and consider what they say.

Please keep me updated if someone else attempted something like this.

---

### Post by kurt18947 on 2014-05-05
Unless you do a lot of processor intensive tasks, I wonder if an SSD wouldn't make you machine 'feel' faster than a processor upgrade without the risks.

---

### Post by GameX2 on 2014-05-05
I do 3D, video, Photoshop, and even virtualisation.  Last year I used to run Windows virtualised in Ubuntu quite often to run the Adobe products without problem (I managed to get them running using Wine without "apparent" problem, but you never know when the software will randomly crash).  The only softwares that I cannot use virtualised are AfterEffects, Premiere and 3dsMax.  While I *can* run them, 8GB of RAM isn't enough (Splitted, being 4GB on the Windows guest) to run smoothly.  I could upgrade to 16GB, but I would have to buy 2x8GB (I don't have a free slot), and that goes for like 150$.  Not worth it in my opinion.

For reference purpose, the most intensive task I've done was running OS X in VMware - I had a iOS development class, so is the only way I can do the work at home.  The class is finished anyways, I will delete the VM in a few weeks (If I didn't had this, I couldn't have work for the class).

The store will charge 50-60$ for installing the CPU, it takes about 1 hours to remove everything up to the motherboard.  He said as well that this upgrade probably won't worth it.
Checked, and the i5 goes for 60$ and the i7, 150$.  Not soooo bad, but still, there's the 50$ extra for professional installation.

SSD would remain the best choice for now, unless there's a way to use a unofficially supported quad-core, which would probably be a hit-or-miss.
Thanks for your advice.

---

### Post by jon43 on 2014-05-05
So, some years ago I purchased a Dell Inspiron 570. It came with an Athlon X2 processor and 4gbs of memory. I decided it was not nearly fast enough, so I added more memory. Then I upgraded the CPU tp a Phenom X4. Then switched to an SSD. Then added a dedicated graphics card. And on, and on, and on. By the time I was done, only the motherboard was left and it was flying... I mean flying. Until the board eventually fried itself because even though the manufacturer listed the Phenom as compatible, and it played nice with the BIOS, the 125w CPU was still WAY too much for the hardware. 

The moral of the story, in my mind, is that factory boards usually aren't built as well as consumer boards and should really not serve as the platform for any serious CPU upgrades. 

Also, you would likely see more gains from switching to an SSD from the spinning disk- and you could do that yourself at home.

---

