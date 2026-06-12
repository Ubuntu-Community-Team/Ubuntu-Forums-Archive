---
title: "bootinfoscript"
date: 2013-05-25
forum: Ubuntu Development Version
---

### Post by VMC on 2013-05-25
bootinfoscript shows the wrong(or otherwise) info for the Boot Summary, when Saucy is in control:

                  Boot Info Script 0.61      [1 April 2012]




============================= Boot Info Summary: ===============================


 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in ***partition 94*** for .


If I install boot from Precise, it looks normal, as ***,msdos6*** or whatever the partition number is.

I did some search in Saucy for in changes in the grub boot, but can't find anything. Anyone else who has install Saucy lately have any issue with bootinfoscript?

---

### Post by cariboo on 2013-05-26
I get the same info, on both hard drives in my system one with Quantal and Raring Ubuntu Gnome, and the other with just Saucy:

```
============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 94 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 94 for .
```

Looking at partition types in fdisk partition type 94 = Amoeba BBT, which I can't seem to find any info on.

---

### Post by VMC on 2013-05-26
I don't think its referring to the partition ID. I have noticed on several occasions where the RESULTS.txt has been displayed, "partition 94" has come up. No one since now even questioned it. I put in a private message to Gert, and will wait his reply.

---

### Post by grahammechanical on 2013-05-27
I have just noticed a slight change in grub.cfg. 

Precise grub.cfg has set root='(hd0,msdos1)'

Raring and Saucy have set root='hd1,msdos8'

The brackets are missing. I have been trying to boot into a btrfs Ubuntu install using the Grub command line. I can do it if I put in the brackets and leave out the single quotation marks. but not if I only have the single quotation marks and not the brackets. The Grub manual insists on the brackets being there. And yet my Raring and Saucy installs (minus the brackets) boot just fine.

Modifications to grub.cfg?

---

