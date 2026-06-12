---
title: "No problems running Ubuntu 17.04 on new Lenovo Ideapad 110-15isk"
date: 2017-02-19
forum: Ubuntu Development Version
---

### Post by rrnbtter on 2017-02-19
Greetings,$248 from Best Buy 
Lenovo 110-15isk  
All Intel System with 1Terabyte Hard Drive, 4 Gig RAM, 15.6 in Display, Bluetooth, WIFI, HDMI
Result of install is "Purrfect".  

What works = WIFI, Bluetooth, HDMI, F-keys, USB3, USB2
What doesn't work = nothing.

How I installed.
Zapped Windows 10
In BIOS Changed UEFI to Legacy.
Moved USB/DVD to first boot order.
Used 17.04 USB Startup Disk 
Enabled Proposed in Updates which gave me the 4.10 kernel, Nice!

900 Meg /Boot
5 Gig swap
15 Gig /Root
956 Gig /Home
Designated the 256Meg EUFI Partition (which i didn't delete) for the reserved boot sector .

Boot time from the 5600 RPM HD is 3.56sec Kernel,  13.5sec userspace
Dislikes = funky right shift key is hard to accept. Everything else is nice.

Opinion of Zesty
On this I have to eat some humble pie.  Zesty on a new modern system is just great. I even like the Gnome Software Center that I bad mouthed in an earlier post. Everything is fast and crisp with no apport errors popping up. 

I have not tested Unity 8 so far. Still getting my basic needs setup in Unity 7. 
This is a nice computer if you need a cheap fix. I will need to remap the right shift key though.

---

### Post by jbicha on 2017-02-19
I recommend that you do not enable [proposed]("http://askubuntu.com/q/785414/1579") during the development cycle.

---

### Post by rrnbtter on 2017-02-19
Greetings,
@jbicha, Thanks, I appreciate your well deserved concern about proposed.  However I have been running every dev version since Natty with proposed enabled. A few reinstalls never hurt anybody. It shortens the learning curve.  My post has more to do with sharing my testing experience than looking for advice. But your fears about Proposed are well founded. Not for someone who can't do a retro for sure.  Also, I've never lost data with my partition scheme. Basically using the same "Home" that I started with years ago.  The boot partition is set to 900 Meg so I have room for RC kernels.  My old Toshiba Laptop lasted seven years and every upgrade used the same Home partition,

---

