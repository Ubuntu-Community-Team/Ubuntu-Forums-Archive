---
title: "VirtualBox"
date: 2008-05-15
forum: Virtualisation
---

### Post by ts_patil on 2008-05-15
I am a new user. I have Windown on one partition and Ubuntu on another. I have installed the VirtuslBox 1.6 on Ubuntu. I want to open the Windows from the existing partition.

Please any one help me.

I have created the virtal disk file and when I am trying to adding the virtual disk, I am getting the following error


VD: error opening image file '/home/user/.VirtualBox/Win.vmdk' (VERR_ACCESS_DENIED).


Result Code: 
0x80004005
Component: 
HardDisk
Interface: 
IHardDisk {fd443ec1-000f-4f5b-9282-d72760a66916}
Callee: 
IVirtualBox {2d3b9ea7-25f5-4f07-a8e1-7dd7e0dcf667}

---

### Post by Sand Lee on 2008-05-16
Here you go, [http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883)

and please do not make multiple threads about related issues...

---

### Post by Sand Lee on 2008-05-19
[QUOTE=ts_patil]Hi Sand Lee,

I tried the as per the details mentioned in the below link.

[http://ubuntuforums.org/showthread.php?t=795715&goto=newpost](http://ubuntuforums.org/showthread.php?t=795715&goto=newpost) 

I have a disk of 120 GB and 35 is given to Ubuntu and 70+ is a NTFS partition.

I recently created loaded the ubuntu and I want to continue to use this.
 
The problem is some of the application which I use should required Windows and I want to use the same disk.

When I create vmdk file I have given /dev/sda and the virtual disk manager of virtual box shows me 112 GB and when I use /dev/sda2 the "partition 2" option not work and without that it shows 72 GB.

When I start the machine, the windows won;t get loaded and a the screen becomes blank and wiats.

I also tried to resize the windows parition through partiotion magic but its giving me the error 1529. and till now I am not able to get the solution.

Please can you help me to resolve both these issue.

Thanks
:)[/QUOTE]

Could you post/show the output of, ```
sudo cfdisk
```
Also, have you tried the alternate step 1 outlined in the tutorial?

---

### Post by ts_patil on 2008-05-19
cfdisk (util-linux-ng 2.13.1)

                              Disk Drive: /dev/sda
                       Size: 120034123776 bytes, 120.0 GB
             Heads: 255   Sectors per Track: 63   Cylinders: 14593

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sda1        Boot        Primary   Dell Utility                        57.58
    sda2        Boot        Primary   NTFS             []              75861.76
    sda3                    Primary   Linux ext3                       38115.95
    sda4                    Primary   Linux swap / Solaris              5996.23

---

### Post by ts_patil on 2008-05-27
Hi Please can some on help me to resolve this issue.

Thanks

---

