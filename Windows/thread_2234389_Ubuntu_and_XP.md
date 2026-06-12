---
title: "Ubuntu and XP"
date: 2014-07-14
forum: Windows
---

### Post by pepezacik2 on 2014-07-14
Hey , i am currently using Ubuntu 13.10 but i would like to install Windows XP.I already have the original ISO file but do not have any CDs/DVDs nor floppy disk and my computer won't boot from USB.Is there any program which would allow me to install XP directly from the ISO file ? Thanks for any help ! 

Also i have access to another computer with XP installed if it is needed.

---

### Post by coffeecat on 2014-07-14
This is a Windows problem.

*Thread moved to **Other OS/Distro Support**.*

What do you mean by "original ISO"? Where did this come from?

---

### Post by pepezacik2 on 2014-07-14
From the original CD

---

### Post by LastDino on 2014-07-14
I thought you couldn't do that with Original installation CD's back then? Maybe I'm wrong and how did you get one without having original CD/DVD? Or you meant the drive itself? 

But that hardly matter here as XP has been discontinued, so if you want to move back to windows go with W7. It really isn't that big on resources hog as long as you don't abuse it. Given you actually have that luxury with hardware.

You may have to stick with Linux depending on your hardware though, so do tell more. And ''if'' that does not make any sense, your best bet would be to borrow someone else CD/DVD drive and use it for installation.

---

### Post by at_first_light on 2014-07-17
You will need to install Windows XP from CD. To my knowledge the only tool that supports Windows XP installing from an iso is Vboot, which seems to be a dead project. This would also result in Windows XP being installed to a virtual hard drive instead of a real one. Vboot would require either overwriting your existing Grub2, or setting up a chainload between Grub2 and VBoot. Vboot wasn't free software either. It was priced at $79, but like I said the project appears to be dead. I think it died in Beta?

You can find out more about Vboot here:
[http://www.vmlite.com/index.php?option=com_content&view=article&id=51&Itemid=148](http://www.vmlite.com/index.php?option=com_content&view=article&id=51&Itemid=148)

According to it's documentation booting a Windows XP iso would use a menu entry like this:
> menuentry "XP Install Step 1" {
   vboot harddisk=(hd0,1)/winxp.vhd floppy=(hd0,1)/vboot/vboot.img cdrom=(hd0,1)/winxp-sp2.iso boot=cdrom
}
- Source: [http://www.vmlite.com/vboot/instructions.html#xp-to-vd](http://www.vmlite.com/vboot/instructions.html#xp-to-vd)

---

