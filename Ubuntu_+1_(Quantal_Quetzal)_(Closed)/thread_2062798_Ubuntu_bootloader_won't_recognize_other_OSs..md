---
title: "Ubuntu bootloader won't recognize other OSs."
date: 2012-09-25
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by donniezazen on 2012-09-25
Hello,

Ubuntu GRUB is not recognizing other OSs (Arch and Fedora) I newly installed on my system. I am sharing /home and swap. If I install grub in Arch it does recognize Ubuntu. os-prober isn't coming up with anything on Ubuntu.

Thanks.

---

### Post by balloons on 2012-09-26
Please get a bug report filed for this :-) Grub 2.0 is the default now in quantal, and it's a big change from the previous versions.

---

### Post by dino99 on 2012-09-26
To avoid troubles, set grub2.0 everywhere or nowhere.

---

### Post by donniezazen on 2012-09-26
Quantal is using grub-common 2.00-5ubuntu3 and Arch uses grub-bios 2.00-1. These seems to be both Grub 2.0. I will file bug report. Thanks.

---

### Post by grahammechanical on 2012-09-26
I have found that Grub 2 and update-grub stumble if there are Grub 1.99 configuration files in a partition.

I have also noticed, as far as Ubuntu is concerned, that the last OS installed puts its Grub into the MBR and over-writes the Grub configuration files on the other partitions. I do not know if Arch and Fedora do the same thing.

I have 1x12.04 and 3x 12.10 installed and I have in the Grub menu multiple entries for the same kernels. And there is no way to distinguish the entries from one another.

Grub 2 has a different naming convention for the kernels/partitions than Grub 1.99. I get the new style labels and the old style (with "on /devsda5" for example) labels and they point to the same kernel images.

Do you not see any references to Arch or Fedora in /boot/grub/grub.cfg? Or to their partitions. Look for something like set root='hd0,msdos5' as that has replaced hdo,sda5. Relevant to the partitions that Arch and Fedora are installed on.

Also look for the menuentry. I get this with 12.10. Note the label in quotation marks.

menuentry "Ubuntu quantal (development branch) (12.10)"

Arch and Fedora might be wrongly labelled. All of this might help identify what is going wrong and whether it is with update-grub or 30_osprober script.

Regards.

---

### Post by coffeecat on 2012-09-26
I wonder if it's related to this:

[http://ubuntuforums.org/showthread.php?t=2061414](http://ubuntuforums.org/showthread.php?t=2061414)

os-prober recognises Windows 7 on one machine but not Vista on another, whereas it recognises the recovery partition on both.

---

### Post by oldfred on 2012-09-26
In grub 1.99 some have reported that Fedora installed in LVM is not seen by os-prober. But mounting the Fedora partition first (and having lvm2 installed) then os-prober finds the Fedora partition.

---

### Post by Lars Noodén on 2012-09-26
> **oldfred said:**
> In grub 1.99 some have reported that Fedora installed in LVM is not seen by os-prober. But mounting the Fedora partition first (and having lvm2 installed) then os-prober finds the Fedora partition.

I'm having that trouble, Fedora is not found by (L)ubuntu's Grub.  It was working fine until a few weeks ago.  One of the updates for 12.10 broke it.  It still finds OS X just fine, though.  So dual boot works even if triple boot is not currently possible.

---

