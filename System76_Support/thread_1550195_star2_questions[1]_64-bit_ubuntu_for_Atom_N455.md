---
title: "star2 questions[1]: 64-bit ubuntu for Atom N455?"
date: 2010-08-10
forum: System76 Support
---

### Post by tlroche on 2010-08-10
> Date: 5 Aug 2010 11:43:34 -0600
Message-ID: <20100805174334.9253.qmail@system76.com>
Subject: System76's 2nd Gen Starling NetBook Takes Flight
From: [email]system76@system76.com[/email], Inc. <info@system76.com>

> Today System76 starts shipping the 2nd generation Starling Netbook.

[presumably model=star3]("http://ubuntuforums.org/showpost.php?p=9687566&postcount=7")

> > See the Starling NetBook at [http://www.system76.com/starling](http://www.system76.com/starling)

there I note

[LIST]
[*]Operating System: Ubuntu 10.04 Netbook Edition (Lucid Lynx) 32 Bit Linux
[*]Processor: Atom N455 @ 1.66 GHz with Hyper-Threading
[/LIST]

However [Intel says]("http://ark.intel.com/Product.aspx?id=49491")

> [http://ark.intel.com/Product.aspx?id=49491](http://ark.intel.com/Product.aspx?id=49491)
> Instruction Set	64-bit

So I'm wondering, why not put a 64-bit Ubuntu on the star3?

TIA, Tom Roche [Tom_Roche@pobox.com]

---

### Post by jml on 2010-08-10
My guess is that even if the chip will support 64 bit OS, given the modest specifications of the Atom processor, one will probably get better performance out of a 32 bit OS.

Joe

---

### Post by thomasaaron on 2010-08-11
Great question! Here's two great answers (if I do say so myself). ):P

1. There is no Netbook Edition in 64-bit.

2. The Starling doesn't support 4GB of RAM. So, 32-bit is just as good.

---

### Post by Rotund on 2011-01-03
> **thomasaaron said:**
> Great question! Here's two great answers (if I do say so myself). ):P

1. There is no Netbook Edition in 64-bit.

2. The Starling doesn't support 4GB of RAM. So, 32-bit is just as good.

Actually, number 2 is irrelevant as 32-bit Linux supports PAE.  This means it can access >4GB of RAM, just not in a single process.

---

### Post by isantop on 2011-01-05
Actually, 32-bit Ubuntu only supports PAE with a special kernel, and that doesn't receive as wide of community support anyway. however, we are switching to 64-bit on all available computers (Including the Star4 when the images are merged for 11.04. Soon there will only be two different types of Ubuntu; 32-bit and 64-bit.

---

### Post by rdelfin on 2011-01-06
My Starling 3 has the following processor: 
Intel Atom N455 @ 1.6 GHz
 

But now I see that System76 has decided to ship this very same model (star3) with:
Dual Core Atom N550 @ 1.50 GHz 


I know a dual core processor can make a big difference when running multiple applications.  I'm just curious if someone here can explain in a simple way how much better this new processor performs compared to the one the star3 got shipped with first.  

And also, can a processor be changed in the mother board of my star3 just as one would change shirts?  (I apologize if my question sounds stupid, I just don't know).

---

### Post by isantop on 2011-01-07
Actually, it is a new model (Star4), and we simply use the same case. 

The processors in our netbooks are soldered onto the motherboard to save space, so they unfortunately can't be upgraded. This may be something we'll look into later, but I'm not aware of anything regarding that right now.

---

### Post by tlroche on 2011-01-07
OK, so to net this out, 3 questions:

> **rdelfin said:**
> now I see that System76 has decided to ship this very same model (star3) with:
Dual Core Atom N550 @ 1.50 GHz 


> **isantop said:**
> Actually, it is a new model (Star4), and we simply use the same case.

First question should be (pun intended) binary:

1 The currently-shipping Starling is 64-bit-capable, but currently ships with 32-bit Lucid: correct?

> **isantop said:**
> we are switching to 64-bit on [...] Star4 when the images are merged for 11.04

The following questions request answers which are understood to be fuzzier, more approximate, and have all usual caveats regarding forecasting applied:

2 When will the Starling likely begin to ship with 64-bit Natty?

and with apologies for threadjacking (feel free to break this out separately),

3 With which default desktop will the 64-bit-Natty Starling probably ship?

---

