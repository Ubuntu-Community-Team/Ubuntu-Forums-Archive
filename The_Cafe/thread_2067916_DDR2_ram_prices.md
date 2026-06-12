---
title: "DDR2 ram prices"
date: 2012-10-07
forum: The Cafe
---

### Post by Cyber72 on 2012-10-07
There is a big difference in ram prices between DDR2 and DDR3. For example Crucial charge £28.78 for 4GBx2 DDR3 and £118.78 4GBx2 DDR2. My laptop uses DDR2 and one day I will have to upgrade it. Being old technology have they stopped manufacturing it? And most importantly will the price go up or down in future years?

---

### Post by PhilGil on 2012-10-08
I doubt DDR2 is still being manufactured, so the price will continue to increase over time until new modules become prohibitively expensive or unavailable. You'll be able to buy used at a reasonable price for many years to come.

---

### Post by nothingspecial on 2012-10-08
*Thread moved to **The Community Cafe**.*

---

### Post by mips on 2012-10-08
> **Cyber72 said:**
> My laptop uses DDR2 and one day I will have to upgrade it. Being old technology have they stopped manufacturing it? And most importantly will the price go up or down in future years?

As manufacturing ceases and stocks dwindle the price goes up. Law of supply & demand.

Just buy some run of the mill kingston, transcend etc ram. Shop for value.

---

### Post by fat yak on 2012-10-08
at that price it might make sense to wait and change to a SSD as they are getting cheaper by the month and speed things up that way.

---

### Post by kurt18947 on 2012-10-08
> **PhilGil said:**
> I doubt DDR2 is still being manufactured, so the price will continue to increase over time until new modules become prohibitively expensive or unavailable. You'll be able to buy used at a reasonable price for many years to come.

I bought some used PC-133 and it seems fine.  I made sure to buy from a vendor with return privileges and as soon as I got it I fired up memtest and let it run for a few hours.  Flash memory has a life span, I don't know that DRAM does.

---

### Post by Paqman on 2012-10-08
> **fat yak said:**
> at that price it might make sense to wait and change to a SSD as they are getting cheaper by the month and speed things up that way.

???

Er, he's talking about RAM.

---

### Post by PhilGil on 2012-10-08
> **Paqman said:**
> ???

Er, he's talking about RAM.
I think what **fat yak** is saying is that, if the original poster is looking to speed up his/her computer, the £118.78 might be better spent by purchasing an SSD rather than a RAM upgrade.

I don't necessarily agree with that. It depends on how the OP uses his/her machine.

---

### Post by sandyd on 2012-10-08
Just don't get kingston valueram - They take ram chips from different suppliers, and sometimes one or two of the chips on the board run at a slightly lower/higher speed than the others. That can cause a few weird problems that would be hard to diagnose.

---

### Post by Paqman on 2012-10-09
> **PhilGil said:**
> I think what **fat yak** is saying is that, if the original poster is looking to speed up his/her computer, the £118.78 might be better spent by purchasing an SSD rather than a RAM upgrade.

I don't necessarily agree with that. It depends on how the OP uses his/her machine.

Me neither. Not all DDR2 machines can take DDR3 either.

---

### Post by Cyber72 on 2012-10-09
Thanks for the advice everyone - I still can't make up my mind. 4GB DDR2 sticks that fit my laptop look to be pretty scarce already in the UK , eBay prices are higher than buying direct from Crucial and I couldn't find any other reliable brands. I have no use for 8 gigs at the moment but it looks like I will have to buy a new machine in about 4 years if I don't upgrade now.  On the bright side if the cpu burns out or something I should be able to resell them.

I thought assigning a flash stick for virtual ram might be a sensible solution but I asked in vain on *General help *for advice on how to do this with ubuntu 12.04.

---

### Post by mips on 2012-10-09
> **Cyber72 said:**
> 
I thought assigning a flash stick for virtual ram might be a sensible solution but I asked in vain on *General help *for advice on how to do this with ubuntu 12.04.

That's bot really a substitute for ram, really slow. Flash also has limited cycles but hey it's cheap.

---

### Post by fat yak on 2012-10-11
Yes I did get that you were talking about RAM, but take a look at this:

[http://www.xbitlabs.com/articles/storage/display/ssd-vs-8gb_7.html](http://www.xbitlabs.com/articles/storage/display/ssd-vs-8gb_7.html)

the conclusion from a test re more RAM or an SSD. The short answer would be, depends on what you use the computer for... but it was a serious suggestion and is worth bearing in mind.

---

### Post by Paqman on 2012-10-11
> **Cyber72 said:**
> 
I thought assigning a flash stick for virtual ram might be a sensible solution but I asked in vain on *General help *for advice on how to do this with ubuntu 12.04.

Easily done. Just tell the system it's swap space. Not really much point though, as passing anything over the USB bus will be really slow.

---

### Post by Cyber72 on 2012-10-11
The average access time of my hard disk is 23.5ms which is pretty slow. How would this compare to the usb bus. I think that once 2Gb of ram is not enough and I start using a significant amount of share I am really going to notice the slowdown. How do I tell the system to use a flash stick as swap space?

What if I put in an express card usb adapter and plug the flash sick into that. How much faster than the hard disc would that be and how much slower than ram?

---

### Post by mips on 2012-10-12
> **Paqman said:**
> Easily done. Just tell the system it's swap space. Not really much point though, as passing anything over the USB bus will be really slow.

Maybe try the Nilfs2 file system, apparently it provides big improvements on SSDs, not sure about usb stuff. Just disable the snapshot feature if it's only going to be use for swap space.

---

