---
title: "Overwrite Elelmentary Loki OS"
date: 2018-08-20
forum: Ubuntu/Debian BASED
---

### Post by albertramsbottom on 2018-08-20
Hi

I have dual boot Windows 10 machine with elementary installed on a 25GB partition with grub as the boot loader. Elementary first and windows third down the list

I hate Elementary  and would like to install Ubuntu instead but I am worried about the process. 

If I insert a USB stick with Ubuntu on it and boot to it, will it ask where I want to install it? and will it let me overwrite EOS? And if it does, will it make the necessary changes to grub, to replace elementary with Ubuntu?

Thanks for any advice

---

### Post by slickymaster on 2018-08-20
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by oldrocker99 on 2018-08-20
If you select "Something Else" at the install screen, you should be able to install Ubuntu over Elementary. Make sure that you back up your /home folder **FIRST**. You might want to make separate / and /home partition, and then, once you restore the backup, you'll be able to install without losing your data.

Over the years, I have found that 32GB is *plenty* of space for /. The rest can be formatted as /home.

Good luck! Post here is you have any more questions.

---

### Post by albertramsbottom on 2018-08-20
Thanks for that :) I take it that hopefully it will chnage grub and not overwrite my MBR??

A second question, is it possible to boot a live Ubuntu and install from an SD Card??

Cheers

---

