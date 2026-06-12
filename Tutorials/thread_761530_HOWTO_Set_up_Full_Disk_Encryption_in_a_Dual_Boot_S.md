---
title: "HOWTO: Set up Full Disk Encryption in a Dual Boot System"
date: 2008-04-21
forum: Tutorials
---

### Post by epiphiny on 2008-04-21
Hi there, this is my first tutorial, so I apologise if it's a little rough around the edges.

**What This Covers**

This tutorial will allow you to create a basic dual boot system, using only free open source software, which is fully encrypted (apart from a boot partitioin).

I am **by no means an encryption expert**, so please do not take anything I say as cannon.

At the end of this tutorial, you will have a system in which both windows and ubuntu are completely encrypted, including swap space, the windows page file, and hibernation files.

**Warnings**

I have only tired this on a VMware virtual machine, and my HP 530 laptop.  I cannot guarantee it will work on any computer.

Also, this is not bulletproof.  It is difficult to change the LUKS passphrase, and does not support keyfiles.  You will therefore have to rely upon a very strong passphrase, which cannot change.

Also, your boot files will not be encrypted.  There are ways around this; you can save them to a USB key, and take that with you, or only mount your boot partition as read only.  If you choose the USB option, you must allow your computer to boot from USB, which could allow an attacker to boot a malicious opperating system from a USB key.  If you choose the read only option, an attacker can still modify your boot files if they are sufficiently motivated, and it will be difficult to update your kernel.

At the end of the day, you have to decide where to comprimise.  As a proof of concept, my set up uses a boot partition mounted read/write.

Ok, thats the nagging over, on to **the procedure**

1.  Install Windows XP

This *should* work with vista, but I've not tested it.

2.  Install ubuntu.

During the installation, use the altnerative CD.  At the partitioning phase, create a 400mb logical partitioin, and use the rest of the space to create a final parition.  This should be set to 'type Physical Container for Encryption', in the part where you select filesystem.

It will write changes to disk, just follow the wizard until you get back to the format screen.  The select 'set up encrypted partition' from the top of the menu.  Create a partition inside the encrypted partition, and set the type to Logical Volume.

Once the LV is set up, you can create new logical volumes for home, / and swap.  The standard rule is to use twice your RAM for your swap space.

Once all your disk is set up, it will ask you to create a passphrase.  Make sure it is a good one!

Continue with installation until you have a working system.

3.  Boot to windows, and install Truecrypt.

Within truecrypt, select full disk encryption.  Allow it to encrypt the windows partition ONLY, otherwise it will ruin your ubuntu installation.  Tell it windows is on your MBR.  It isin't, but we will address this problem later. Follow the instructions on screen; you will have to create a rescue CD and burn it.

4.  Reboot the computer, and check that you can boot to windows.

If you can, it will allow you to pass through the truecrypt boot loader, and get into windows.  You can then encrypt your entire windows partition.

5.  Restore GRUB

Boot to the ubuntu **Desktop** cd, and open a terminal.  Type 

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

to find your boot partition.  If your first guess is wrong, use

umount /mnt/boot/

and repeat with a different partition.  Your grub partition will include files grub and initrd

Now we need to copy the MBR.  This is set up by truecrypt, and contains your decryption files to boot the opperating system.

The command for this is;

sudo dd if=/dev/sda of=/mnt/boot/truecrypt.mbr count=1 bs=512
sudo dd if=/dev/sda of=/mnt/boot/truecrypt.backup count=8 bs=32256

Remember sda may be hda on your system.

This copies the MBR

Then start the grub sub-shell, with the command

sudo grub

remember the sudo, otherwise it won't work.  In grub, type

install (hd0,*)/grub/stage1 (hd0) (hd0,*)/grub/stage2 0x8000 p

