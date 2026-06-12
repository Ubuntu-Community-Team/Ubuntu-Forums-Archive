---
title: "boot windows from physical partition with qemu"
date: 2009-01-15
forum: Virtualisation
---

### Post by tmeier on 2009-01-15
[http://ubuntuforums.org/images/editor/attach.gifI](http://ubuntuforums.org/images/editor/attach.gifI) have a Thinkpad x41T with the following disk setup :

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  12.9GB  12.9GB  primary   ntfs         boot 
 3      12.9GB  25.2GB  12.3GB  primary   ext3              
 2      25.2GB  60.0GB  34.8GB  extended               lba  
 6      25.2GB  25.8GB  592MB   logical   linux-swap        
 5      25.8GB  60.0GB  34.2GB  logical   ntfs         

Partition 1 is the Windows partition.

I try running qemu with the following command 

sudo qemu -hda /dev/sda

It starts up brings up grub and I select my windows partition and then I get a message that says :  A Disk Read Error has Occurred
Press Ctr-Alt-Del to restart

I am running Intrepid Ibex and using qemu 0.9.1.
The Windows partition is not mounted.

Any ideas?

Thanks

---

