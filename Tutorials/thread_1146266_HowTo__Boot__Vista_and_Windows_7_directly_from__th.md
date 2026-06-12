---
title: "HowTo:  Boot  Vista and Windows 7 directly from  the Grub menu"
date: 2009-05-02
forum: Tutorials
---

### Post by meierfra. on 2009-05-02
This tutorial is for people who have Vista and Windows 7 installed and would like to be able to boot  both directly from the Grub menu.
(The same tutorial works if you have two installations of Vista  or two installation of Windows 7, but it does not work for XP).
The tutorial assumes that you are able to boot into Vista and Windows 7 via the Windows Boot Menu.

In the following I will refer to the two Windows installation by WinA and WinB.  WinA refers to  one which has the boot loader  "bootmgr".  "bootmgr"  is a [hidden system file]("http://www.tech-recipes.com/rx/1521/how_to_view_hidden_and_system_files_and_folders_in_vista/") in the root directory, or C:\, of one of your two Windows installations. In most cases  WinA will be  the one which was installed first.

[SIZE="4"][COLOR=blue] Boot into WinA[/COLOR][/SIZE]


** Step 1 Edit the WinA boot loader, so that it also will work on the WinB partition: **

Go to "Start". Type "cmd" and press "Ctrl+Shift+Enter". This will open a command line as an administrator. (If this did not open the command line: Go to Start->Program Files->Accessories, Right Click "Command Prompt", Choose "Run as administrator")

Type


```
  
bcdedit /set {bootmgr} device boot

```


[SIZE="4"][COLOR=blue] Boot into Ubuntu.[/COLOR][/SIZE]
 and open a terminal (Applications->Accessories->Terminal) 


** Step 2 Add WinB to "menu.lst": **

Open menu.lst via

```
gksudo gedit /boot/grub/menu.lst
```

The existing entry for Windows will be used for booting into WinA. Add a similar  entry for WinB.
If you need help with this, post the output of "sudo fdisk -lu" and the current Windows entry.


** Step 3  Copy the boot files from WinA to WinB **

Type 

```
 sudo fdisk -lu
```

and determine the device names of the WinA and WinB  partitions.
In the following I assume that  WinA  is on /dev/sda1 and WinB is on /dev/sda2. 

```
sudo mkdir /mnt/Win{A,B}
sudo mount /dev/sda1 /mnt/WinA
sudo mount /dev/sda2 /mnt/WinB
sudo cp /mnt/Win{A,B}/bootmgr
sudo cp -R /mnt/Win{A,B}/Boot

```
Of course you need to  replace  /dev/sda1 by the device name of the WinA partition and /dev/sda2 by the device name of the WinB  partition. 
Sometimes the directory  Boot  is called BOOT instead. Use  "ls -l /mnt/WinA" the determine the correct spelling. 


** Step 4 Edit the WinA boot loader, so that it boots directly into WinA**

Reboot.
Choose the WinA entry at the Grub menu. The  WinA boot menu will appear. Boot into WinA.  Open the WinA command line as in Step 1 and type

```

bcdedit /set {bootmgr} default {current}
bcdedit /set {bootmgr} timeout 0

```



** Step 5 Edit the WinB boot loader, so that it boots directly into WinB**

Reboot.

Choose the WinB entry at the Grub menu. The  WinB  boot menu will appear. Boot into WinB.  Open the WinB command line as in Step 1  and type

```

bcdedit /set {bootmgr} default {current}
bcdedit /set {bootmgr} timeout 0

```


From now on if you pick WinA  at the Grub menu you should boot directly into WinA , and the same for WinB.


Here is a thread where this method was used sucessfully:

[http://ubuntuforums.org/showthread.php?t=1121214](http://ubuntuforums.org/showthread.php?t=1121214)

---

### Post by felipeabk on 2009-07-28
Thank You so much! It worked perfectly for me! And using what I learned with the tutorial, now I found how to boot Windows XP and Windows 7 directly from the Grub menu!! :D

---

### Post by HarmCla on 2009-08-04
Hi there,
 
 
That's a great and clear guide you made there.
But unfortunately, it doesn't work with me :(
 
I did all of these steps, but when i now boot WinA, WinB boots instead :(
I haven't tried WinB yet though...
 
Can you help me please?
 
I've tried the *fixmbr* command, i thought that would restore the Windows Boot Loader, but but I get an error saying that this command isn't recognized :(
Same for *FDISK /mbr*.
 
I'm brand new to this forum, should I have made a topic instead?

---

### Post by N1c0_ds on 2009-09-29
This one does not work at all for me. Still no results after doing it over at least 5 times. I tried everything I could find and I still can't boot 7 separately.

(MS rant...)

---

### Post by octanemv on 2011-08-21
Hi,

Thanks very much for this tip! It worked well as long as second windows exists in primary partition. I am using grub2 and looks to me grub2 does not read bootsector at the logical volume in extended partition. Is that right?

menuentry "win on extended partition" {
    # 1st logical volume in extended partition
    set root=(hd0,msdos5)
    chainloader +1
}

Any tip would be really appreciated.

---

### Post by octanemv on 2011-08-27
After some analysis, it turns out that the pbr(partition boot record) inside extended partition installed by Windows does not show real "hidden sectors" in Physical disk. The mismatch fails Windows to boot from grub2. While legacy grub takes care of it, so legacy grub still works.

For those who are interested in booting Windows installed inside extended partition directly from grub2, try following. It worked for me perfectly.

a) copy pbr into a file e.g. dd if=/dev/sda5 of=sda5.pbr bs=512 count=1
b) check real staring sector of the partition. I used Gparted. select the partition and show information.
c) open a file e.g sda5.pbr with binary editor. 
d) replace hidden sector entry, 4bytes starting 0x1c with real starting sector from b)
    e.g. assume if real sector is 251,690,418 (0x0f007db2)
     0x1c : b2
     0x1d : 7d
     0x1e : 00
     0x1f : 0f
e) save a file e.g. sda5.pbr.mod

menu entry should be like e.g.

menuentry win {
    set root=(hd0,msdos5)
    chainloader /sda5.pbr.mod
}

Hope this helps someone who specifically wants to boot windows inside extended partition
directly from grub2.

---

