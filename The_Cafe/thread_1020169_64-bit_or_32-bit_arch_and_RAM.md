---
title: "64-bit or 32-bit arch? and RAM?"
date: 2008-12-23
forum: The Cafe
---

### Post by ryaxnb on 2008-12-23
I've heard that 64-bit and 32-bit architectures are primarily separated, on x86, by how much ram is available, both real and virtual. if you have 4GB of ram (on a mobo that can see all 4gb, e.g. santarosa), it is more useful than 2gb arguably, because you're more likely to find the ability to use >4GB virtual memory useful. If you have >4GB memory, of course, you're almost certainly using 64-bit, unless you just run PAE (weirdo ;) ).

64-bit also enables more registers, which could theoretically be useful, and drops support for virtual mode, swap to real mode, and 8086-style segment addressing, in favor of one large segment. These were mostly already obsolete.

So what do you have in terms of RAM and arch?
Where by arch i mean the target processor of linux distro, have you chosen 64 or 32 target. it matters not what kind of processor you have.

---

### Post by WaeV on 2008-12-23
My PC is 64-bit with 4GB ram, I think that's what you meant.  I went with 64-bit arch.

---

### Post by ryaxnb on 2008-12-23
yes that is, i meant the arch you downloaded and use, not the computer you have

---

### Post by Frak on 2008-12-23
64-bit, but I only have 2GB of RAM (1.75GB after Nvidia takes it's part for the gfx).

---

### Post by crimesaucer on 2008-12-23
Advertised as 4GB but only shows: 3876331520 bytes = 3.61012 GB

HP puts this on the box (in the small print):

1GB = 1 billion bytes: Actual formated capacity is less.
1MB = 1,000,000 bytes


The Byte conversion charts say this....

1GB = 1,073,741,824 bytes
1MB = 1,048,576 bytes


So......

4,000,000,000 bytes = 3.72529 GB

..... and not 4GB.....



Then I lose another 117.93408 MB (or 118 MB) somewhere else?????


4 GB becomes 3.6 GBs...... that's false advertising. (Same thing on Windows Vista)

---

### Post by SuperSonic4 on 2008-12-23
> **crimesaucer said:**
> Advertised as 4GB but only shows: 3876331520 bytes = 3.61012 GB

HP puts this on the box (in the small print):

1GB = 1 billion bytes: Actual formated capacity is less.
1MB = 1,000,000 bytes


The Byte conversion charts say this....

1GB = 1,073,741,824 bytes
1MB = 1,048,576 bytes


So......

4,000,000,000 bytes = 3.72529 GB

..... and not 4GB.....



Then I lose another 117.93408 MB (or 118 MB) somewhere else?????


4 GB becomes 3.6 GBs...... that's false advertising. (Same thing on Windows Vista)

Not quite, 1MB is actually 1,000,000 bytes so it's true. The difference is they are selling it as 4GB not 4GiB. 1 GiB is 2^30 bytes

---

### Post by Kelsus on 2008-12-23
64 bit arch -- with 8 Gigs of installed RAM...

---

### Post by SuperSonic4 on 2008-12-23
> **Kelsus said:**
> 64 bit arch -- with 8 Gigs of installed RAM...

Does 8gb make a significant difference compared to 4gb? I mean for basic firefox, kmess, amarok and dolphin with occasional k9copy and k3b? I ask because RAM is next on my list to upgrade

I have 4gb ram and a 64 bit OS

---

### Post by Kelsus on 2008-12-23
> **SuperSonic4 said:**
> Does 8gb make a significant difference compared to 4gb? I mean for basic firefox, kmess, amarok and dolphin with occasional k9copy and k3b? I ask because RAM is next on my list to upgrade

I have 4gb ram and a 64 bit OS
I have one setup with 4gb installed and another with 8 installed.  The difference for firefox and amarok is minimal &#8211; if noticeable at all.  I use the extra RAM for manipulating pictures and for computation.  I do not use the other applications enough to say.  RAM is so much cheaper nowadays it was really not a big leap to build a rig with 8gb instead of 4.

---

### Post by crimesaucer on 2008-12-23
> **SuperSonic4 said:**
> Not quite, 1MB is actually 1,000,000 bytes so it's true. The difference is they are selling it as 4GB not 4GiB. 1 GiB is 2^30 bytes

I know I am far from expert, but I only said this because they advertise it as 4GBs of RAM not 3.6GBs of RAM.... and not 4 GiB (gibibytes)


chart:

[http://www.t1shopper.com/tools/calculate/](http://www.t1shopper.com/tools/calculate/)

1,048,576 bytes = 1 Megabytes

From wikipedia: [http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

> Although most manufacturers of hard disk drives and flash-memory disk devices define 1 gigabyte as 1,000,000,000 bytes, the computer operating systems used by most users usually calculate size in gigabytes by dividing the total capacity in bytes (whether it is disk capacity, file size, or system RAM) by 1,073,741,824. This distinction is a cause of confusion, as a hard disk with a manufacturer-rated capacity of 400 gigabytes may be reported by the operating system as only 372 GB large, depending on the type of report.

As "memory" shouldn't it be: 

> The usage of the word "gigabyte" is ambiguous: the value depends on the context. When referring to RAM sizes and file sizes, it traditionally has a binary definition, of 1024*3 bytes.



I also read how it can also mean GiB:

> When referring to disk storage capacities and the transmission of data over telecommunication lines, it means exactly 1000*3 bytes, since the prefix "giga-" refers to 1000 "megas". In order to address this confusion, currently the International Electrotechnical Commission (IEC) promotes the use of the term "gibibyte" for the binary definition. 


[http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)

---

### Post by ushimitsudoki on 2008-12-23
64-Bit, 8G

Mostly put in more RAM for audio processing and to slide a little more memory over to virtualization when needed.

---

### Post by igknighted on 2008-12-24
What would 3gb ram be? it's not less than 2gb, but it isn't 4gb.  And I use 64 bit.

---

### Post by hanzomon4 on 2008-12-24
I'm trying to install 64bit Ubuntu on my macbook pro. With things like flash and java going 64bit there's very little draw back. I do wonder however if the ram speed is more important then the capacity once you go past 4gb.

---

### Post by tad1073 on 2008-12-24
> **hanzomon4 said:**
> I'm trying to install 64bit Ubuntu on my macbook pro. With things like flash and java going 64bit there's very little draw back. I do wonder however if the ram speed is more important then the capacity once you go past 4gb.

Ram speed would be a factor. DDR2 1066 will be much faster than DDR2 800

---

### Post by Chame_Wizard on 2008-12-24
64 Bit arch and 1024 MB DDR-RAM 400:guitar:.

---

### Post by markp1989 on 2008-12-24
64bit, and 2gb ram. 

my cpu supports 64bit, so i didnt see any reason not to chose 64bit

---

### Post by Thelasko on 2008-12-24
64-bit and 1GB RAM.  Yup, that's how I roll.
I asked for more RAM for Christmas, but I doubt I'll get it because no one in my family knows what RAM is, let alone what kind I need.

P.S. I buy pre-built machines with the minimum amount of RAM, because it's usually cheaper than building it myself.  I've found that retailers usually sell the machines at a discount and then try to make a profit on RAM upgrades.

---

### Post by Frak on 2008-12-24
> **hanzomon4 said:**
> I'm trying to install 64bit Ubuntu on my macbook pro. With things like flash and java going 64bit there's very little draw back. I do wonder however if the ram speed is more important then the capacity once you go past 4gb.
I've found RAM speed to be nearly unnoticeable unless you're using PC133 and instantly upgrade to DDR2 1066. I've been unable to detail the differences between my DDR2 677 and DDR2 1066 RAM.

---

### Post by Eisenwinter on 2008-12-24
64 bit, 1GB of RAM, DDR-400.

---

### Post by nick09 on 2008-12-24
You need to review some math here. 1 byte = 8 bits. The reason you see less than what is advertised on hard drives and the such is because the computer counts in base-2(binary) than us humans who count in the base-10. Therefore you will see less than that was advertised on a product.

Read this article and it will help to understand a bit more:
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

---

### Post by init1 on 2008-12-24
> **SuperSonic4 said:**
> Does 8gb make a significant difference compared to 4gb? I mean for basic firefox, kmess, amarok and dolphin with occasional k9copy and k3b? I ask because RAM is next on my list to upgrade

I have 4gb ram and a 64 bit OS
I'm certainly not an expert on this, but 4GB is probably way more than enough for what you need.

---

### Post by SomeGuyDude on 2008-12-24
32-bit Arch with a 64-bit proc and 2GB of RAM.

Given that, with every application I regularly use running right now, I'm only using up 360MB, I have no idea what I'd need 4GB for. Additionally, since the 64-bit benefits don't kick in until in the 4GB area, I have no need for that version.

I ran Arch64 for a little while, but it ran a little hot, was heavier on the CPU, and ate battery life faster than its 32 bit little brother. Thus, here I am.

---

### Post by crimesaucer on 2008-12-25
> **nick09 said:**
> You need to review some math here. 1 byte = 8 bits. The reason you see less than what is advertised on hard drives and the such is because the computer counts in base-2(binary) than us humans who count in the base-10. Therefore you will see less than that was advertised on a product.

Read this article and it will help to understand a bit more:
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)


Was this directed at me? Maybe it was directed at my post #5.... which was me ranting about my initial expectation of buying a computer that advertised 4GBs of available RAM..... and I expected that it would be the "binary" measurement of: 4096MB


Only to find out latter that HP had written a statement on the box in small print that said it used the metric measurement of: 1MB = 1,000,000 bytes plus it will register as less....  


If the "check your math" comment was for me, then I will have to direct you to my 2nd post "#10" that has the exact same wikipedia link (same confusion section)..... as well as the conversion tables with the same explanations. If none of that comment was at me than I'm sorry.


As for HP advertising 4GB RAM..... I think that they don't mind using the confusion of the metric and binary translations to advertise more RAM.....


4GBs sounds a lot better than 3.6GBs.

---

### Post by jespdj on 2008-12-25
> **ryaxnb said:**
> 64-bit also enables more registers, which could theoretically be useful, ...
For processor-intensive programs (video or audio encoding or decoding, or envcryption, for example), the performance difference is not theoretical, but very real.

---

### Post by diskotek on 2008-12-25
i have 64 bit amd arch, and 1 gb ram with (32 mb ati radeon shares)

---

### Post by mips on 2008-12-25
> **jespdj said:**
> For processor-intensive programs (video or audio encoding or decoding, or envcryption, for example), the performance difference is not theoretical, but very real.

In this scenario the more cores you have the better as well ;) 64bit OS on a Quad core just flies with this.

---

