---
title: "I didn't get the internship"
date: 2011-04-06
forum: The Cafe
---

### Post by Legendary_Bibo on 2011-04-06
I went to our school's big IT discussion panel thingy where my professor was going to introduce me to the representative from the company he recommended me to that had an internship for Linux people. He was also the only guy that didn't show up! The other companies there were looking for web developers and .NET people, and whatnot. 

It wasn't a total waste, they had a drawing at the end for T-shirts, wastebasket baskets (like basketball), a power supply, pens, and an OEM copy of 64-bit Windows 7. I won the copy of Windows 7. I almost took the power supply, but then I realized that I wasn't planning on building a desktop anytime soon, and I'm pretty sure the copy of Win7 was worth more than the power supply.

---

### Post by RiceMonster on 2011-04-06
It happens. Start applying for more jobs.

---

### Post by Legendary_Bibo on 2011-04-06
I guess I'll be doing a teaching internship this summer unless I can get into contact with them. Blah!

I really wanted to be exposed to more fields.

---

### Post by Dustin2128 on 2011-04-06
Well, you got a 200$ copy of windows 7. That must be worth... 200$..

---

### Post by matt_symes on 2011-04-06
Back luck. Keep your chin up though. It just means something better is around the corner. You just have to make find it or make it happen.

---

### Post by Legendary_Bibo on 2011-04-06
> **Dustin2128 said:**
> Well, you got a 200$ copy of windows 7. That must be worth... 200$..

The only computer in my house that could run it that isn't already running Win7 is my Ubuntu laptop, and it just seems like too much work to make a back up, install Win7, setup everything, then reinstall Ubuntu for a dual boot system, and set everything back up how I like it in Ubuntu.

---

### Post by Spr0k3t on 2011-04-06
I hated the .Net shops when I first got into technical work and programming.  It was like programming yourself into a corner making your code obsolete before final release.  Hang in there though, you will find something huge before long.

---

### Post by wilee-nilee on 2011-04-06
> **Legendary_Bibo said:**
> The only computer in my house that could run it that isn't already running Win7 is my Ubuntu laptop, and it just seems like too much work to make a back up, install Win7, setup everything, then reinstall Ubuntu for a dual boot system, and set everything back up how I like it in Ubuntu.

Just for info I doubt you would have to any thing but free a space for W7 put a NTFS partition there put a boot flag on it and install. The Windows before others is a myth.

---

### Post by Johnsie on 2011-04-07
Sorry you didn't get it. Don't limit yourself to just Linux jobs though... There is alot more to computers than just Linux, and that involves .NET and all the Microsoft stuff. Once you get into those jobs you can sometimes still get to use and work with Linux. Where I work most of the desktops are Windows-based, but I installed a Linux server and also installed Linux on my desktop and another persons so I still get to mess around on Linux. Working with Windows/.net isn't as bad as most Linux users think. There are actually alot of fun things you can to with Windows.

---

### Post by Legendary_Bibo on 2011-04-07
> **wilee-nilee said:**
> Just for info I doubt you would have to any thing but free a space for W7 put a NTFS partition there put a boot flag on it and install. The Windows before others is a myth.

Is there a guide? I'm thinking of using gparted to make an 80-100gb NTFS partition and hopefully the Windows 7 disk will see and use that without disturbing my Ubuntu partition. I'm still going to create a backup, I haven't created one, and my hard drive is sounding funny. I think it's going to start failing soon. Will grub set itself up though?

---

### Post by scouser73 on 2011-04-07
Their loss is someone else's gain mate.

---

### Post by manzdagratiano on 2011-04-07
> **Legendary_Bibo said:**
> Is there a guide? I'm thinking of using gparted to make an 80-100gb NTFS partition and hopefully the Windows 7 disk will see and use that without disturbing my Ubuntu partition. I'm still going to create a backup, I haven't created one, and my hard drive is sounding funny. I think it's going to start failing soon. Will grub set itself up though?

There is an even easier way.

