---
title: "Boot error"
date: 2012-03-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by holytree on 2012-03-13
hey all i made a bootable usb stick of precise 12.04 beta 1 and after i boot into it it Shows


Boot Error
 and the underscore keeps blinking 
and then it goes into normal booting

and of
PLEASE HELP!!

---

### Post by zombifier25 on 2012-03-13
By "Normal Booting" did you mean the system booted into Ubuntu normally, or it never had the chance?

---

### Post by jerrrys on 2012-03-13
your boot log may tell you something

[http://ubuntuforums.org/showthread.php?t=49925](http://ubuntuforums.org/showthread.php?t=49925)

---

### Post by holytree on 2012-03-15
> **jerrrys said:**
> your boot log may tell you something

[http://ubuntuforums.org/showthread.php?t=49925](http://ubuntuforums.org/showthread.php?t=49925)



DID not help.... :(( now the it doesnt even boot from pendrive at all....!

---

### Post by holytree on 2012-03-15
> **zombifier25 said:**
> By "Normal Booting" did you mean the system booted into Ubuntu normally, or it never had the chance?


it booted normally :confused:

---

### Post by dino99 on 2012-03-15
> **holytree said:**
> it booted normally :confused:

if you have installed grub on /dev/sda (which is the default on a single hdd), then from a terminal:

sudo grub-install /dev/sda
sudo update-grub

---

### Post by holytree on 2012-03-16
Now It does nOt boot at all it gives error 
Error:ELF header smaller than expected
Please help !!!
Neither is it booting into ubuntu nor windows. !!!!

---

### Post by superbike on 2012-03-16
boy o boy!

get a lightweight linux into your pendrive (i'd use puppy and unetbootin) install grub into your system's mbr and add windows entry

alternatively :P

If you want your Windows 7 back then you have to use Windows 7 DVD to get into recovery console and then from recovery console you have to run the following command:

bootrec.exe /fixmbr

---

### Post by holytree on 2012-03-16
Unable to boot pen drive :((((

---

### Post by superbike on 2012-03-16
> **holytree said:**
> Unable to boot pen drive :((((

something should work
- check your bios setup and set it to boot from usb
- try with another pendrive
- try windows cd
- burn linux distro to cd and try

---

### Post by YannBuntu on 2012-03-16
superbike +1

Also, don't use 12.04 as it is still in development. Use last stable version: 11.10.

Once you can boot a CD or live-USB, if you still have boot problems, please indicate your [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1").

---

### Post by jerrrys on 2012-03-16
I think its still morning there.  Good morning YannBuntu.

@OP
And a +1 here too.

---

### Post by VinDSL on 2012-03-16
Only boot error I'm getting (recently) is...

Boot sequence cannot find my network.  :(

I get the flashing underscore for about 2-3 minutes, then it gives up and boots without a network connection.

The funny thing is, as soon as I get to the desktop, the network connection immediately pops up, with a notification dialog, and everything is fine.

---

### Post by YannBuntu on 2012-03-16
Please setup your BIOS so that the boot on disk is before the boot via network.

---

### Post by holytree on 2012-03-17
Thanks All!!!

Especially @Superbike that code saved windows.... :D

Thanks all for the help!!

Regards,
Holytree

---

### Post by holytree on 2012-03-17
> **superbike said:**
> boy o boy!

get a lightweight linux into your pendrive (i'd use puppy and unetbootin) install grub into your system's mbr and add windows entry

alternatively :P

If you want your Windows 7 back then you have to use Windows 7 DVD to get into recovery console and then from recovery console you have to run the following command:

bootrec.exe /fixmbr

uh windows up and running!!

Now UBUNTU!!  how to install grub is puppy linux required or can i use boot-repair?>? :D

---

### Post by YannBuntu on 2012-03-18
Puppy uses GRUB1, so i think it won't help (Ubuntu uses GRUB2).

I recommend you run Boot-Repair's "Recommended repair". A new BootInfo URL will appear, please indicate it if you have problems.

---

