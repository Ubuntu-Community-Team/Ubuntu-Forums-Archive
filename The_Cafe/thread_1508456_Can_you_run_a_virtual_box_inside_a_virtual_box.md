---
title: "Can you run a virtual box inside a virtual box?"
date: 2010-06-13
forum: The Cafe
---

### Post by Legendary_Bibo on 2010-06-13
Google could not provide me the answer. I'm just wondering...

---

### Post by kevin11951 on 2010-06-13
Yes, but the second will be severely slower due to running software VM instead of hardware.

---

### Post by Linye on 2010-06-13
Some how that question made me laugh.

---

### Post by WinterRain on 2010-06-13
> **kevin11951 said:**
> Yes, but the second will be severely slower due to running software VM instead of hardware.

I'd like to see it. I tried it once, and the second instance of vbox started up, but choked soon after. Like I said, I'd like to see it. I don't think it's possible right now.

Since the original os in vbox is emulating hardware, I don't think you can piggyback on virtual hardware.

---

### Post by Stancel on 2010-06-13
So I can use Ubuntu while I'm using Ubuntu while using Ubuntu? :lolflag:

---

### Post by rukiaEnix on 2010-06-13
yep but very sloooooooooowyly XD

---

### Post by chessnerd on 2010-06-13
You're not talking about something as simple as picture-in-picture. You're talking about running an operating system on a virtual computer inside of an operating system on a virtual computer inside of an operating system on a physical computer. 

A common question that you hear here on the forums is: Is my computer able to run Ubuntu in VirtualBox? To answer that question, you need the hardware specs. 

The same question applies here. Are the hardware specs of the virtual machine good enough?

**It has no hardware specs!** 

At least, not really. 

It only has as much hardware power as the operating system it is running in allows it to have. The same would be true of this other virtual machine, which is running in an operating system. 

You probably could get it to work, but not on a typical computer. The system needs to be *very* powerful, because only the real, physical hardware exists. With each virtual machine you layer, you get less and less access to the real hardware which is required for it to work.

---

### Post by kevin11951 on 2010-06-13
Tell you what, I will do it, I will run cli debian stable inside debian testing on a bare metal debian sid!  Wish me luck.

---

### Post by samjh on 2010-06-13
> **kevin11951 said:**
> Tell you what, I will do it, I will run cli debian stable inside debian testing on a bare metal debian sid!  Wish me luck.

I'd be more impressed if you could run Ubuntu/Wubi inside Windows inside Debian. ;)

---

### Post by marshmallow1304 on 2010-06-13
> **samjh said:**
> I'd be more impressed if you could run Ubuntu/Wubi inside Windows inside Debian. ;)

That would be cheating, for Wubi isn't virtualized.  :razz:

---

### Post by schauerlich on 2010-06-13
yo dawg, i heard you liek brown, so i put an ubuntu in your ubuntu so you can spin cubez while you spin cubez.

---

### Post by clarknick67 on 2010-06-13
> **marshmallow1304 said:**
> That would be cheating, for Wubi isn't virtualized. :razz:
 em, it must be cheating

---

### Post by Legendary_Bibo on 2010-06-13
> **schauerlich said:**
> yo dawg, i heard you liek brown, so i put an ubuntu in your ubuntu so you can spin cubez while you spin cubez.
haha, this made me laugh. It makes me think of a hyper cube.

---

### Post by john_spiral on 2010-06-13
I'm sure Slitaz could be run within Slitaz within Slitaz ...

---

### Post by cartman640 on 2010-06-13
I present to you Ubuntu 9.04 inside Ubuntu 10.04 inside Windows 7 :D

Ubuntu 10.04 is running inside VMWare and Ubuntu 9.04 inside VirtualBox, so to answer Legendary_Bibo, yes, yes you can. It's not fast though, took a good long while to install and open Firefox.

[IMG]http://imgur.com/mKwH0.jpg[/IMG]

For those who are interested, host machine is a Core 2 Quad Q6600 running at 3.2Ghz with 8Gb of RAM on Windows 7 Pro 64bit. 10.04 guest has a virtual dual core CPU with 2Gb of RAM, 9.04 runs a single virtual CPU with 512Mb of RAM.

---

### Post by Legendary_Bibo on 2010-06-13
> **cartman640 said:**
> I present to you Ubuntu 9.04 inside Ubuntu 10.04 inside Windows 7 :D

Ubuntu 10.04 is running inside VMWare and Ubuntu 9.04 inside VirtualBox, so to answer Legendary_Bibo, yes, yes you can. It's not fast though, took a good long while to install and open Firefox.

[IMG]http://imgur.com/mKwH0.jpg[/IMG]

For those who are interested, host machine is a Core 2 Quad Q6600 running at 3.2Ghz with 8Gb of RAM on Windows 7 Pro 64bit. 10.04 guest has a virtual dual core CPU with 2Gb of RAM, 9.04 runs a single virtual CPU with 512Mb of RAM.
Holy crap that's awesome. It takes a lot of power eh?
I would try it, but I'm low on CDs at the moment. My system also doesn't have quite the specs as yours.

---

### Post by MichealH on 2010-06-13
I did it on Windows once...

[IMG]http://3.bp.blogspot.com/_VHcYLjUYssM/SWPz82Vq6lI/AAAAAAAABKY/V68XUUimElc/s400/bsod.jpg.jpg[/IMG]

---

### Post by NightwishFan on 2010-06-13
That would be akin to Marco Hietala losing his voice! I am sure performance would not be too bad if you ran your host with hz=1000, and your guests with hz=100, and the noop scheduler. Also, virtualization extensions enabled in the first guest and not in the second.

---

