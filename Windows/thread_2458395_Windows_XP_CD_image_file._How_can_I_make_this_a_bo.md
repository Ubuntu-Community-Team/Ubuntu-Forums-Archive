---
title: "Windows XP CD image file. How can I make this a bootable USB drive?"
date: 2021-02-23
forum: Windows
---

### Post by 777funk on 2021-02-23
I have DVDs that I could burn to, but I'd like to just put this on a thumb drive. How can I do this from Linux?

---

### Post by 777funk on 2021-03-02
> **777funk said:**
> I have DVDs that I could burn to, but I'd like to just put this on a thumb drive. How can I do this from Linux?


Does anyone know how I can do this? I'd like to put my Win XP install CD onto a regular USB drive.

---

### Post by Tadaen_Sylvermane on 2021-03-02
Not sure it's possible. An ISO needs to be built a certain way for usb to work. At the time that just wasn't a common thing, especially for Windows. 

[https://superuser.com/a/623998](https://superuser.com/a/623998)

This may work but it looks way more effort than it's worth. Is there a reason you want XP specifically? Especially with it totally unsupported these days?

---

### Post by 777funk on 2021-03-02
> **Tadaen_Sylvermane said:**
> Not sure it's possible. An ISO needs to be built a certain way for usb to work. At the time that just wasn't a common thing, especially for Windows. 

[https://superuser.com/a/623998](https://superuser.com/a/623998)

This may work but it looks way more effort than it's worth. Is there a reason you want XP specifically? Especially with it totally unsupported these days?

The reason I'd use it still is to run a few pieces of software (music production) that still loaded in XP up to a couple years ago. I have a few thousand worth of music recording software and it'd be too expensive to upgrade or in some cases it's even obsolete. 

I don't get online with the XP laptop.

---

### Post by deadflowr on 2021-03-02
What kind of image file is it?
ISO can boot directly in a virtual machine, which is probably a better thing to do than installing directly onto a machine.

---

### Post by 777funk on 2021-03-02
> **deadflowr said:**
> What kind of image file is it?
ISO can boot directly in a virtual machine, which is probably a better thing to do than installing directly onto a machine.

Thanks for the tip and it is infact an ISO (created from a Win XP CD via dd).

It seems like a virtual machine may have trouble with USB and Firewire audio interface I/O speeds (latency can be an enemy in live recording). 

Ironically I also tried installing from the .iso file (and the disc) to VirtualBox and it's not taking it (the OS just opens and closes).

---

### Post by yancek on 2021-03-03
Using dd on an iso file to make it bootable on a usb requires that it be hybrid, which windows iso files are not.  I don't think bootable usb's were common in the days of xp.  You might be able to loop mount the xp iso file, then copy the extracted contents to a usb and either boot it from Grub on your installed Linux or install Grub on the usb and write a proper menuentry in grub.cfg.

I've done this type of thing with a windows 7 recovery disk as well as a windows 10 installer on the same usb, but have not used xp.   I expect something like this would work.

---

