---
title: "i2c designware Compatible Kernel or Disable"
date: 2015-01-14
forum: Ubuntu/Debian BASED
---

### Post by expphoto on 2015-01-14
Okay, so I'm posting this about Kali linux (debian variant). Would have posted on the Debian board, but it won't let me register. 

I have a Dell 3147 Inspiron 11 inch. And under Kali, the touchpad doesn't work.

I type dmesg, and it gives an i2c_designware, Synopsys unknown device 0x000000. I've looked all over and haven't found a solid answer on getting the touchpad working.
I run xinput and the touchpad isn't listed. 

So what I am looking for with this post is one of two things. 1. Get the kernel that supports my touchpad. 2. Disable it altogether so dmesg stops showing that error and I'll just use an external mouse or the touch screen.

Any thoughts?

---

### Post by Bucky Ball on 2015-01-14
*Thread moved to **Ubuntu/Debian BASED**.*

Please note: The main support areas here are for the official Ubuntu flavours Ubuntu, Kubuntu, Xubuntu, Edubuntu, Lubuntu, UbuntuGnome, Ubuntu Studio, and Mythbuntu.

Good luck. ;)

---

### Post by expphoto on 2015-01-15
SOLVED! Woot!

rmmod i2c_designware_platform
rmmod i2c_designware_core
blacklist i2c_designware_platform
blacklist i2c_designware_core

Fixed!

---

### Post by Bucky Ball on 2015-01-15
Excellent news. Please mark as solved to help future travelers. See the second link in my signature for how. Thanks.

---