repacing * with the partition of your disk.  Grub uses a diferent system to linux, so you will need to subtract one from your partition number.  Thus if your boot partition is sda4, grub will require (hd0,3)
(it doesn't matter if linux says sd or hd).

Finally, you need to set up grub to chainload your the image you took earlier, to load the decryption algorithm.

All you need to do edit /mnt/boot/grub/menu.lst so that your windows sections looks like

title           Windows XP Professional
rootnoverify    (hd0,0)
makeactive
chainloader (hd0,*)/truecrypt.mbr
boot

**Done!**  You should now be able to boot, see grub, and select windows.  This *should* drop you to the truecrypt bootloader, which will in turn allow you to boot windows after entering your password.  Similarly, selecting ubuntu should ask you for your password, then boot it.

My sincere thanks to Jari Eskelinen, who's tutorial I've borrowed heavily from.  This can be found at 

[http://keitin.net/jarpatus/articles/dcpp_grub/index_eng.shtml]("http://keitin.net/jarpatus/articles/dcpp_grub/index_eng.shtml")

I hope this helps anyone thinking of dual booting with encryption; it really is pretty easy!

If anyone has questions, please feel free to reply and I'll do my best to answer them (remember, I'm defiantly not an expert).
Also, if there is interest I will try and coax VMware into letting me take to screenshots to clear up the more confusing parts!

---

### Post by staticsage on 2008-04-22
Thanks for this! I've been meaning to try the dual boot full disk encryption with Truecrypt ever since they offered full disk encryption. I'll do this in a VM as soon as I find time to test it. If it works out for me, it'll go on my laptop.

Thanks again.

---

### Post by Distue on 2008-04-27
Hello, 

first thanks for the tutorial. It worked for me with Kubuntu 8.04 and Windows Vista Business.

I just had to do these modifications:

#1 

The dd commands need "sudo" in my case:

> dd if=/dev/sda of=/mnt/boot/truecrypt.mbr count=1 bs=512
dd if=/dev/sda of=/mnt/boot/truecrypt.backup count=8 bs=32256

to 

> sudo dd if=/dev/sda of=/mnt/boot/truecrypt.mbr count=1 bs=512
sudo dd if=/dev/sda of=/mnt/boot/truecrypt.backup count=8 bs=32256

#2

I have a boot partition, where the mount point is /boot, so /boot is not necessary:

> install (hd0,*)/boot/grub/stage1 (hd0) (hd0,*)/boot/grub/stage2 0x8000 p

to

> install (hd0,*)/grub/stage1 (hd0) (hd0,*)/grub/stage2 0x8000 p

Thanks again

---

### Post by Distue on 2008-04-27
Another point:

I've read somewhere that is not that good idea to create the swap partition with the logical volume manager due performance reasons.

---

### Post by epiphiny on 2008-04-27
Thanks Distue, good point well made - it's always easy to leave out stuff!  I've edited the post to include the changes.

You can certainly create another logical partition for encryption, set it to swap, and set it to have a random passphrase (its in the screen where you set the options like AES encryption etc).  That said, I haven't noticed any performance issues, but you can certainly change it if you think it will make a difference.

---

### Post by siouzi on 2008-05-02
You don't actually have to restore the grub, because you can ESC-key out of the truecrypt bootloader residing in MBR and it will look for any other bootable partitions. That is unless of course you want the linux bootloader to be on MBR and load linux by default (truecrypt bootloader will just sit there and wait for your input).

1. Install windows whatever
2. Install linux whichever way you want for dual or multi boot. Verify that you can still boot to windows and linux.
3. In linux **install the grub to a bootable partition** e.g. the /boot partition when using LUKS.
```

$ sudo grub
# n = the /boot (or root) partitions number minus 1
# e.g. if boot partition is the second partition on your drive, n = 1
grub> root (hd0,n)
grub> setup (hd0,n)

```
4. Install truecrypt in windows and encrypt the windows partition. Because of step 3 you can safely let truecrypt install the bootloader to MBR.
5. On boot, hit esc in the truecrypt prompt if you want to load linux (you'll see the grub menu).

Truecrypt is really good and smart software =)

---

### Post by epiphiny on 2008-05-02
That should work, but on my system it couldn't find the grub bootloader.  The way I wrote the tutorial should work regardless of how you've set up your system...

---

### Post by laltopi on 2008-05-03
Has anyone successfully encrypted an existing installation of ubuntu; or is a fresh install needed?

---

### Post by jesiah97 on 2008-05-06
perhaps you can detail the windows truecrypt procedures described in step 3.  It is a little confusing to a new user and one could easily ruin their ubuntu installation (like I may have!)

Thanks

---

### Post by -X- on 2008-07-15
Thannks a lot for the guide, worked well for me :)

---

### Post by gearond on 2008-07-17
I think the original developer of this got lucky or started grub from withing the grub directory (file location issues, error 15) For **ME** to make it work, I had to:

change
     install (hd0,5)/grub/stage1 (hd0) (hd0,5)/grub/stage2 0x8000 p
to
     install (hd0,5)/boot/grub/stage1 (hd0) (hd0,5)/boot/grub/stage2 0x8000 p

