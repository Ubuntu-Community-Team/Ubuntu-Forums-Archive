---
title: "unable to boot elementary os"
date: 2015-04-04
forum: Ubuntu/Debian BASED
---

### Post by Lhakarpo on 2015-04-04
Hi there,
I am new to linux and I am having problem booting my laptop which has dual boot(windows 8 and elementary os). I am able to boot into windows 8 but when i try to boot elementary OS i am stuck at grub prompt.

Following are the things I have tried.
1) I tried boot repair tool several times and to no avail. Link for that is  [http://paste2.org/2dW26xwj](http://paste2.org/2dW26xwj)
2) At the grub prompt, when I type set it looks for /boot/efi/ubuntu. I used live CD to check on the machine in my /boot/efi, I found it empty
3) Elementary is onstalled on sda6 

my machine is Asus ultrabook 32VD.

I really need help. I spent last two days to fix myself using forums but no luck.

thank you in advance.

---

### Post by ajgreeny on 2015-04-04
You say you are new to Linux but in your installation you appear to have 22 different kernel versions; where did all of those come from if this was a new installation and you are new to this OS?

There are also several inconsistencies with what you say and the details shown in the Boot-repair report which shows sda9 and sda10 as shared data partitions for Windows and Linux, which is not possible as they are both formatted to ext# filesystems.

You also appear to have three separate Windows Recovery Environment partitions which I suspect is far from normal, though I may be incorrect in that supposition as I no longer have any dealings with a Windows OS, and have never used Windows-8 on any machine.

Is the machine using a hybrid disk with both a spinning HDD and an SSD in the one physical disk as if that is the case I can not help much, never having had any experience of how they work, or is sdb a separate 24GB drive?  I see however that there is a second EFI partition on that drive which I believe can confuse the boot of a system.

Tell us more of the history of the machine please, as it may help in diagnosing the best way for you to proceed.

---

### Post by coffeecat on 2015-04-04
Elementary OS.

*Thread moved to **Ubuntu/Debian BASED**.*

---

