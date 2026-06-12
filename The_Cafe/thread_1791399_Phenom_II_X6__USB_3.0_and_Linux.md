---
title: "Phenom II X6 / USB 3.0 and Linux"
date: 2011-06-26
forum: The Cafe
---

### Post by CharlesA on 2011-06-26
Hiya,

Does anyone know how support for this processor is in Linux?

I recall seeing issues relating to the i7s a while ago and was wondering if the new AMD processors had the same problems.

I was looking at getting [this combo]("http://www.newegg.com/Product/ComboBundleDetails.aspx?ItemList=Combo.644157").

Is anyone running a x6 proc?

Thanks,
Charles

---

### Post by Lucradia on 2011-06-26
ubuntu works fine, and can get a Phenom II X6 fully. However, you must use a motherboard that allows overvolting/overclocking via the BIOS to use overclocking in Linux. (The overclocking software provided by AMD is via Windows, as a failsafe so that if something goes wrong, your BIOS doesn't get locked out via constant reboot.)

Since you have the 1090T, you don't need to worry about the processor not turbo'ing properly like the 1100T does (it turbos automagically like the i7, different instruction though, so it may be more compatible with linux.)

I will be getting the 1100T, and may install Linux aside Windows. So if you know a benchmark that can tax the AMD 1100T enough to cause it to turbo, I can test it for you.

---

### Post by CharlesA on 2011-06-26
Thanks. I'm currently using a dual core as my file server/VM box, but I'm thinking of upgrading since I'd like to run more VMs at once (current box has 6GB of RAM, thinking of bumping that up to 16GB).

What do you mean about it not "turboing" properly?

---

### Post by Brent0 on 2011-06-26
> **Lucradia said:**
> ubuntu works fine, and can get a Phenom II X6 fully. However, you must use a motherboard that allows overvolting/overclocking via the BIOS to use overclocking in Linux. (The overclocking software provided by AMD is via Windows, as a failsafe so that if something goes wrong, your BIOS doesn't get locked out via constant reboot.)

Since you have the 1090T, you don't need to worry about the processor not turbo'ing properly like the 1100T does (it turbos automagically like the i7, different instruction though, so it may be more compatible with linux.)

+1 Should work just fine.
The motherboard you chose is also great for overclocking. I wouldn't recommend software overclocking anyway. From experience, it can get unstable and lacks the depth of features on the BIOS. ;)

---

### Post by LowSky on 2011-06-26
USB3 works amazingly for me. Worked right out of the box. I was getting steady 40+ Mbps with a 5400RPM laptop drive.

Can't say anything about PII x6, but my PII x2 is unlocked to 4 cores and overclocked 500Mhz and runs amazing. I can't see why six cores can't work for you, a lot of people here have them listed in the signatures. Linux has been multi-core ready for so very long.

---

### Post by Lucradia on 2011-06-27
> **CharlesA said:**
> What do you mean about it not "turboing" properly?

The entire Lynnfield processor line for i7 cannot turbo automatically, and thus, you are stuck with the lowest speed. Some Clarksdale line i7s do the same. This is because the auto-turbo system of the i7 is software-based, not hardware based.

We don't know how AMD's auto-turbo system works however. If it's pure hardware, requiring no drivers to turbo, it will work with Linux.

---

### Post by CharlesA on 2011-06-27
Thanks for the info. Didn't even know about that.

---

### Post by 3Miro on 2011-06-27
When the new Phenom II X6 came out, the kernel needed a patch to work properly, but it was done almost immediately and this was over a year ago. Ubuntu 10.04 and everything newer works great. I like playing with distribution and I have tried all Ubuntus, Fedore 14/15, Arch, Gentoo, Slackware 13, Debian stable and others, they all work great.

I have USB 3.0 port, but I have no USB 3.0 devices, so I have not tried that.

---

### Post by CharlesA on 2011-06-27
> **3Miro said:**
> When the new Phenom II X6 came out, the kernel needed a patch to work properly, but it was done almost immediately and this was over a year ago. Ubuntu 10.04 and everything newer works great. I like playing with distribution and I have tried all Ubuntus, Fedore 14/15, Arch, Gentoo, Slackware 13, Debian stable and others, they all work great.

I have USB 3.0 port, but I have no USB 3.0 devices, so I have not tried that.

Thanks for that.

I've been using a USB 3.0 external hard drive and it works very well so far. :)

---

