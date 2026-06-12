---
title: "Clone drive with GPT - gpt-fix"
date: 2016-04-11
forum: Ubuntu Development Version
---

### Post by sudodus on 2016-04-11
If you clone a drive to another drive (*not* restore to the original drive from an image) with a GUID partition table, GPT, it will usually be corrupt, because in most cases you clone to another drive size, and GPT is sensitive to that (which is different from the old MSDOS partition table).

I made a shellscript file, [***gpt-fix***](http://phillw.net/isos/linux-tools/uefi-n-bios/gpt-fix), that does the work for me. It works for [all the cases that I have tested](http://ubuntuforums.org/showthread.php?t=2213631&page=4&p=13468260#post13468260). ***gpt-fix*** uses ***gdisk*** under the hood, and you may need to install it. Run gpt-fix in the directory, where you downloaded it (or install it into a directory in $PATH).

```
sudo apt-get install gdisk  # install if necessary

sudo bash gpt-fix /dev/sdx
```

where **x** is the drive letter.

-o-

There might be another problem too. The ***sector size*** (for example as seen by ***parted***) must match between the source drive and the target drive.

[hr][/hr]
It would be valuable if you can ***test how gpt-fix works for you***. Are there scenarios where it does not work? Should some other command of gdisk be added to gpt-fix? Or is there some fundamental problem, that cannot be fixed with gdisk?

I have tested gpt-fix when cloning both to a larger drive and to a smaller drive (provided that the partitions are within the target size). Actually I am only cloning until the end of the last partition, so I am not cloning the partition table copy at the end of the drive. The cloning method uses ***dd*** under the hood.

---

### Post by grahammechanical on 2016-04-11
Have tried cloning Ubuntu on an MBR partitioned drive with Grub in the MBR & restoring it to a GPT partitioned drive? 

There is a user in another thread that needs to do something like that to do what he wants.The new drive has Windows 10 on it. He has Windows 7 & Ubuntu on another drive and he does not want to go through all the bother of re-installing Ubuntu & setting it up all again. I think it is like wanting an easy route down a mountain. Well, jumping off the cliff is the real easy way down.

[http://ubuntuforums.org/showthread.php?t=2320204](http://ubuntuforums.org/showthread.php?t=2320204)

Regards

---

### Post by sudodus on 2016-04-11
No, I have not tried cloning Ubuntu on an MBR partitioned drive with Grub in the MBR & restoring it to a GPT partitioned drive. (I have cloned, but not converted it to a GPT drive.) It might be possible, but I don't know how to do it.

But Ubuntu can boot from an MBR (MSDOS) partitioned drive in UEFI mode. So if the guy has two drives, maybe that could be a solution.

---

### Post by sudodus on 2016-06-09
**gpt_fix** is built into [mkusb](https://help.ubuntu.com/community/mkusb). The GUID partition table, GPT, is fixed automatically, if you use mkusb 10.6.6 or a newer version to install from compressed image files with GPT. The functions **gpt_zap** and **gpt_fix** are built into mkusb.

If you use other tools, you need ***gpt-fix*** or to fix the GPT manually with ***gdisk***.

See also this link: [/Installation/UEFI-and-BIOS/stable-alternative#gpt-fix](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative#gpt-fix)

---

