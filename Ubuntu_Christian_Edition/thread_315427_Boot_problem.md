---
title: "Boot problem"
date: 2006-12-09
forum: Ubuntu Christian Edition
---

### Post by Rocker452 on 2006-12-09
I just installed Ubuntu CE 2.0 on my laptop but it won't complete the boot up. Using the recovery option I get a bug message about a soft lockup on cpu#0 and the boot stalls. What does that mean and how do I fix it. Thanks for any help. Just for info I'm on a Dell E1505 with a T2400 1.83 ghz dual core cpu.

---

### Post by mhancoc7 on 2006-12-09
> **Rocker452 said:**
> I just installed Ubuntu CE 2.0 on my laptop but it won't complete the boot up. Using the recovery option I get a bug message about a soft lockup on cpu#0 and the boot stalls. What does that mean and how do I fix it. Thanks for any help. Just for info I'm on a Dell E1505 with a T2400 1.83 ghz dual core cpu.

Sorry for your trouble. I am not sure what is going on there. Since Ubuntu CE v2.0 is basically Edgy with some customizations it is probably an Edgy issue. Have you ever installed Edgy on your system. If so and it worked then we will know it is an issue specific to CE.

Thanks, Jereme

---

### Post by Rocker452 on 2006-12-09
I haven't installed the regular Edgy on this machine but I have found what the problem is. It seems it has to do with the fact it's a dual core processor. I can go into the BIOS setup and turn off support for multi processors and it boots fine. I would be interested if others with dual core processors have had this problem and if they have a fix for it.

---

### Post by Darrious on 2006-12-09
I don't have dual processors, but  install first then try to see if it runs with dual processors.

---

### Post by Rocker452 on 2006-12-09
Well I installed the regular version of edgy elf and have no problems booting and have the multi processor support enabled in setup so it must be a problem in the CE version.Anyways thanks for the help and maybe it was just a quirk of this install.

---

### Post by Darrious on 2006-12-09
One, it is edgy eft, not edgy elf.:mrgreen:

Two, you could always run the [convert_me_script](http://www.christianubuntuukmirror.co.uk/ubuntuce/scripts/convert_to_ubuntu_christian_edition_edgy.tar.gz)

---

### Post by pvegdahl on 2006-12-15
I ran into this same problem with basic Edgy Eft on my e1505. The problem was related to booting with the wireless module turned off (Using Fn+F2). However I think this issue may have been resolved in an update earlier this week.

---

### Post by doobit on 2006-12-15
There are some issues with the Edgy live CD and some hardware. I can't install from the live CD on one of my machines, but I can use the alternate install Cd with no problem. Interesting is the fact that I was able to install from the Ubuntu CE 2.0 live CD on the same machine!

---

### Post by pvegdahl on 2006-12-15
> **pvegdahl said:**
> I ran into this same problem with basic Edgy Eft on my e1505. The problem was related to booting with the wireless module turned off (Using Fn+F2). However I think this issue may have been resolved in an update earlier this week.

Never mind about that last part. The bug seems to still be alive and well...

---

