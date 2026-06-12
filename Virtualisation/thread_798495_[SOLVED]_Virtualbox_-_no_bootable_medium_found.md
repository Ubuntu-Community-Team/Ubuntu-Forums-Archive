---
title: "[SOLVED] Virtualbox - no bootable medium found"
date: 2008-05-18
forum: Virtualisation
---

### Post by spamzilla on 2008-05-18
I have just installed Arch Linux in virtualbox. I rebooted Arch and I cannot boot into the newly installed OS - it just loops and sends me to the install page. So I removed the install CD from the cd/dvd drive, and tried to boot, and I get

```
no bootable medium found - system halted
```

Ok this is probably due to me taking out the install CD, but how do I actually boot into the OS I have just installed?

(I was going to post this in the General forum, but I don't seem to have access to it :confused::confused:)

Cheers

---

### Post by spamzilla on 2008-05-18
Bump!

---

### Post by shifty_powers on 2008-05-18
machine>settings>advanced and check the boot order....

---

### Post by Victormd on 2008-05-18
did you configure virtualbox to boot from the HD?

---

### Post by Mhurst1 on 2008-05-18
Also make sure that you dont have the iso mounted

---

### Post by spamzilla on 2008-05-18
> **Mhurst1 said:**
> Also make sure that you dont have the iso mounted

> **Victormd said:**
> did you configure virtualbox to boot from the HD?

That's how I set it up, and I get the "no bootable medium found" error.

---

### Post by bumanie on 2008-05-18
I just had the same problem installing hardy heron in virtualbox. I got around it by deleting the virtual hard drive and starting again. Can't say if that will help you or not.

---

### Post by spamzilla on 2008-05-18
Ugh. I just uninstalled virtualbox, deleted the hidden folder, reinstalled VB and Arch, and I still get this problem.

I just don't understand what is going wrong :confused:

---

### Post by Victormd on 2008-05-18
did you install virtualbox from the repos? Or did you download it from [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")? (IMO, the second option is better...)

---

### Post by spamzilla on 2008-05-18
> **Victormd said:**
> Or did you download it from [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")? (IMO, the second option is better...)

Yup that's where I downloaded the file from.

---

### Post by bodhi.zazen on 2008-05-18
With an arch linux guest you need to set your hard drive as IDE and use the ide-legacy otpion (add it to grub)

Add it in on your grub kernel line :

title Arch linuix
root (hd0,0)
kernel /boot/vmlinux-x.y.z quiet splash **ide-legacy**
initrd /boot/initrd-x.y.z
boot

---

### Post by spamzilla on 2008-05-18
> **bodhi.zazen said:**
> With an arch linux guest you need to set your hard drive as IDE and use the ide-legacy otpion (add it to grub)

Add it in on your grub kernel line :

title Arch linuix
root (hd0,0)
kernel /boot/vmlinux-x.y.z quiet splash **ide-legacy**
initrd /boot/initrd-x.y.z
boot

I cannot get into the shell, so how can I do this without reinstalling Arch? 

Thanks :)

---

### Post by spamzilla on 2008-05-18
Oddly enough, I didn't change anything and Arch is now booting up fine.

Thanks for all the help :)

---

### Post by Rohen on 2008-05-20
I'm having the same problem... :(

I've erased the image file, re-created it, changed boot orders, mounted and un mounted the ISO...

No idea what's wrong....!!!!  :confused:

---

### Post by jim1964 on 2008-10-31
I got mine to work. I have two CDROM drives. Virtual box was pointing to drive 1 yet I had to put the CD in drive 2 to get it to boot. Found it by dumb luck.

---

### Post by jamiel on 2008-12-05
As this was the first result for my google search for this problem, in case anyone else has this issue mine was being caused because I was installing GRUB on my boot partition (/dev/sda1) instead of MBR (/dev/sda).

Hope this helps someone.

J

---

### Post by smdofjmdsfjoiez on 2009-09-12
Thank you jamiel!!!

---

