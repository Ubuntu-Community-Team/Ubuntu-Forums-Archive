---
title: "So I enabled UEFI in my BIOS; Reaction = O.O"
date: 2013-05-02
forum: The Cafe
---

### Post by pqwoerituytrueiwoq on 2013-05-02
My laptop shipped with this disabled, it came with win7
I was shocked with how much faster it booted an insane ~50% improvement
With UEFI on the left and UEFI off on the right
[[img]http://www.zimagez.com/miniature/screenshot-05022013-034720pm.php[/img]](http://www.zimagez.com/zimage/screenshot-05022013-034720pm.php)

---

### Post by Paqman on 2013-05-03
Interesting, but not entirely unexpected. Trying to boot modern hardware using BIOS relies on a cludgey mass of hacks held together with spit and sticky tape.

---

### Post by pqwoerituytrueiwoq on 2013-05-03
I wonder how fast that would be if i made a grub2 profile, net time i manage to get the boot menu to come up with shift i will do that (i spelled shift wrong and it look me way too long to figure out it was missing a f)

---

### Post by Slim Odds on 2013-05-03
> **pqwoerituytrueiwoq said:**
> My laptop shipped with this disabled, it came with win7
I was shocked with how much faster it booted an insane ~50% improvement
With UEFI on the left and UEFI off on the right
[[IMG]http://www.zimagez.com/miniature/screenshot-05022013-034720pm.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-05022013-034720pm.php")

How do you calculate a ~50% improvement?

I see 25.94 seconds with UEFI and 29.37 without... and that's not 50% better

---

### Post by pqwoerituytrueiwoq on 2013-05-03
the chart includes a set amount of time, on the right login is ready at 6 or 7 seconds and on the left it is ready at about 4 seconds

---

### Post by zach.detton on 2013-05-06
That's still not a 50% improvement, it's more like 25 ~ 30%. It's still an improvement either way you look at it. Perhaps I should look into enabling UEFI on my mobo.

---

### Post by Slim Odds on 2013-05-06
> **pqwoerituytrueiwoq said:**
> the chart includes a set amount of time, on the right login is ready at 6 or 7 seconds and on the left it is ready at about 4 seconds
It must be horrible having to wait for that extra 2-3 seconds to get a log in prompt.

---

### Post by pqwoerituytrueiwoq on 2013-05-06
but i am using a $80 SSD, so i better be very fast

---

### Post by Paqman on 2013-05-06
> **Slim Odds said:**
> It must be horrible having to wait for that extra 2-3 seconds to get a log in prompt.

Yeah, but why wait if you don't have to?

---

### Post by Slim Odds on 2013-05-06
> **Paqman said:**
> Yeah, but why wait if you don't have to?

Sure, but how often to you need to reboot a Linux machine?

---

### Post by Paqman on 2013-05-06
> **Slim Odds said:**
> Sure, but how often to you need to reboot a Linux machine?

Servers, only after a kernel upgrade. Desktops, all the time. I shut my desktop down whenever I'm done with it. My netbook less often admittedly, but I don't see the point in leaving a computer powered up when it's not needed.

---

### Post by pqwoerituytrueiwoq on 2013-05-06
for a desktop there is suspend, but a laptop when you don't want to drain a battery...

---

### Post by Slim Odds on 2013-05-07
> **pqwoerituytrueiwoq said:**
> for a desktop there is suspend, but a laptop when you don't want to drain a battery...
For the laptop, I use hibernation. Therefore, no reboot to bring the machine up and no power drain.

---

### Post by pqwoerituytrueiwoq on 2013-05-07
can you use hibernate if you are using a ramdisk?

---

### Post by Slim Odds on 2013-05-07
> **pqwoerituytrueiwoq said:**
> can you use hibernate if you are using a ramdisk?
I don't see why not... hibernation copys RAM to permanent disk.

---

### Post by Paqman on 2013-05-07
> **pqwoerituytrueiwoq said:**
> for a desktop there is suspend, but a laptop when you don't want to drain a battery...

I always switch my desktop off at the wall now. They suck about 8Wish constantly otherwise, even when off.

---

### Post by pqwoerituytrueiwoq on 2013-05-07
> **Paqman said:**
> I always switch my desktop off at the wall now. They suck about 8Wish constantly otherwise, even when off.Mine actually leaves power on the usb ports when it is off, and i use my space bar for a power on button

---