and change the menu line
     chainloader (hd0,5)/truecrypt.mbr
to
     chainloader (hd0,5)/boot/truecrypt.mbr


Notice the full path name, which is what I recommend. [Obviously, my linux installation is in sda6/(hd0,5), but that's not an issue]

Other than that, WooHoo!!!! it works, got them both working. And TrueCrypt said it couldn't be done <snicker>. Thank you to the writer of this article. 

I'm not really sure if the original version of extra code above the first sector  of the hard drive(if any) that truecypt uses is being used from that area starting at the 2nd sector, or if (hd0,5)/boot/truecrypt.backup is being used.

NOW, I want to get a *cloned* version of my basic Vista installation running with LoJack On it and a guest account. It will report where it is the first time it is turned on using the ONLY usable OS on the drive. I will have the BIOS locked out, so unless they want to replace the hard dirve or pull it apart and flash the bios. They are out of luck if they steal my drive <the ba****ds>

---

### Post by robpower on 2008-07-28
Thanks for the useful walktrough.
I have also an additional hint:
when changing the windows section in menu.lst, you have to change that line
```
title Windows XP Professional
**rootnoverify (hd0,0)**
makeactive
chainloader (hd0,*)/truecrypt.mbr
boot
```in```
rootnoverify (hd0,**x**)
```
where you have to change **x** with the partition where windows resides. 
You can find which number **x** stands for from the original Windows section of the menu.lst, at the line
```
title Windows XP Professional
**root (hd0,x)**
...

```

---

### Post by Keymaster on 2008-09-19
When trying to create swap I kept getting errors that it can't mount swap via the LVM  Here is the failed setup:
```

Encrypted Table:
-swap
-/
Regular table:
-WinXP
-/boot
-LVM

```
Right now I'm trying swap outside the encrypted partition. Probably not the most secure, but it should yield a performance increase, and fix my issue.  Besides doesn't swap get deleted on shut down?

---

### Post by Keymaster on 2008-09-19
I tried reinstalling grub and I am now getting an error 23 soemthing about parsing a number. Google hasn't been able to help me, and I need to get this working.  What can I do?  Thanks

---

### Post by Keymaster on 2008-09-25
I know TrueCrypt has the rescue disk, but how do you recover data off of a non-bootable LUKS partition, or if the system dies, and you need to recover the data via another machine?  Thanks

---

### Post by caroline.danon on 2008-10-09
Thanks !
Your first description (1st entry in this post) worked for me, taking along the adaptions of Gearond a few posts above. This because the grub-directory resides in the boot-directory. 

Works fine now.. 

Caroline

---

### Post by zimek on 2008-10-15
> **epiphiny said:**
> 
remember the sudo, otherwise it won't work.  In grub, type

install (hd0,*)/grub/stage1 (hd0) (hd0,*)/grub/stage2 0x8000 p

repacing * with the partition of your disk.


Everything is fine, great tutorial, but please tell me how can I do this 'install' command in grub2 ?

I have to use grub2 because I have many problems running ubuntu on Dell Optiplex 320, and in grub2 there is no 'grub' command, so I don't have access to grub's shell.

Regards

---

### Post by SCFC on 2009-01-02
Thanks epiphiny and the others,

I tried the process on an 8.10 install with XP and it worked.

Cheers

---

### Post by ubumar on 2009-01-09
Hi,
Thanks for a great tutorial. I havn't tried it yet, but it's exactly what I've been looking for and I'll give it a try on my laptop soon!
Does truecrypt and linux use the same encryption algorithm?
The follow up question is: If yes, can I mount the windows partition in linux and vice versa? (provided I have an ext2 driver etc)
Thanks

---

### Post by zachwoodham on 2009-05-09
> **ubumar said:**
> Hi,
Thanks for a great tutorial. I havn't tried it yet, but it's exactly what I've been looking for and I'll give it a try on my laptop soon!
Does truecrypt and linux use the same encryption algorithm?
The follow up question is: If yes, can I mount the windows partition in linux and vice versa? (provided I have an ext2 driver etc)
Thanks

That's a good point. I'd be interested in doing this, but I'd like to know as well. They would be using the same algorithm here I believe, but would that allow one to mount the Windows partition in Linux and vice versa?

---

### Post by tymtheenchanter on 2009-05-19
First off, thanks for the instructions, they worked perfectly first time :)


