---
title: "encrypted ubuntu 10.04 with trucrypt windows 7 help!!!1"
date: 2010-06-24
forum: Security
---

### Post by xenosaga456 on 2010-06-24
im doing all of this from [http://ubuntuforums.org/showthread.php?t=761530]("http://ubuntuforums.org/showthread.php?t=761530")

hey im having problems doing this ??

5. Restore GRUB

Boot to the ubuntu Desktop cd, and open a terminal. Type

ls /dev/sd* && ls hd*

This will list the hard drives on your computer, which should be in the format

hda hda1 hda2 hda3 hda4

or

sda sda1 sda2 sda3 sda4

use the command

sudo mkdir /mnt/boot/
sudo mount /dev/sda* /mnt/boot/

followed by

ls /mnt/boot/

to find your boot partition. If your first guess is wrong, use

umount /mnt/boot/

and repeat with a different partition. Your grub partition will include files grub and initrd

Now we need to copy the MBR. This is set up by truecrypt, and contains your decryption files to boot the opperating system.

The command for this is;

sudo dd if=/dev/sda of=/mnt/boot/truecrypt.mbr count=1 bs=512
sudo dd if=/dev/sda of=/mnt/boot/truecrypt.backup count=8 bs=32256

Remember sda may be hda on your system.

This copies the MBR

Then start the grub sub-shell, with the command

sudo grub

remember the sudo, otherwise it won't work. In grub, type

install (hd0,*)/grub/stage1 (hd0) (hd0,*)/grub/stage2 0x8000 p

repacing * with the partition of your disk. Grub uses a diferent system to linux, so you will need to subtract one from your partition number. Thus if your boot partition is sda4, grub will require (hd0,3)
(it doesn't matter if linux says sd or hd).

Finally, you need to set up grub to chainload your the image you took earlier, to load the decryption algorithm.

All you need to do edit /mnt/boot/grub/menu.lst so that your windows sections looks like






when i get to
```
install (hd0,7)/grub/stage1 (hd0) (hd0,7)/grub/stage2 0x8000 p
```
its gives me error 15 ??

i do all of this then i try to install grub with the above command and it gives me error 15??

```
sudo mount /dev/sda8 /mnt/boot/
```


```
ls /mnt/boot/
abi-2.6.32-21-generic         System.map-2.6.32-21-generic
config-2.6.32-21-generic      truecrypt.backup
grub                          truecrypt.mbr
initrd.img-2.6.32-21-generic  vmcoreinfo-2.6.32-21-generic
lost+found                    vmlinuz-2.6.32-21-generic
memtest86+.bin

```




is any of thease error's because im using a ubuntu 9.04 live cd on my ubuntu 10.04 os???

---

### Post by xenosaga456 on 2010-06-25
ya that dident work but i did manage to get past the trucrypt boot loader with this disk i found called super grub disk so now i can boot up into ubuntu i just have to use the disk everytime???

is there anywaye i can rerite my MBR to point to grub on my /boot partition

---

### Post by wilee-nilee on 2010-06-25
> **xenosaga456 said:**
> ya that dident work but i did manage to get past the trucrypt boot loader with this disk i found called super grub disk so now i can boot up into ubuntu i just have to use the disk everytime???

is there anywaye i can rerite my MBR to point to grub on my /boot partition

I think you have to use a live cd that has grub2 9.10 and beyond here is a link.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

I am assuming this is a dual boot not a wubi install.

I'm also assuming since supergrub gets you in that rewriting the MBR and mounting Ubuntu is okay I'm not familiar with truecrypt.

You could also download the bootscript in my sig and post it or look at it yourself.

---

### Post by xenosaga456 on 2010-06-25
well i still have the grub in my boot on hd0 sda8
but i dont have the grub mbr i have the truecrypt mbr i followed all the steps here [http://ubuntuforums.org/showthread.php?t=761530&page=3]("http://ubuntuforums.org/showthread.php?t=761530&page=3")


well i have a 9.10 cd but the cd is a 32bit but my installed ubuntu is 64bit

---

### Post by wilee-nilee on 2010-06-25
> **xenosaga456 said:**
> well i still have the grub in my boot on hd0 sda8
but i dont have the grub mbr i have the truecrypt mbr i followed all the steps here [http://ubuntuforums.org/showthread.php?t=761530&page=3]("http://ubuntuforums.org/showthread.php?t=761530&page=3")


well i have a 9.10 cd but the cd is a 32bit but my installed ubuntu is 64bit

I wasn't sure if truecrypt was in the mbr or part of the chainload on the MS boot. The link I posted is for loading the mbr so I'm not sure at all about needing a grub2 disc but if your following a standard protocol it probably wouldn't hurt to download the karmic or lucid 64 bit live cd and try it using the methods you have been.

It would be interesting to see the script though with the setup you have. We don't see these with truecrypt involved.

---

### Post by xenosaga456 on 2010-06-25
well this is what i have this first box of code u can follow all of my commands if u look at it



```
bryan@thispc:~$ ls /dev/sd* && ls hd*
/dev/sda   /dev/sda2  /dev/sda5  /dev/sda7
/dev/sda1  /dev/sda3  /dev/sda6  /dev/sda8
ls: cannot access hd*: No such file or directory
bryan@thispc:~$ 
bryan@thispc:~$ sudo mkdir /mnt/boot/
[sudo] password for bryan: 
mkdir: cannot create directory `/mnt/boot/': File exists
bryan@thispc:~$ sudo mount /dev/sda8 /mnt/boot/
bryan@thispc:~$ ls /mnt/boot/
abi-2.6.32-21-generic         memtest86+.bin
abi-2.6.32-22-generic         System.map-2.6.32-21-generic
boot                          System.map-2.6.32-22-generic
config-2.6.32-21-generic      truecrypt.backup
config-2.6.32-22-generic      truecrypt.mbr
grub                          vmcoreinfo-2.6.32-21-generic
initrd.img-2.6.32-21-generic  vmcoreinfo-2.6.32-22-generic
initrd.img-2.6.32-22-generic  vmlinuz-2.6.32-21-generic
lost+found                    vmlinuz-2.6.32-22-generic
bryan@thispc:~$ sudo dd if=/dev/sda of=/mnt/boot/truecrypt.mbr count=1 bs=512
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.00029 s, 1.8 MB/s
bryan@thispc:~$ sudo dd if=/dev/sda of=/mnt/boot/truecrypt.backup count=8 bs=32256
8+0 records in
8+0 records out
258048 bytes (258 kB) copied, 0.0641441 s, 4.0 MB/s
```


then after that i open a new terminal and the sudo grub



```
bryan@thispc:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> 

```

then i 
```
install (hd0,7)/grub/stage1 (hd0) (hd0,7)/grub/stage2 0x8000 p
```
because its sda8 i put the 7 in.....well it says
```
grub> install (hd0,7)/grub/stage1 (hd0) (hd0,7)/grub/stage2 0x8000 p            
install (hd0,7)/grub/stage1 (hd0) (hd0,7)/grub/stage2 0x8000 p

Error 15: File not found
```

so i try with
```
install (hd0,7)/boot/grub/stage1 (hd0) (hd0,7)/boot/grub/stage2 0x8000 p
```
but it gives me the same error??



oww if this helps heres fdisk l
```
bryan@thispc:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00037c82

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       27976   224609375    7  HPFS/NTFS
/dev/sda3           27976       60802   263672833    5  Extended
/dev/sda5           27976       28025      390144   83  Linux
/dev/sda6           28025       59829   255467520   83  Linux
/dev/sda7           59829       60315     3905536   82  Linux swap / Solaris
/dev/sda8           60315       60802     3906560   83  Linux

Disk /dev/mmcblk0: 7948 MB, 7948206080 bytes
81 heads, 10 sectors/track, 19165 cylinders
Units = cylinders of 810 * 512 = 414720 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *           1       19166     7761806+   c  W95 FAT32 (LBA)
```




you can see my problem on youtube
[http://www.youtube.com/watch?v=-AcrNITmXW4]("http://www.youtube.com/watch?v=-AcrNITmXW4")

---

### Post by xenosaga456 on 2010-06-25
well this is what i have this first box of code u can follow all of my commands if u look at it



```
bryan@thispc:~$ ls /dev/sd* && ls hd*
/dev/sda   /dev/sda2  /dev/sda5  /dev/sda7
/dev/sda1  /dev/sda3  /dev/sda6  /dev/sda8
ls: cannot access hd*: No such file or directory
bryan@thispc:~$ 
bryan@thispc:~$ sudo mkdir /mnt/boot/
[sudo] password for bryan: 
mkdir: cannot create directory `/mnt/boot/': File exists
bryan@thispc:~$ sudo mount /dev/sda8 /mnt/boot/
bryan@thispc:~$ ls /mnt/boot/
abi-2.6.32-21-generic         memtest86+.bin
abi-2.6.32-22-generic         System.map-2.6.32-21-generic
boot                          System.map-2.6.32-22-generic
config-2.6.32-21-generic      truecrypt.backup
config-2.6.32-22-generic      truecrypt.mbr
grub                          vmcoreinfo-2.6.32-21-generic
initrd.img-2.6.32-21-generic  vmcoreinfo-2.6.32-22-generic
initrd.img-2.6.32-22-generic  vmlinuz-2.6.32-21-generic
lost+found                    vmlinuz-2.6.32-22-generic
bryan@thispc:~$ sudo dd if=/dev/sda of=/mnt/boot/truecrypt.mbr count=1 bs=512
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.00029 s, 1.8 MB/s
bryan@thispc:~$ sudo dd if=/dev/sda of=/mnt/boot/truecrypt.backup count=8 bs=32256
8+0 records in
8+0 records out
258048 bytes (258 kB) copied, 0.0641441 s, 4.0 MB/s
```


then after that i open a new terminal and the sudo grub



```
bryan@thispc:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> 

```

then i 
```
install (hd0,7)/grub/stage1 (hd0) (hd0,7)/grub/stage2 0x8000 p
```
because its sda8 i put the 7 in.....well it says
```
grub> install (hd0,7)/grub/stage1 (hd0) (hd0,7)/grub/stage2 0x8000 p            
install (hd0,7)/grub/stage1 (hd0) (hd0,7)/grub/stage2 0x8000 p

Error 15: File not found
```

so i try with
```
install (hd0,7)/boot/grub/stage1 (hd0) (hd0,7)/boot/grub/stage2 0x8000 p
```
but it gives me the same error??



oww if this helps heres fdisk l
```
bryan@thispc:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00037c82

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       27976   224609375    7  HPFS/NTFS
/dev/sda3           27976       60802   263672833    5  Extended
/dev/sda5           27976       28025      390144   83  Linux
/dev/sda6           28025       59829   255467520   83  Linux
/dev/sda7           59829       60315     3905536   82  Linux swap / Solaris
/dev/sda8           60315       60802     3906560   83  Linux

Disk /dev/mmcblk0: 7948 MB, 7948206080 bytes
81 heads, 10 sectors/track, 19165 cylinders
Units = cylinders of 810 * 512 = 414720 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *           1       19166     7761806+   c  W95 FAT32 (LBA)
```



[[IMG]http://brainstorm.ubuntu.com/idea/22551/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22551/)

---

### Post by xenosaga456 on 2010-06-25
hey i fixed it lol
it took forever

---

### Post by xenosaga456 on 2010-06-25
i fixed it

---

### Post by xenosaga456 on 2010-06-25
how would i mount my uwindows 7 with trucrypt from a live cd?



[[IMG]http://brainstorm.ubuntu.com/idea/22551/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22551/)

---

### Post by wilee-nilee on 2010-06-25
> **xenosaga456 said:**
> hey i fixed it lol
it took forever

Why don't you post the fix or did you put it on the thread where you were working from. The you tube video to be honest is about 2 min of the total I'll never get back.:lolflag:

---

### Post by new_tolinux on 2010-06-25
No offence, but please next time explain what your goal is.
I see a lot of text and logs, but I'm missing what you were trying to accomplish.

---

### Post by wilee-nilee on 2010-06-25
This is also a double thread.[http://ubuntuforums.org/showthread.php?t=1517015](http://ubuntuforums.org/showthread.php?t=1517015)

---

### Post by new_tolinux on 2010-06-25
Boot the live cd and install truecrypt?

---

### Post by wilee-nilee on 2010-06-25
I thought you had this fixed.

---

### Post by xenosaga456 on 2010-06-25
sorry i was trying to do this [http://ubuntuforums.org/showthread.php?t=761530&page=3]("http://ubuntuforums.org/showthread.php?t=761530&page=3")
but i did it a really diffrent way?? cuz i have the trucrypt bootloader as my default but i can still boot into ubuntu LVM



[[IMG]http://brainstorm.ubuntu.com/idea/22551/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22551/)

---

### Post by new_tolinux on 2010-06-25
> **xenosaga456 said:**
> sorry i was trying to do this [http://ubuntuforums.org/showthread.php?t=761530&page=3](http://ubuntuforums.org/showthread.php?t=761530&page=3)
but i did it a really diffrent way?? cuz i have the trucrypt bootloader as my default but i can still boot into ubuntu LVM
I guess you did really mess up somewhere. But I've got no idea where.
The tutorial is for Windows XP and Ubuntu (probably version 8.04 or even 7.10).

Since then a lot has changed. Ubuntu replaced grub with grub2 and Windows 7 installs on 2 partitions (100 mb boot and rest on another partition for the OS itself). I really think your best option was to try in on a virtual or spare machine instead of your primary computer.

I will report that topic to a moderator, as I think it should not be in the "Tutorials and tips" section anymore before it is properly updated.

---

### Post by xenosaga456 on 2010-06-25
> **wilee-nilee said:**
> Why don't you post the fix or did you put it on the thread where you were working from. The you tube video to be honest is about 2 min of the total I'll never get back.:lolflag:

well i dont really know how to explain it cuz i was high
so ya.....dont expext me to remimber mutch



[[IMG]http://brainstorm.ubuntu.com/idea/22551/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22551/)

---

### Post by xenosaga456 on 2010-06-25
> **wilee-nilee said:**
> I thought you had this fixed.

well i do have it fixed
i can start windows BUT only at the boot screen and i can start ubuntu by hitting 'esc' key


but now if im in ubuntu on the desktop how do i access the windows partiton from ubuntu with trucrypt?



[[IMG]http://brainstorm.ubuntu.com/idea/22551/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22551/)

---

### Post by lisati on 2010-06-25
Threads merged

---

### Post by xenosaga456 on 2010-06-25
what??



[[IMG]http://brainstorm.ubuntu.com/idea/22551/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22551/)

---

### Post by xenosaga456 on 2010-06-25
well u can see what im doing here better 
sorry fo the vids i just dont know hoe to explain it???

[http://www.youtube.com/watch?v=iTXXIQtnidE]("http://www.youtube.com/watch?v=iTXXIQtnidE")



[[IMG]http://brainstorm.ubuntu.com/idea/22551/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22551/)

---

### Post by lisati on 2010-06-25
> **xenosaga456 said:**
> what??

It was getting a little bit confusing for some of us with three similar threads alive at the same time.

---

### Post by xenosaga456 on 2010-06-25
> **lisati said:**
> It was getting a little bit confusing for some of us with three similar threads alive at the same time.

opps sorry???



[[IMG]http://brainstorm.ubuntu.com/idea/22551/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22551/)

---

### Post by wilee-nilee on 2010-06-25
> **xenosaga456 said:**
> well i dont really know how to explain it cuz i was high
so ya.....dont expext me to remimber mutch

Now that you mention that part I wanted to suggest another toke as a former long time user I recognized the state of mind. Not that there is anything wrong with that.:p

Really though why do you even need truecrypt is this a bragging rights issue? If it is we all on the forum are proud of you already,;)

Here is a link about hacking truecrpyt. 
[http://www.h-online.com/security/news/item/Tool-to-fool-TrueCrypt-published-832301.html](http://www.h-online.com/security/news/item/Tool-to-fool-TrueCrypt-published-832301.html)

Honestly if you were able to use supergrub to get in to the dual boot that is a easy access. If somebody really wanted to get in it would be pretty easy I suspect. Packet capture/sniffing is a weakness in wpa and other encryption.

This is a funny scroogle ssl pic.
[ATTACH]161585[/ATTACH]

---

### Post by xenosaga456 on 2010-07-11
i figured it out
while im in ubuntu i dloded trucrypt from there site and i went to select device and i clicked options and ticked the *mount with pre-boot authentication* and that workd now i can access all of my windows stuff from ubuntu yayay














> **wilee-nilee said:**
> Now that you mention that part I wanted to suggest another toke as a former long time user I recognized the state of mind. Not that there is anything wrong with that.:p

Really though why do you even need truecrypt is this a bragging rights issue? If it is we all on the forum are proud of you already,;)

Here is a link about hacking truecrpyt. 
[http://www.h-online.com/security/news/item/Tool-to-fool-TrueCrypt-published-832301.html](http://www.h-online.com/security/news/item/Tool-to-fool-TrueCrypt-published-832301.html)

Honestly if you were able to use supergrub to get in to the dual boot that is a easy access. If somebody really wanted to get in it would be pretty easy I suspect. Packet capture/sniffing is a weakness in wpa and other encryption.

This is a funny scroogle ssl pic.
[ATTACH]161585[/ATTACH]



[[IMG]http://brainstorm.ubuntu.com/idea/22551/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22551/)

---

