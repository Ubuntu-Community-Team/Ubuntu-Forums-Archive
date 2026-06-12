---
title: "Stuck at grub rescue after installing ChaletOS"
date: 2018-04-03
forum: Ubuntu/Debian BASED
---

### Post by lucianam42 on 2018-04-03
Hello, I'm posting this here, since I've sent a message to the ChaletOS team and I don't get a response. I've spent several hours googling but I haven't found a solution. 
I installed ChaletOS 16.04 from a USB stick in a new partition I created (*) (I also created a swap partition). When the installation finished and rebooted, I was directly sent to the grub rescue shell, with this message: "error: unknown filesystem". After investigating, I realized that the "root" and "prefix" grub variables were pointing to the wrong partition. The steps I followed were these:

1) [FONT=courier new]set root=(hd0,msdos2)/[/FONT]  [COLOR=#ff0000]*-> When issuing the command: "[FONT=courier new]ls (hd0,msdos2)/[/FONT]" it shows the linux root, so I know it's the correct partition.*[/COLOR]
2) [FONT=courier new]set prefix=(hd0,msdos2)/boot/grub/i386-pc[/FONT]   [COLOR=#ff0000]* -> here is where I found all the .mod grub files where at.*[/COLOR]
3) [FONT=courier new]insmod normal[/FONT]   [COLOR=#ff0000]*-> This is where the problem is. I get this error: **[FONT=courier new]symbol not found: 'grub_divmod64'[/FONT]**.*[/COLOR]

All the answers I've found to this problem said I should boot from a live CD (or USB) and reinstall grub, but the thing is I can't even do that. My BIOS boot priority is correctly configured to boot from my USB stick first (it's a netbook, I don't have a CD drive), still, "grub rescue" is the first thing I see, and I can't get out of it.

I'm completely locked outside of my computer and about to cry. Does anybody know how to solve this? :'(
Thanks in advance!

PD: (*) extra info just in case it's relevant: Before this whole thing, I had 3 partitions:
1) Linux Mint 13
2) a broken Windows 7
3) fat32 partition for data in general
To install ChaletOS I erased the first 2 partitions, and created a new one for ChaletOS and a swap partition too.

---

### Post by wildmanne39 on 2018-04-03
Hello and welcome to the forum!

*Thread moved to **Ubuntu/Debian BASED, a more appropriate forum**.*

---

### Post by oldfred on 2018-04-03
Do not know if it works on your Chalet installer.
You may need Ubuntu live installer and add ppa to it.
It may work or just be missing  a command or two.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by lucianam42 on 2018-04-03
Hello oldfred! thanks for replying. 

The problem is that I can't boot from any Live CD, I tried with the same Chalet live installer, with the live versions of SuperGrub, Boot-Repair, and even GParted. None of those booted. It always goes to the grub rescue shell. It's so frustrating, because I was perfectly able to boot from USB when I installed Chalet, and now I can't :(

---

### Post by oldfred on 2018-04-03
Is system UEFI?
It has a fast boot setting that assumes no changes to hardware nor configuration and immediately starts booting. Or booting the non-working system.
Your system may need to "cold" boot rather than a warm reboot.
If laptop remove battery.
Power down system & unplug it. Hold power switch for 10 sec or so.
Then see if you can boot and press correct key to either get into UEFI/BIOS (often f2 or del key) or UEFI/BIOS boot menu key often f10 or f12.

---

### Post by lucianam42 on 2018-04-08
Hi oldfred! I apologize for the delay. I tried what you said, and it worked!! :D After that it let me boot from my USB stick with a SuperGrub live version, from which I was able to boot my Chalet installation. Then I ran the following commands: ```
sudo grub-install /dev/sdX  #(in my case, sda)
sudo update-grub
```  

After that, grub was fixed, no more grub rescue :)

Thank you so much!!!

---

