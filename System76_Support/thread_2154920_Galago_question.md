---
title: "Galago question"
date: 2013-06-16
forum: System76 Support
---

### Post by guacamole7 on 2013-06-16
The Galago looks like a great machine and I'm really considering buying it.  One question, if I go with the mSata drive can I easily install my own drive in the other slot?  I have an Intel SSD in another machine it so that'd be great to be able to use that as a 2nd drive in the Galago.  Thanks.

---

### Post by isantop on 2013-06-18
Easily is relative; the entire bottom panel of the laptop must be removed. The good news is that this is easy since it's held on with only screws. There's just 17 of them. ;-)

In short, yes, it's completely possible to add a second hard drive to an mSATA machine, but you do have to remove 17 screws to do it.

---

### Post by Chbribs on 2013-06-18
Is the process for upgrading RAM and adding an mSATA SSD the same? Or is the process for that different?

---

### Post by isantop on 2013-06-19
Those are on the top of the motherboard, under the keyboard. They're both also user-serviceable. The process itself is slightly different.

---

### Post by semhustej on 2013-06-24
Hello,
I have a related questions.
I am thinking of purchasing Galago and I plan to purchase 240GB SSD. I don't want to have Intel SSD inside because of the SandForce controller (I want my drive to be encrypted). So the options either Crucial M500 or M4 mSATA. M500 has shown big idle consumption (over 1W) in standard idle mode (see [here]("http://www.anandtech.com/show/6884/crucial-micron-m500-review-960gb-480gb-240gb-120gb/9")) DIPM (Device Initiated Power Management) idle consumption is good enough, thoug. mSATA Crucial M4 is another option, but it's older technology. I'd like to have Samsung 840 inside, because of it's low power consumption and reasonable performance. 
So my questions are:
1] is the warranty of the computer voided when HDD is replaced?
2] is there any advantage of having mSATA instead of SATA drive, when I plan to have only one drive inside of the notebook? I guess there's little weight advantage, but that's not that much important for me.
3] does M500 access DIPM idle in Galago, or just standard idle?

Galago seems like a nice machine, I especially like it's low weight, 1080p matte display, powerful graphics with OSS driver and hopefully reasonable battery life.

Pol

---

### Post by isantop on 2013-06-24
Intel actually doesn't use SandForce in their 525 Series mSATA SSDs, and uses binned flash instead. Our BIOS doesn't support drive-based hardware disk encryption. Instead, I would use the option within Ubuntu.

In any case, I don't think it's going to make a huge difference when you're looking at around 1W difference or lower. The processor, screen, and motherboard together draw orders of magnitude more power, and even going from HDD to SSD is only expected to add maybe 10-15 minutes of battery power.

---

### Post by semhustej on 2013-06-24
Thanks for the answer, it's good to know that BIOS drive-based hardware encryption is not supported.
1W difference is not that much, but consider it's idle power - it will draw more all the time. Every minute of battery life is nice bonus. When I'm buying new machine I try to get the best possible option.
Are you sure Intel 525 doesn't use SandForce? Some internet sites say different, e.g. [here]("http://www.anandtech.com/show/6725/the-full-intel-ssd-525-review-30gb-60gb-120gb-180gb-240gb-tested") or [here]("http://www.tomshardware.com/reviews/ssd-525-msata-review,3449.html").

---

### Post by isantop on 2013-06-24
The Tom's Hardware page has this to say (On the final words page):

> The SSD 525 family does enjoy 128-bit AES encryption, though, along with enterprise-class 1016 uncorrectable bit error rates, end-to-end data protection, and revised LLKi firmware. Also featured on the drives is thermal monitoring and protection, set to trip at 70 degrees Celsius if things get too warm. **Moreover, Intel forgoes SandForce's RAISE cross-die redundancy feature**, preferring instead to rely on binned flash and extra over-provisioning for longevity. Rather than devoting an extra die worth of NAND to parity, that space is used for OP. The 30 GB model has 11% OP; the other models run closer to 14%.

That said, it appears it may actually use the SandForce controller. What was the reason you wanted a drive without it?

---

### Post by semhustej on 2013-06-25
The reason I don't want to use SSD with SandForce controller  is that it's very fast with compressible data, but not so fast with incompressible data. Software encrypted partition behaves as completely incompressible data, thus the speeds are lower. The results are not catastrophical, of course, but software encryption and SandForce controller are not very good combination. At least that's what I've read.
I think I'll get the M500, hopefully it will idle in DIPM mode.

---

