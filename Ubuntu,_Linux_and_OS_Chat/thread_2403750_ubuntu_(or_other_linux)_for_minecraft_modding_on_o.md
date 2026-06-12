---
title: "ubuntu (or other linux) for minecraft modding on older pcs?"
date: 2018-10-15
forum: Ubuntu, Linux and OS Chat
---

### Post by lb96179 on 2018-10-15
Sorry if this is the wrong forum, but I'm trying to work out (hopefully without too much trial and error) whether ubuntu is a good choice for my purposes.

My kids want to do minecraft modding, so I've set up a couple of older pcs with Ubuntu 18.04 and the requisite software. It actually works pretty well - the frame rates are decent, the systems are responsive and so on.

Since the systems are a little older (details below) I wonder if a smaller linux distribution (lubuntu or some such), might be a better choice.
The other relevant factor here is that the linux competency required shouldn't be too great - something like Ubuntu, no problems, advanced heroics required not what we're looking for.

One of the devices has an Intel Core™ i3 CPU M 330 @ 2.13GHz with 4gb ram, small ssd, tend to use wired connection that it has wifi.
Other system has a similar CPU, slightly better inbuilt graphics, 8 gb ram but only hdd, again tend to use wired connection though has wifi.

Tips on speeding up running of this software on linux and any other helpful advice much appreciated.

---

### Post by wildmanne39 on 2018-10-15
*Thread moved to **Ubuntu, Linux and OS Chat for a more appropriate fit**.*

---

### Post by mastablasta on 2018-10-16
> **lb96179 said:**
> 
One of the devices has an Intel Core™ i3 CPU M 330 @ 2.13GHz with 4gb ram, small ssd, tend to use wired connection that it has wifi.
Other system has a similar CPU, slightly better inbuilt graphics, 8 gb ram but only hdd, again tend to use wired connection though has wifi.

Tips on speeding up running of this software on linux and any other helpful advice much appreciated.

your bottleneck is likely the GPU. 

1. you will get **minor improvement** if you install a desktop that doesn't require GPU acceleration. from the Ubuntu family your options are Xubuntu, Lubuntu. Mate (without any compiz or similar stuff). you could also go even lighter but that might make it complicated and you might not see that much gain.

2. you will get a **major improvement** with a descent dedicated GPU. for minecraft it doesn't need to be top of the line. Nvidia or AMD that go for about 60-70 EUR here (they are probably less in US and elsewhere) will increase performance a lot. however if your machines are laptops then you can only do the minor improvement above.

i play minecraft and many older games under windows xp on single core AMD cpu with nvidia GT 730. i can run most games that have directx9 support with very little issues. minecraft is very fluent (lags when i trigger many TNT). i know soem of the stuff would work even faster on linux. i am still in planning stage of movement to it. 
the other PC is old dual core celeron E3300 with 2 Gb ram and old ATI 256MB GPU. minecraft runs there well, but more or less on medium settings. if i could put a modern GPU in it, it would again be running "super fast".

---

### Post by lb96179 on 2018-10-16
Thanks mastablasta.
I'll look into 1, I was thinking that might be the case.
Unfortunately the devices are laptops so I think adding a dedicated GPU is not possible cheaply - is that correct?
Kind regards

---

### Post by mastablasta on 2018-10-16
> **lb96179 said:**
> 
Unfortunately the devices are laptops so I think adding a dedicated GPU is not possible cheaply - is that correct?

correct. you can still try a lighter desktop. maybe it will help.

---

### Post by lb96179 on 2018-10-17
Tried lubuntu, seems to be a bit quicker. Thanks.

---

