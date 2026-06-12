---
title: "Installed Vista, now i cant boot up Ubuntu"
date: 2009-01-20
forum: Server Platforms
---

### Post by jairom70 on 2009-01-20
had Ubuntu Server. 8.10. first.  then i installed Vista Home Prem.
i followed the steps using NeoGrub. 

I noticed my menu.lst has this line

title		Ubuntu 8.10, kernel 2.6.27-9-server
uuid		6a88bdf8-cb8f-470d-8698-02522703a087
kernel		/boot/vmlinuz-2.6.27-9-server root=UUID=6a88bdf8-cb8f-470d-8698-02522703a087 ro quiet splash vga=0x346
initrd		/boot/initrd.img-2.6.27-9-server


but i read seomwhere it should be 

title		Ubuntu 8.10, kernel 2.6.27-9-server
[COLOR="Red"]root		(hd0,1)[/COLOR]
kernel		/boot/vmlinuz-2.6.27-9-server root=UUID=6a88bdf8-cb8f-470d-8698-02522703a087 ro quiet splash vga=0x346
initrd		/boot/initrd.img-2.6.27-9-server

why does it say uuid. and how can i chnage it back. I figure i can just edit and type it in. I treid that but then on boot up it tells me.

 Cant mount drive.

If i leave the line as it is. (with uuid) then i get 

error 17 file missing.

how can i find out which combination of (hd0,1) to use?  im currently using a live CD to boot up and view my server files.

---

### Post by Jense on 2009-01-20
Well first, I would expect your Grub-bootsector has been overwritten, which is why you normally install the other way around, first Win, the linux. 
But maybe MS changed it's policy concerning other OS on the same HardDisk. Because I would expect Grub to not show up at all.

Using the live cd you can identify the UUID of your linux partition (depending on your setup this should be the start partition) by 
```
ls -l /dev/disk/by-uuid

```
The syntax of grub is (I believe...) hd(harddirve,partition) where first harddrive/partition is refered to as 0.
So using gparted in the live Cd should enable you to figure out which partition/UUID to use.
Also, if your boot sector is damaged you might download "SuperGrubDisc" (burn iso to cd and boot using it) to repaire it.

It's been a while since I had to cope with this, so my memory is a bit hazy, but I hope I could help.

---

### Post by jairom70 on 2009-01-20
total 0
lrwxrwxrwx 1 root root 10 2009-01-20 10:00 2b571526-14d4-4bfc-a61d-8f76eba33915 -> ../../sdb2
lrwxrwxrwx 1 root root 10 2009-01-20 10:00 6a88bdf8-cb8f-470d-8698-02522703a087 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2009-01-20 10:00 B0E04D53E04D20C8 -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-01-20 10:00 E07C265C7C262E2A -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-01-20 10:00 E42274D42274AD64 -> ../../sda2

thats what i ger when using 

ls -l /dev/disk/by-uuid

 and pretty much lsot after that lol.

---

### Post by Jense on 2009-01-20
Use ```
sudo fdisk -l
``` to identifiy which partition is your linux system. You will get something like ```
sudo fdisk -l
[sudo] password for jens:

Platte /dev/sda: 100.0 GByte, 100030242816 Byte
255 Köpfe, 63 Sektoren/Spuren, 12161 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xcccdcccd

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1        4462    35840000+  83  Linux
/dev/sda2            4463       10636    49592655   83  Linux
/dev/sda3           10637       12008    11020590   83  Linux
/dev/sda4           12009       12161     1228972+  82  Linux Swap / Solaris

```
Then you should be able to seperate which are Win and which are linux partitions. I don't know how you setup your partitions, so ...
With the other command you should then be able to assign the right uuid

---

### Post by jairom70 on 2009-01-20
ok so i did fdisk.

now i have both info so i put it like this?

title		Ubuntu 8.10, kernel 2.6.27-9-server
root            (hd0,1)
uuid		6a88bdf8-cb8f-470d-8698-02522703a087
kernel		/boot/vmlinuz-2.6.27-9-server root=UUID=6a88bdf8-cb8f-470d-8698-02522703a087 ro quiet splash vga=0x346
initrd		/boot/initrd.img-2.6.27-9-server

---

### Post by Jense on 2009-01-20
Sorry, I am really not sure here, but I believe UUID is an alternative to hd(0,1). Both are ways to identify any partition in your system, so.. If your linux system partition still exists and it is indeed sdb1? then your grub entry should be correct, which would point to a damaged boot sector - at least winxp does kill your bootsector if you install it after linux, so actually what you need to do is repaire the boot sector using "SuperGrubDisc" or a simular tool.
However, maby somebody else could give advice here, cause as I said I am a littel unsure about all this.

---

### Post by jairom70 on 2009-01-20
yes the boot thing was originally with thte uuid. and it is the same one i see when i run that commands u gave me not the fdisk. the loinger one.

but bootin u[ with  that.  i get error 17 file missing. i will look into that supergrub.

ty

---

### Post by Jense on 2009-01-20
Maby this post can help...
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)
or
[http://www.3till7.net/2007/10/25/grub-error-17/](http://www.3till7.net/2007/10/25/grub-error-17/)

It seems the win install did something so linux doesn't recognize the partition type. sorry, never had this error myself.

---

### Post by caljohnsmith on 2009-01-20
In order to get a clearer picture of your setup related to your boot problem, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