ubumar & zachwoodham
I haven't tried this yet, but you might be able to use truecrypt in linux to mount the windows system disk as a device?

-- Edit --
Just tried this and truecrypt has an option to mount an encrypted system volume. Works perfectly.

---

### Post by JustHall on 2009-10-26
Sorry to bump an old topic, but I can't seem to resolve an issue I'm having and people who read this thread may have more insight than I.

The instructions in this thread worked perfectly, however I would like to customize the TrueCrypt boot loader pre-boot authentication behavior. In TrueCrypt, under System -> Settings, you can check a box labeled "Do not show any texts in the pre-boot authentication screen (except the below custom message)" and then you can enter your own custom text in the box provided. Additionally, you can un-check a box at the bottom of this window labeled "Allow pre-boot authentication to be bypassed by pressing the Esc key (enables boot manager)" to prevent the Esc key from doing anything. This allows you to fake somebody into thinking your system is absent or corrupt.

Manipulating these options works great, until you get to the point where it's time to restore GRUB. Upon saving the TrueCrypt MBR and restoring GRUB, those settings seem to disappear. Selecting the Windows boot option in GRUB loads the standard TrueCrypt boot loader (full default text and you can press Esc, etc.), seemingly ignoring or losing the settings I had set prior to restoring GRUB.

Furthermore, now that TrueCrypt is no longer in the MBR, you can't go into the application and customize the options anymore. If you try, it brings up a message indicating that TrueCrypt isn't in your MBR so the settings may not be saved.

I assume these custom settings are stored in the MBR, but if that were the case then I would also assume they would be saved when you use dd to write the truecrypt.mbr file on your Linux boot partition.

Any thoughts or suggestions?

Thanks in advance.

---

### Post by mk4umha on 2010-01-03
> **JustHall said:**
> Sorry to bump an old topic, but I can't seem to resolve an issue I'm having and people who read this thread may have more insight than I.

The instructions in this thread worked perfectly, however I would like to customize the TrueCrypt boot loader pre-boot authentication behavior. In TrueCrypt, under System -> Settings, you can check a box labeled "Do not show any texts in the pre-boot authentication screen (except the below custom message)" and then you can enter your own custom text in the box provided. Additionally, you can un-check a box at the bottom of this window labeled "Allow pre-boot authentication to be bypassed by pressing the Esc key (enables boot manager)" to prevent the Esc key from doing anything. This allows you to fake somebody into thinking your system is absent or corrupt.

Manipulating these options works great, until you get to the point where it's time to restore GRUB. Upon saving the TrueCrypt MBR and restoring GRUB, those settings seem to disappear. Selecting the Windows boot option in GRUB loads the standard TrueCrypt boot loader (full default text and you can press Esc, etc.), seemingly ignoring or losing the settings I had set prior to restoring GRUB.

Furthermore, now that TrueCrypt is no longer in the MBR, you can't go into the application and customize the options anymore. If you try, it brings up a message indicating that TrueCrypt isn't in your MBR so the settings may not be saved.

I assume these custom settings are stored in the MBR, but if that were the case then I would also assume they would be saved when you use dd to write the truecrypt.mbr file on your Linux boot partition.

Any thoughts or suggestions?

Thanks in advance.


Hmmm, interesting, I was hoping this method would work the way I thought it would. maybe it's possible to enter 2 passwords? One for Windows, the 2nd one for Linux using truecrypt?

---

### Post by operat0r on 2010-06-05
*** SOLVED **

be sure the mbr file is loading from the right part .. DUH...

  ```


title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader (hd0,4)/boot/truecrypt.mbr




```
Not sure what I am missing I can't get windows to boot now:


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7256    58283788+   7  HPFS/NTFS
/dev/sda2            7257       14593    58934452+   5  Extended
/dev/sda5            7257       14288    56484508+  83  Linux
/dev/sda6           14289       14593     2449881   82  Linux swap / Solaris


head /boot/truecrypt.mbr
ê| TrueCrypt Boot Loader
°}èf;²}t%öF}uÆF}± ö·}u*6U}èS6|èLëþÀØúÐ¼ûRh´f3Û¾èºfS»
hzhhç|hËÄZÀt    6U}èþ6·}ÀØúÐ¼ükûhË3Û´ü¬ÀtÍë÷Ãµ¶´Ís6G}èàÿÃf3Àü¬fØfÑÃâ÷ÃDisk error


so I know the MBR was backed up properly


I know windows could boot before/truecrypt

