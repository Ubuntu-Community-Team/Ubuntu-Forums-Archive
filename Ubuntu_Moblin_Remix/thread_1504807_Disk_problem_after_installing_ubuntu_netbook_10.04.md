---
title: "Disk problem after installing ubuntu netbook 10.04"
date: 2010-06-08
forum: Ubuntu Moblin Remix
---

### Post by JingJing on 2010-06-08
I had Win 7 starter on my PC and two partitions. After I installed Ubuntu netbook 10.04 on my EEE pc form USB installer(on Disk D and my win7 is installed on C) , I started my win7 and the Disk D is no long available. But I want to use Disk D under window as well.... I'd appreciate if any one could explain this?  THANKS!!!~

---

### Post by kerry_s on 2010-06-08
windows can't use linux file system.

---

### Post by JingJing on 2010-06-08
Yes, as I remembered, when I installed ubuntu system, I selected the hard drive format to be EX3 jounarying files. But now I want to deleted this linux system from my computer. I tried to use adminstratior tools to format my disk D under ubuntu. But if I perform this operation, the entire disk will be formatted. I will also lose my win 7 ???  But I don't want to resintall win7... Any ideas???? Thanks a lot !!

---

### Post by wilee-nilee on 2010-06-08
So when you boot your computer do you get grub or the windows bootloader to choose windows or Ubuntu. We need to confirm whether this is a wubi or dual boot. A dual boot would have been installed with booting a live cd and installing in a separate partition. The use of letters can be confusing, in trying to figure, actually whats going on. A letter in MS=partition.

---

### Post by JingJing on 2010-06-08
when booting the computer, I get grub to choose windows or ubuntu. But how can I uninstalled ubuntu if so ?

---

### Post by wilee-nilee on 2010-06-08
So you want to remove Ubuntu, this is fine but we want to get W7 booting from it's own bootloader first. Post this boot script so that the people who can help see the whole picture. Post it in code tags, like this.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end. Please make sure to due the post in code tags otherwise it is difficult to read.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Now when you get some help you might ask some more questions in that it may be that you could have a dual boot that does what you want, and just have more options.

---

