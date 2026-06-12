---
title: "boot Windows from esata external"
date: 2011-12-31
forum: System76 Support
---

### Post by Mendel314 on 2011-12-31
I would like to set up my system so that I can boot windows 7 from my external esata drive.  I have a windows cd and the drive connected, I just partitioned it into ntfs and now I am not sure what to do.  I can't get my laptop (pan p7) to boot from the cd.  how do I do this?

---

### Post by Paddy Landau on 2012-01-01
Your BIOS determines from which device your computer will boot. Look in your BIOS, and tell it to try to boot from the CD before it tries the hard drive.

Alternatively, some computers let you choose when you boot. Try repeatedly pressing F12 while you boot, and it may offer a mini-menu allowing you to boot from the CD.

Your computer manual should help.

---

### Post by Mendel314 on 2012-01-01
> **Paddy Landau said:**
> Your BIOS determines from which device your computer will boot. Look in your BIOS, and tell it to try to boot from the CD before it tries the hard drive.

Alternatively, some computers let you choose when you boot. Try repeatedly pressing F12 while you boot, and it may offer a mini-menu allowing you to boot from the CD.

Your computer manual should help.

I have done this, I keep getting device not bootable messages.  I tried this with the oem cd, with an old windows iso burned to a flash drive, and I tried UNetbootin to install windows onto the external hdd, always the same message.

---

### Post by Paddy Landau on 2012-01-02
If the OEM CD does not work, there is something wrong either with the CD or with your laptop. Can you boot from a different CD (e.g. from an Ubuntu Live CD) on your computer? Try booting from your Windows OEM CD on a friend's computer (but obviously do not install). Those two tests, I hope, will narrow down where the problem lies.

---

### Post by isantop on 2012-01-03
Also, I should point out that the BIOS boot bypass key on a PanP7 is F1, so you'll want to press that to choose the CD drive.

---

