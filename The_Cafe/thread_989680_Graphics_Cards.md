---
title: "Graphics Cards"
date: 2008-11-21
forum: The Cafe
---

### Post by Grant A. on 2008-11-21
I'm looking into buying a new graphics card while they are cheap on Black Friday here in the U.S., anyways, what is the (2nd) best graphics card out there from NVidia? I'm looking for something that will be compatible with the same motherboard that an AMD Athlon x2 (AMD 64 Live!) uses. I currently have a GeForce 6 card, which hasn't given me good performance lately. I'm not looking for something that needs over clocking or liquid cooling. Any suggestions? Thanks in advance. :)

---

### Post by cardinals_fan on 2008-11-21
NVIDIA will care about you for a little while, then ignore your complaints and focus on their newer cards.

---

### Post by Skripka on 2008-11-21
> **cardinals_fan said:**
> NVIDIA will care about you for a little while, then ignore your complaints and focus on their newer cards.

AMD/ATi will write p*ss-poor drivers for your card, whether it is new or old.



@the OP, what kind of north/southbridges are on your mobo?

PS-2nd best from Nvidia right now is a GTX 260....it is a monster card, weighs a few pounds, and is 10.5" long and needs 2 6-pin PCIe power inputs.

---

### Post by Grant A. on 2008-11-21
Holy crap. That IS a monster card. I'm not quite sure, will I need to open up the computer to see this? Or can I do a certain command to check it?

---

### Post by Skripka on 2008-11-21
> **Grant A. said:**
> Holy crap. That IS a monster card. I'm not quite sure, will I need to open up the computer to see this? Or can I do a certain command to check it?

The only reason it would really matter is if you ever plan on using multple GPUs in SLI or Crossfire.  If you know the manufacturer and their own name for it, it is easy enough to look up.



The GTX260 is a beast, it barely fit in my LianLi ATX mid-tower, by "barely" I mean that I had to shuffle drives, and there is NO space between the GPU and the drive bay rack....it is a neat toy though.....and for 1/2 the cost of a GTX280 and only a 20% or so change in performance--it kicks but.

The GTX2XX "cards" from Nvidia are not so much "cards" as they are "bricks".....with more transistors in them than in any current generation CPU :popcorn:

---

### Post by Grant A. on 2008-11-22
So it's essentially a brick of silicon. :lolflag:

Hmm... any recommendations on how to set up a 2nd internal hdd, one for windows, and one for linux?

---

### Post by zachtib on 2008-11-22
I'd suggest a Geforce 8800GT (I upgraded to one from a Geforce 6600GT)

It's a great card for the money, and it's not a giant brick, either.

---

### Post by Skripka on 2008-11-22
> **Grant A. said:**
> So it's essentially a brick of silicon. :lolflag:

Hmm... any recommendations on how to set up a 2nd internal hdd, one for windows, and one for linux?

My way:

1) Install windows first to it's own drive.


Now, presuming you don't already have a linux install, the linux part is easy....if you DO and you don't want to lose it--it makes things much more complicated.....

2) Install linux in 3 partitions to its own drive (/root, /media, /swap), AND install GRUB to YOUR LINUX DRIVE, NOT the Windows drive.

2a) Set your windows drive to mount as /windows, during setup

3) Open your BIOS, set your Linux drive as PRIMARY boot drive



Now why the above especially #2?  This sandboxes both Windows and Linux, you can completely lose one drive without losing the ability to boot the other (you are NOT messing around with MBR).

As zachtib said above, an 8800GT is a nice card too that is less brickish--and you don't need to worry about whether or not your case will fit it.  Depending on how little you are doing, a GTX200 card can be completely overkill, they also NEED at least a 500W PSU to drive them.

---

### Post by Grant A. on 2008-11-22
Thank you very much for the info. :)

I have thanked everyone who contributed their time to helping. :)

---

### Post by piousp on 2008-11-24
Also, you may want to consider this: a gtx 260 will probably be an overkill now, but hopefully it will last longer in terms of power gaming.
Also, if you wanna stay on a middle ground, you can try with a 9800gtx or an 8800 gtx, as those cards can run every game available now, not at highest settings, but they will.

---

### Post by gletob on 2008-11-24
> **Skripka said:**
> My way:

1) Install windows first to it's own drive.


Now, presuming you don't already have a linux install, the linux part is easy....if you DO and you don't want to lose it--it makes things much more complicated.....

2) Install linux in 3 partitions to its own drive (/root, [COLOR="Red"]/media[/COLOR], /swap), AND install GRUB to YOUR LINUX DRIVE, NOT the Windows drive.

2a) Set your windows drive to mount as /windows, during setup

3) Open your BIOS, set your Linux drive as PRIMARY boot drive



Now why the above especially #2?  This sandboxes both Windows and Linux, you can completely lose one drive without losing the ability to boot the other (you are NOT messing around with MBR).

As zachtib said above, an 8800GT is a nice card too that is less brickish--and you don't need to worry about whether or not your case will fit it.  Depending on how little you are doing, a GTX200 card can be completely overkill, they also NEED at least a 500W PSU to drive them.

I think you meant /home. /media having its own partition seems pointless

---

### Post by Skripka on 2008-11-24
> **gletob said:**
> I think you meant /home. /media having its own partition seems pointless

I try to only Post Under the Influence, at least that is what I claim afterwards. :-P

---

### Post by pgatrick on 2008-11-24
> **gletob said:**
> I think you meant /home. /media having its own partition seems pointless

Personally I think a seperate /media makes more sense than seperate /home, as that can cause issues if you upgrade or install a different distro and use the same /home partition with all the old config files. Just keep important things on the /media partition. :)

---

### Post by bufsabre666 on 2008-11-24
i still say go with amd/ati. nvidia has better current linux drivers but the ati ones are decent. but the point i want to make is ati has opened their drivers, which means if you upgrade your system components often it doesnt matter go nvidia, but if you plan on using it for an extended period of time go with ati, youll put up with not the best drivers (although to say theyre bad is really over stating matters, they work very well just not videos and compiz at the same time, i dont use compiz so it doesnt bother me) but eventually they opensource will catch up with it and will have 3d accell ((seriously it only took about 4 months for 2d accell, 3d accell is futher off but i imagine its not ganna be too much further off.

but summary: if you upgrade often: nvidia, if you stick with hardware till it becomes ancient: ati. newegg has a bunch of 4830's between 100 and 130 US dollars and presumably cheaper on black friday

---

### Post by handy on 2008-11-25
A 9800gtx outperforms the 8*** series due it being on a finer die it both runs cooler & uses less power, & they are really in price performance terms amazingly good value.

That is what I would buy currently anyway. :-)

---

