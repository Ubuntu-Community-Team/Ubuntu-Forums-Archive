---
title: "Bad selection of drive while I created usb stick"
date: 2014-09-09
forum: System76 Support
---

### Post by josimar_chire on 2014-09-09
Good morning.
I have a laptop and I had installed ubuntu on external disk.
This external disk had 4 partitions sdb1,sdb2,sdb3,sdb4.

I was trying to format my usb with a .iso that  I needed using this:
sudo umount /dev/sdb
sudo dd if=/path/to/ubuntu.iso of=/dev/sdb bs=1M

But I made mistake I had to write sdc and I wrote sdb. I was thinking I format my external disk.

Can you help me? What did I do? How can I fix it or recover data?

Thank you.

---

### Post by varunendra on 2014-09-12
Hi, and Welcome to the forums!

The popular name for 'dd' is "Destroyer of Disk" for a reason. But assuming it would have written only the initial part of the disk, equal to the amount of the size of the iso, I think you should try 'testdisk' to see if it can find the older partition structure.

TestDisk Step by Step : [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

If it fails, you can try to recover whatever recoverable data there is using 'photorec' that comes with the same package.

PhotoRec Step by Step : [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

Please note that the package 'testdisk' is in the default repositories. So, with a working internet connection, you can install it with -
```
sudo apt-get update
sudo apt-get install testdisk
```

Good Luck!

---

