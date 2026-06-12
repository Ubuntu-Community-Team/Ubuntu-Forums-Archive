---
title: "If you don't dual-boot then your OK with alternate installer, correct or not."
date: 2010-04-29
forum: The Cafe
---

### Post by MechaMechanism on 2010-04-29
Just like subject says.

If you don't dual-boot then your OK with alternate installer, correct or not.

I should have added this is for 10.04.

---

### Post by gordintoronto on 2010-04-29
I could be wrong, but I think the two items are not related to each other. The alternate installer is for systems with limited resources, primarily memory.

---

### Post by shafin on 2010-04-29
> **MechaMechanism said:**
> Just like subject says.

If you don't dual-boot then your OK with alternate installer, correct or not.

I should have added this is for 10.04.
Correct.

If you want to dual boot with Alternate installer, just wait a day or two. New ISO's will land. Or you can install it and update grub.

---

### Post by aysiu on 2010-04-29
You can set up a single-boot with the Desktop CD.
You can set up a dual-boot with the Desktop CD.
You can set up a single-boot with the Alternate CD.
You can set up a dual-boot with the Alternate CD.

What CD you use has **no** bearing on whether you can set up a single- or dual-boot.

---

### Post by MechaMechanism on 2010-04-29
Thanks.

---

### Post by chessnerd on 2010-04-29
The LiveCD installer definitely makes it easier to configure a dual-boot, but the Alternative installer can do it too. The only reason you should use the Alternative CD is if you have a low-RAM computer or just love the command-line.

If you have 786 MB or more RAM I would highly recommend the LiveCD installer, even if you are single booting. It's much easier to work with and doesn't take much longer to run.

If you have limited RAM, 512 MB or less, then you might want the Alternative CD. (512 MB is on the fence, it SHOULD work with the LiveCD, but I've tried to install on a computer with 384 MB and that required the Alternative.)

---

### Post by aysiu on 2010-04-29
Even with 256 MB or 384 MB, I would recommend the Desktop CD.

There is an option at bootup to just install directly (instead of running a live session while installing, which uses up a lot more RAM).

---

### Post by cariboo on 2010-04-30
> **chessnerd said:**
> The LiveCD installer definitely makes it easier to configure a dual-boot, but the Alternative installer can do it too. The only reason you should use the Alternative CD is if you have a low-RAM computer or just love the command-line.

If you have 786 MB or more RAM I would highly recommend the LiveCD installer, even if you are single booting. It's much easier to work with and doesn't take much longer to run.

If you have limited RAM, 512 MB or less, then you might want the Alternative CD. (512 MB is on the fence, it SHOULD work with the LiveCD, but I've tried to install on a computer with 384 MB and that required the Alternative.)

There are other reasons for using the alternate install iso that have nothing to do with low specs. I have a fairly up-to-date sytem,AMD X@ 3800+ cpu, 2GB ram Nvidia 9400GT, with  no ide drives in it, the Live CD will not detect my SATA hard drive. Using the alternate iso the drive gets detected properly. There are other people whose video card isn't detected properly by the Live CD, and it won't let them even install Ubuntu, the alternate install allows them to install Ubuntu and set up their graphics card once they are at the desktop. 

The alternate also allows you to setup full disk encryption, where the Live CD only allows you to setup an encrypted home directory. The alternate iso will allow you to setup LVM, where the Live CD doesn't have that option.

There is no command line needed when using the alternate iso, the installer is text based, it won't allow you to use the mouse, but using the keyboard to cycle between options is not a problem.

---

### Post by Viva on 2010-04-30
I always use the alternate installer. The couple of times I used the live cd, it ended up being a mess.

---

