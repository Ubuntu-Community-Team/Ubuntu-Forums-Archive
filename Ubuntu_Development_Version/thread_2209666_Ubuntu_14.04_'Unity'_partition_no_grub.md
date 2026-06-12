---
title: "Ubuntu 14.04 'Unity' partition no grub"
date: 2014-03-06
forum: Ubuntu Development Version
---

### Post by Hazzabin on 2014-03-06
My partition with Unity has lost it's grub, no matter what I do I cannot seem to get it back 

The partition is not showing at the boot menu, therefore cannot enter into it, tho can via Files (once in another os)

Is there anyway I can fix this, without having to do a re-install

---

### Post by ventrical on 2014-03-06
> **Hazzabin said:**
> My partition with Unity has lost it's grub, no matter what I do I cannot seem to get it back 

The partition is not showing at the boot menu, therefore cannot enter into it, tho can via Files (once in another os)

Is there anyway I can fix this, without having to do a re-install

 I use the Grub Rescue CD.  Works 9 times out of 10. You would have to download it and burn it to a CD. I am only reporting a method I use.  There are probably other methods but I am just covering what I do. Once burned and booted it is pretty well self explanatory after that.


Regards..

---

### Post by Hazzabin on 2014-03-06
Thanks mate
will give that a try

---

### Post by cariboo on 2014-03-06
You can boot from a live CD/USB, and chroot your / partition:

```
sudo mount /dev/sda1 /mnt
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /sys /mnt/dev
sudo mount -o bind /proc /mnt/dev
sudo chroot /mnt
```

substitute the location of you / partition for /dev/sda1

Once you have chrooted the partition try the following commands:

```
sudo grub-install /dev/sda

sudo update-grub
```

**Note:** If you are running a 64-bit version, you must use a 64-bit live CD/USB,

---

### Post by Hazzabin on 2014-03-06
Guys I thank you for your help, being that partition 14.04 Unity had been running with all the ups and downs over the past 7 weeks, I
came to the conclusion to be 'brutal' and did the very latest daily iso

---

