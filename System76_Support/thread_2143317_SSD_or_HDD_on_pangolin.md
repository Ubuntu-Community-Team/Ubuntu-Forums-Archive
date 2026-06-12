---
title: "SSD or HDD on pangolin"
date: 2013-05-08
forum: System76 Support
---

### Post by jsmeche on 2013-05-08
Hi,

I am planning on buying a pangolin performance in a few days. I have all of the specs nailed down except the choice between a small ssd or a 750GB 7200rpm hdd. I plan on going with the 2.40ghz i7 and 16 gb of ram just because it's cheap and there may be a day when I actually need something like that. So will running a hdd have any significant impact on the performance of the system as a whole? If so, is lvm able to handle a small ssd and a big hdd together to give me the best performance possible while still giving me a simple configuration? I have heard of people putting all the system stuff on the ssd and files on the hdd by splitting it up into different partitions. But I want the software to be able to know what is used most often and put that on the ssd and other stuff that is not often used put on the hdd. Any ideas?

Thanks

---

### Post by isantop on 2013-05-08
SSD.

Unless you absolutely *need* to have the storage built-in, it's better to use external hard drives. The speed difference is fantastic.

---

### Post by pqwoerituytrueiwoq on 2013-05-08
the 3.9 kernel supports caching which is what it sound like you are asking for (" I want the software to be able to know what is used most often and put  that on the ssd and other stuff that is not often used put on the hdd"), saucy salamander's kernel will be the 1st ubuntu release support caching
you can use a hdd+ssd without caching, this will extend the life of the ssd, i did make a install guide for this here in the guide for that 
[http://www.youtube.com/watch?v=2sPGEwqoXA0](http://www.youtube.com/watch?v=2sPGEwqoXA0)
a pure ssd setup is faster than a hdd+ssd or hdd setup

from looking at the configure page for the Pangolin only lets you use a single drive ssd or hdd not both
you can replace a dvd drive with a adapter for a 2.5" drive like [this]("http://www.amazon.com/dp/B0056EW4A4") so you can have a second internal disk drive
i have heard system76 will do custom setups upon request, but i'm not sure if that would cover doing that
using a ssd+hdd will increase the cost,  hdd cost 50-100 depending on the capacity, and a ssd cost about 1$ per GB, in a hybrid setup like i did a 30gb is plenty but you may as well get a 60gb at the price of a 30gb 

you could make those changes after you get the laptop, am am sure system76 will tell you how to restore there modifications so it will work right (drivers)
not sure if replacing the dvd drive would void the warranty or not
it is also possible to move a install to a ssd and split it into multiple partitions, i just did this for my mom last weekend

---

### Post by Leslie Dorner on 2013-05-10
It's better that you get an internal ssd and buy a high capacity external drive to store your data. You can always purchase newer, faster, and larger high capacity external drives to attach to your PCs whereas an internal drive is going to be replaced much less frequently due to wear and tear. SSDs are wickedly fast.

I tried the opposite scenario and I was dissatisfied by the results. I have a large 1 TB 2.5" 9.5 mm hard drive and it was dog slow compared to my crucial m4 128 GB SATA-3 SSD. I found myself copying the same data I had on my external drives to my internal 1 TB hard disk drive and it was just redundant. It was nice to be able to carry all of that data, but it was just too slow.

If you get 120 or 128 GB SSDs, then you'll be surprised by how much you can download and install in such limited space. I managed to install Ubuntu 13.04 64 bit, tons of software applications including 3rd party, closed source, and proprietary stuff, and I was able to install Humble Indie Bundle V and Double Fine Bundle and Steam for Linux and Windows including Civilization V, Portal, and Portal 2. Playing PC games is incredibly fast on a SSD and it's fluid and dynamic. Hard drives are much slower and loading scenes take 5 times as long on 5400 RPM hard drives compared to a SATA-3 SSD.

It's your time. How much is your time worth it to you? Pay a little more now and get a SSD or save up more money and get a bigger capacity SSD.

You'll thank us.

---

### Post by him610 on 2013-05-12
I ordered a PP9 about 6 months ago which included a 750GB HDD, with the intention of replacing it with a SSD at some time in the future. I replaced it about 3 months ago with a Samsung 250GB SSD. Boot time is less than 10 seconds. I thought so much of the performance increase I replaced the HDD in the laptop of my spouse with a SSD just like it a short time later. 

Cheers

---

