---
title: "[SOLVED] Installing Slackware 12.0 like second OS"
date: 2008-01-15
forum: Slackware and derivatives
---

### Post by b0rka7a on 2008-01-15
Okay, I want to make Slackware 12.0 my second OS. I've just got a second hard drive and I'm afraid that if I install Slackware on it and after that I want to remove it for some reason, I'll not be able to boot my Ubuntu :confused: Can someone help me with that problem ?

[i]Edit: And I also want to know how to install ssh and vnc servers so I can control my pc from everywhere
Thanks in advance![/i]

---

### Post by MonctonJohn on 2008-01-15
Hi.

When you install Slackware it will ask you if you want to install lilo. Just skip the installation of lilo and you should be able to boot Ubuntu just fine.

---

### Post by fish2ways on 2008-01-15
Hi
You should have no problems installing Slackware either on a seperate hard drive or partition. 
You can choose to either let Slack install the Lilo boot loader which you will be able to add your Ubuntu install to. Or choose not to install a bootloader at all when asked during the Slackware install, then add Slack to your Ubuntu /boot/grub//menu.lst. 
It's up to you.
If you subsequently remove Slackware it won't make any difference to your Ubuintu install. Just edit either Lilo or grub to remove Slackware.
**_Read the Slackware documentation before you install. _**
Best of luck, Slackware is excellent and you'll learn a lot.

---

### Post by b0rka7a on 2008-01-15
That is what I did:
I detached my HDD with Ubuntu and left only the empty HDD. Next I installed Slackware on it and when the installation asked me to install LILO I chose No. After I rebooted, an error appeared:
```
GRUB Loading...
Error 13 *(or 15)*...
```
(I don't remember the number of the error)
I attached my Ubuntu HDD with the Slackware HDD and booted in Ubuntu. Now I have to add Slackware in /boot/grub/menu.lst, but I don't know what to type in it :(
Here's content of the file now:
```
........
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=976bf8ec-b1b3-40e2-858f-71925b78352d ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=976bf8ec-b1b3-40e2-858f-71925b78352d ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```
I see Slackware as /media/disk (/) and /media/disk-1 (/home).
In GParted, the Slackware HDD is shown as /dev/sdb.
Any help would be appreciated!

[i]***Edit:** Yep, the error is 15:
```
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 15
```
According to the [GNU GRUB Manual]("http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors") this error is:
15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.[/i]

---

### Post by b0rka7a on 2008-01-17
I deleted Slackware cause I don't like it. I had too much problems with it :) Now I'm back to Ubuntu.
Thanks for the answers ;)

---

### Post by kellemes on 2008-01-17
> **b0rka7a said:**
> I deleted Slackware cause I don't like it. I had too much problems with it :)


Nah.. Slackware had problems with you!
This is the way it gose so often, Slackware needs to like you (the user) in order to be tamed.. :)

---

### Post by b0rka7a on 2008-01-17
> **kellemes said:**
> Nah.. Slackware had problems with you!
This is the way it gose so often, Slackware needs to like you (the user) in order to be tamed.. :)

hmm... maybe :D :lolflag:

---

### Post by Antman on 2008-01-17
> **b0rka7a said:**
> I deleted Slackware cause I don't like it. I had too much problems with it :) Now I'm back to Ubuntu.
Thanks for the answers ;)

You should have tried Zenwalk before going back to Ubuntu. It's based on Slackware but makes things a little easier.

They are getting things ready to roll for the new version 5 release, so some of the download links aren't 100% functional yet, but give it a try if you still want to go with a slackware distro.

---

### Post by b0rka7a on 2008-01-17
I installed SuSE :) It's also based on Slackware and it's also user-friendly ;)

---

### Post by Antman on 2008-01-17
> **b0rka7a said:**
> I installed SuSE :) It's also based on Slackware and it's also user-friendly ;)

I think Suse is more akin to Redhat now then Slackware. But it too is a good distro... Once it goes to version 11 I will definitely try it again.


Edit:
This is interesting; I didn't know Suse's full history in regards to it's slackware roots. I was reading a wiki on it:
[http://en.wikipedia.org/wiki/SUSE]("http://en.wikipedia.org/wiki/SUSE")

---

### Post by andrew.46 on 2008-01-20
Sorry to hear of your trouble with my favourite distro:

> **b0rka7a said:**
> I installed SuSE :) It's also based on Slackware and it's also user-friendly ;)

There is an old saying: 'Slackware is actually *very* user friendly, it is just very picky about who it makes friends with'.

I have your setup in reverse, I have Slackware on hda1 and Feisty on hda3 with the following lilo.conf:

```
# Default boot is Slackware 12:
image = /boot/vmlinuz-generic-smp-2.6.21.5-smp
  initrd = /boot/initrd.gz
  root = /dev/hda1
  label = Slackware
  read-only 
# Secondary boot is Ubuntu Feisty:
other = /dev/hda3
  label = Feisty
  table = /dev/hda
```This is the Lilo version of chainloading where Feisty is selected by Lilo but loaded by Grub, which I installed in hda3 rather than the MBR. Or in Grub-speak: (hd0,2).

Just another way of doing things :-)

  Andrew

---

