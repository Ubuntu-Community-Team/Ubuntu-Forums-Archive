---
title: "64bit computing?"
date: 2007-11-30
forum: The Cafe
---

### Post by blithen on 2007-11-30
Anyone want to help me with a ton of 64bit questions on msn? We could do it here, just I find it's easier IMing. They aren't really help questions just a few general things I should now about 64bit. That's why I'm posting here in the cafe.
[email]blithen101010@hotmail.com[/email]
There is my email if you want to help.

Though if this is inappropriate to ask then just tell me and I will ask them in the forums instead.

Good point Nathan,  I guess lets get started.

Would a harddrive on a 64bit computer be different then on a 32bit?
Can I run 32bit Ubuntu on a 64bit computer? (I don't intend to I was just wondering)
Why won't my graphics card on my new computer fit into my new one? (Does being a 64bit computer affect that?)
How buggy are 32bit programs on a 64bit computer?

---

### Post by -grubby on 2007-11-30
what's wrong with asking them here now that you've started a whole thread? :D?

---

### Post by blithen on 2007-11-30
There you go. I'm sure I will have more in the future though.

---

### Post by NullHead on 2007-11-30
Ask away! Please!

---

### Post by frup on 2007-11-30
> **blithen said:**
> 
Would a harddrive on a 64bit computer be different then on a 32bit?

I don't see how really. I could be very wrong though. The most likely difference you would encounter is the change from IDE to SATA.
> **blithen said:**
> 
Can I run 32bit Ubuntu on a 64bit computer? (I don't intend to I was just wondering)

Seen it done.
> **blithen said:**
> 
Why won't my graphics card on my new computer fit into my new one? (Does being a 64bit computer affect that?)

Again like the HDD... probably a hardware thing, One might be AGP and the other PCI or something. you mean Old to New too don't you?
> **blithen said:**
> 
How buggy are 32bit programs on a 64bit computer?
Can't say because I haven't personally run it but as far as the forums go, things seem to be getting better and the problems are flash and codecs.

---

### Post by blithen on 2007-11-30
Thanks for the input!

---

### Post by timpino on 2007-11-30
> 
Would a harddrive on a 64bit computer be different then on a 32bit?
The files are stored in exactly the same way, using the same filesystems. SATA harddrives can be used in IDE mode with a converter, but if you have SATA on your motherboard you want to run SATA.

> 
Can I run 32bit Ubuntu on a 64bit computer? (I don't intend to I was just wondering)
Yes, alot of people do this, in fact most OS:es are 32 bit while almost all CPUs sold today are 64bit, This is mostly because of the vast amount of applications available for 32bit OS:es

> 
Why won't my graphics card on my new computer fit into my new one? (Does being a 64bit computer affect that?)

That is because of PCIe, its the "new AGP port" simply put, it offers better speed than AGP ports, if you already have a PCIe graphics card that you have run on 32bit it will work in 64bit (granted you can find drivers for it)

> 
How buggy are 32bit programs on a 64bit computer?

there is a big difference between running 32bit applications in 32bit OS:es on 64bit machines and running 32bit applications in 64bit OS:es on a 64bit machine. The first is really simple, the other is a bit trickier, not impossible though.

---

### Post by regomodo on 2007-11-30
64bit support is a lot better in Linux than XP. I've got hardware i can't use in XP as there are no drivers for XP64 yet for 32bit it's fine. I'm thinking of downgrading.
Additionally 64bit vista won't work on my setup. BSOD every boot.

Why MSN? Why not an irc channel?

---

### Post by bash on 2007-11-30
The only thing with 32bit programs in a 64bit Ubuntu you have to watch out for is that you just can't install them "normally" like 64bit programs. It requires some tweaking. I switched recently to 64bit and the only program I had to do that for was Skype that is only available in 32bit. But there is a thread on here which has a nifty terminal command you just need to copy and paste and you have Skype running in about 1 minute (just depends on how fast you internet connection can download Skype ;) ). Besides that everything works flawlessly. Got flash running through normaly apt-get install. Codecs are working normally as well. So can't complain. Seriously it was so smooth Im kinda expecting for some problem to pop up.

---

### Post by atlfalcons866 on 2007-11-30
jfs is a 64 bit file system. It can run on 32bit perfect.

---

### Post by svtfmook on 2007-11-30
#1, there is no 32bit or 64 bit hard drives.  there is 32bit data transfer on some hard drives, but that has nothing to do with 32/64 bit architectures.

#2 yes.  i ran 32bit feisty on my 64bit AMD system for a long time.  you're just not taking advantage of your 64bit architecture processor and ram

#3 not sure what you mean.  but 64 bit has nothing to do with video cards.  is your card AGP and you're trying to put in in a pci/pci x16 slot? or vise versa?

#4 not buggy at all as long as you have the 32 bit libraries installed

---

### Post by blithen on 2007-11-30
SWEET!!! Thanks for the input guys. I was really scared. And I forgot that there was different types of graphics card which is probably why my old one didn't fit. I'm now confident to move ahead with my new computer. And thanks again guys for helping me.

---

