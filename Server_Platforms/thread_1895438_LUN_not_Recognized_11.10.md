---
title: "LUN not Recognized 11.10"
date: 2011-12-14
forum: Server Platforms
---

### Post by hifriend on 2011-12-14
Hello,

First post, been digging through the forums, no luck on the issue so i thought i would try posting.  Here is my situation.

I have an HP p2000 SAN array that connects over 8gb/s fibre.  I have a 2 computers i am currently testing with.  An HP blade running 11.10 server, and a custom built dev box also running 11.10 server with a gui on top.  I am able to see and interact with the LUN's on the blade.  But i follow the same steps and the custom box just will not see LUNs assigned to it.  I have checked / swapped cables, created new LUNs, but it simply will not see it.  With the blade, i assigned the LUN, restarted the computer ran 'sudo fdisk -l' and i saw the LUN.  No such luck with the custom box.  The only thing i can think of, is that on the blade server, the fibre HBA card was installed when 11.10 was installed fresh.  But on the custom box, the fibre HBA card was added after the OS was installed.  I have checked the hardware and the card is seen by the machine, and the drivers appear to be the same between the two boxes.  The only other thing to add, is that HP produced this card and there are no officially provided drivers, only for RHEL.  But the blade see's LUN's w/ out any drivers installed.  Im pretty much tapped for idea's any suggestions are welcomed.

Thanks very much!

---