1> Once you have set up a free partition, install Winblows to it without any worries - it will tell you that it is too lame to keep track of all the other OSes and therefore you will have to fix that yourself. But it will install all right.
2> After install, you have no grub, but have no fear! Throw in the Ubuntu LiveCD/LiveUSB, and then:
3> Unmount all mounted partitions, and then do ```
sudo fdisk -l
```, which will tell you what partition is what.
4> Mount the root partition (you will know which one from size and file type) somewhere, eg: ```
sudo mount /dev/sda1 /mnt
```5> Mount the boot partition inside the root partition, eg: ```
sudo mount /dev/sda2 /mnt/boot
```6> Then do: ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```This will rebuild your grub.
5> Do ```
sudo update-grub
``` and reboot. Voila! You shall have a perfect dual boot!

However, if you were to ask for a personal opinion, I would say that that copy of Windows 7 ain't worth cr*p, and I would tell you to throw it in the trash can, and live at peace with GNU/Linux. But of course, you didn't, and I didn't tell you :D

---

### Post by sydbat on 2011-04-07
> **manzdagratiano said:**
> There is an even easier way.

1> Once you have set up a free partition, install WinblowsYou lost me, and likely anyone else who takes computing seriously, right there. Please refrain from these childish attempts at humour. They make you look like someone who does not know what they are talking about.

---

### Post by Legendary_Bibo on 2011-04-07
I was thinking of popping in a live cd, using gparted to make the NTFS partition, and an extra partition, and once I install the live cd on the small partition it'll setup grub automagically, and then I can install windows on the NTFS partition then just do a grub update. Yes I'll be losing hard drive space, but it's a lot less of a headache. Unless I'm wrong and grub is still there, and actually not that hard to setup.

Does grub install even if you wipe the drive and put only Linux on it?

---

### Post by youbuntu on 2011-04-07
Aww mate, I'm sorry to hear of your bad news :(

However, look on the bright side - you got a free shaving mirror out of it :P

---

### Post by wilee-nilee on 2011-04-08
> **Legendary_Bibo said:**
> I was thinking of popping in a live cd, using gparted to make the NTFS partition, and an extra partition, and once I install the live cd on the small partition it'll setup grub automagically, and then I can install windows on the NTFS partition then just do a grub update. Yes I'll be losing hard drive space, but it's a lot less of a headache. Unless I'm wrong and grub is still there, and actually not that hard to setup.

Does grub install even if you wipe the drive and put only Linux on it?

When you install windows it will overwrite the mbr you will just have to reload the grub bootloader to the mbr, very easy stuff. You can also get back into Ubuntu with supergrub and load the bootloader from the terminal.

I'm not sure I understand your install schema so I'm a bit concerned there, so if you think you need help just ask.

If you wiped your drive when you install a distro using grub it will install basically. It is when you install windows after that you have to reload the MBR.

---

### Post by Legendary_Bibo on 2011-04-08
> **wilee-nilee said:**
> When you install windows it will overwrite the mbr you will just have to reload the grub bootloader to the mbr, very easy stuff. You can also get back into Ubuntu with supergrub and load the bootloader from the terminal.

I'm not sure I understand your install schema so I'm a bit concerned there, so if you think you need help just ask.

If you wiped your drive when you install a distro using grub it will install basically. It is when you install windows after that you have to reload the MBR.

I think I need a step by step guide. I can do the gparted thing, but I'm not so sure how I would install Win7 without it wiping out Ubuntu. 

I wish I could make a complete copy of everything and put it on an external HDD then just install Win7, and copy everything back over and just setup grub.

---

### Post by wilee-nilee on 2011-04-08
> **Legendary_Bibo said:**
> I think I need a step by step guide. I can do the gparted thing, but I'm not so sure how I would install Win7 without it wiping out Ubuntu. 

I wish I could make a complete copy of everything and put it on an external HDD then just install Win7, and copy everything back over and just setup grub.

You can with clonezilla.
[http://clonezilla.org/](http://clonezilla.org/)

It is pretty straight forward, you boot a clonezilla disc and it dd's the data for you, you just point it correctly, it's easy, you can copy the whole thing or a specific partition. The partition that the copy goes back into has to be the same size, so if you're limited to the one hd you could move some data off the partitions to be copied and shrink them with gparted to a size that leaves the room for what you want to install.

---

