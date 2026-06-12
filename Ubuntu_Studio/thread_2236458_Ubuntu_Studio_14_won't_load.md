---
title: "Ubuntu Studio 14 won't load"
date: 2014-07-26
forum: Ubuntu Studio
---

### Post by CrimsonEquinox on 2014-07-26
Hello,

I have made about 5 or 6 attempts at this and gotten no where.  My rig has two Win7 Pro installs, one for general computing and one for testing stuff that will likely nerf things.  In the past, Ubuntu 12, I was able to successfully triple-boot my system without a problem.  Here are the drive layouts as they stand.

500gb drive
#1 100mb Windows recovery
#2 Extended partition
     #2a 200mb /boot
     #2b 8gb linux-swap
     #2c 194gb /
#3 185gb Win7 Pro
#4 80gb Win7 Pro Test

(the sizes are approximate give or take a meg or gig)

Every time I reboot I only see the Windows Bootloader and there is no hint that grub is even there.  I am going to dig through my files tomorrow and see if I still have an ISO for 12 so that I can see if the problem is with my system or with 14.  Until then I wanted to see if there is another solution to blowing the install away again and starting over.  Odds are it is something small and obvious, but I am just to frustrated to see it at the moment.

Later,

---

### Post by CrimsonEquinox on 2014-07-27
Ok, so here is the solution.

Apparently the "Default devise for the bootloader" was not defaulted to the right place.  In some cases /dev/sda is correct but in this case I have 7 Sata devices and for some reason I had to change the "default boot oader device" so that it would be installed on /dev/sde which incidently is the drive that I was installing Linux on in the first place.  Anyway, don't know the how's or the why's but it now boots through linux and windows without issue so it's a win.

---

### Post by Bucky Ball on 2014-07-27
Good news. Please mark thread as 'solved' to help others by following the second link in my thread. Good luck.

---