here is my menu.lst

I treid adding the UUID line to the windows titles after none of them worked ... what am I missing ?

```

default         0
timeout         10
splashimage=b5d01231-261d-4694-a2c1-ec4063bd6d38/boot/grub/splash.xpm.gz

title           Ubuntu 8.10, kernel 2.6.30.9
uuid            b5d01231-261d-4694-a2c1-ec4063bd6d38
kernel          /boot/vmlinuz-2.6.30.9 root=UUID=b5d01231-261d-4694-a2c1-ec4063bd6d38 ro quiet splash
initrd          /boot/initrd.img-2.6.30.9
quiet

title           Ubuntu 8.10, kernel 2.6.30.9 (recovery mode)
uuid            b5d01231-261d-4694-a2c1-ec4063bd6d38
kernel          /boot/vmlinuz-2.6.30.9 root=UUID=b5d01231-261d-4694-a2c1-ec4063bd6d38 ro  single
initrd          /boot/initrd.img-2.6.30.9

title           Ubuntu 8.10, memtest86+
uuid            b5d01231-261d-4694-a2c1-ec4063bd6d38
kernel          /boot/memtest86+.bin
quiet


title           Other operating systems:
root


title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

title Windows XP Professional
rootnoverify (hd0,0)
uuid            b5d01231-261d-4694-a2c1-ec4063bd6d38
makeactive
chainloader (hd0,0)/boot/truecrypt.mbr
boot

title Windows XP Professional 2
rootnoverify (hd0,0)
uuid            b5d01231-261d-4694-a2c1-ec4063bd6d38
makeactive
chainloader (hd0,0)/truecrypt.mbr
boot


title Windows XP Professional 3
rootnoverify (hd0,4)
uuid            b5d01231-261d-4694-a2c1-ec4063bd6d38
makeactive
chainloader (hd0,4)/truecrypt.mbr
boot


title Windows XP Professional 4
rootnoverify (hd0,4)
uuid            b5d01231-261d-4694-a2c1-ec4063bd6d38
makeactive
chainloader (hd0,4)/boot/truecrypt.mbr
boot





title Windows XP Professional 5
rootnoverify (hd0,1)
uuid            b5d01231-261d-4694-a2c1-ec4063bd6d38
makeactive
chainloader (hd0,1)/boot/truecrypt.mbr
boot


title Windows XP Professional 6
rootnoverify (hd0,1)
uuid            b5d01231-261d-4694-a2c1-ec4063bd6d38
makeactive
chainloader (hd0,1)/truecrypt.mbr
boot




```

---

### Post by xenosaga456 on 2010-06-24
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
its gives me erroe 15 ??

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




you can see my problem on youtube
[http://www.youtube.com/watch?v=-AcrNITmXW4]("http://www.youtube.com/watch?v=-AcrNITmXW4")

---

### Post by xenosaga456 on 2010-06-25
hey i fied it

---

### Post by xenosaga456 on 2010-06-25
well what i did was really complicated
but i dloaded super grub disk
then i used it to get to the origonal boot loader and ran grub from there
then i wrote grub to the MBR 
next i used a live CD to open my /boot hard drive and went to my grub and copyed it from there and pasted it to the /boot folder
then i rebooted it 
now trucrypt says press 'ese' to see othe hdd
then it boots from sda8 to grub where i can start ubuntu or windows if i want

---

### Post by iniju on 2010-09-05
Hi xenosaga456,

I'm trying to follow the step that you described above, as I am also getting the error 15.

Could you please detail explain in a bit more detail the super grub disk step?

Thanks and regards

---

### Post by anirudh.srivathsa on 2011-06-29
If i change the passphrase for encrypting the system, will it affect the key generated? will it affect the data present in the system?

---

### Post by guimaster on 2012-10-21
> **epiphiny said:**
> Also, your boot files will not be encrypted.  There are ways around  this; you can save them to a USB key, and take that with you, or only  mount your boot partition as read only.  If you choose the USB option,  you must allow your computer to boot from USB, which could allow an  attacker to boot a malicious opperating system from a USB key.  If you  choose the read only option, an attacker can still modify your boot  files if they are sufficiently motivated, and it will be difficult to  update your kernel.

At the end of the day, you have to decide where to comprimise.  As a  proof of concept, my set up uses a boot partition mounted read/write.

 What does this comment mean? Can someone actually modify the boot partition to enable getting around the encryption? :confused:

 Thanks.

---

