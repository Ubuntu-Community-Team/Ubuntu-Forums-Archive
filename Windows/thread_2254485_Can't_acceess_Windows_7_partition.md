---
title: "Can't acceess Windows 7 partition"
date: 2014-11-27
forum: Windows
---

### Post by sports fan Matt on 2014-11-27
Is there a way that I can get into my Windows 7 after I deleted my linux partiion? the W7 partition is present, it just can not boot from it...

---

### Post by Mark Phelps on 2014-11-27
Since it appears you were dual-booting, it's likely the GRUB code was in the Linux partition you removed.  Had you restored the Win7 boot loader BEFORE you removed the Linux partition, you would not now be having this problem.

I'm presuming you do NOT have Win7 Repair media, otherwise, you would have mentioned it.

Since you can't boot into Win7 now, you can't use it to make a Repair CD, so you will have to be prepared to purchase an ISO file at the following link: [http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Once you have that file downloaded onto a PC, burn the image to a CD, reboot from that CD, and run  Startup Repair three times -- that's right, three times.

After the third repair pass, when you reboot, then without using the CD, you should be able to boot directly into Win7.

---

### Post by sports fan Matt on 2014-11-27
Hi Mark,

I clearly remember not touching the W7 partition, only expanding it after deleting the linux and swap.  And I do have Iso's burned of W7 but they refuse to boot.

---

### Post by Mark Phelps on 2014-11-27
> And I do have Iso's burned of W7 but they refuse to boot. 

Can't help you with that.

You should look into creating a bootable USB stick from one of the Win7 ISOs.  If your PC can boot from USB, you could try using that to do the repairs.

---

### Post by sports fan Matt on 2014-11-27
I do have a USB stick and an image downloaded on that USB of W7

---

### Post by Elfy on 2014-11-27
*Thread moved to **Windows**.*

---

### Post by sports fan Matt on 2014-11-27
So I can wipe linux on an older pc that I have if it helps to create a Windows iso...

---

### Post by sports fan Matt on 2014-11-27
I won't have the cash for that download for a week or so....

---

