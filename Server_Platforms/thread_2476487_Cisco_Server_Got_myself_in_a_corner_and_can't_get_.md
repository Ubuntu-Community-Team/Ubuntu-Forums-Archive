---
title: "Cisco Server Got myself in a corner and can't get out"
date: 2022-06-27
forum: Server Platforms
---

### Post by solarczar on 2022-06-27
Hey guys,

First post.  I came across an opportunity to acquire a Ciscos C220 M4 enterprise server.  installed Ubuntu 20.04.  After some going some directions with nextcloud, home asst, and some other apps, I decided that I wanted to redo my platform and start from a fresh install, and upgrade to 22.04 and go to UEFI.  What a mess.  Tried to go back to Legacy BIOS and couldn't get out of grub rescue or grub, despite all the online reading and grub commands for the last 3 days.  Elected to erase the disk and start completely over.  I'm not an OS chef.  I just want to follow you smart guy's recipes in order to load the software that I really want, but struggling.  Currently, I'm booted in via Ubuntu usb "Try Ubuntu" and using terminal, and running dd to overwrite sda & sdb.  I have no idea what I'm doing.  Everytime I tried to erase and reinstall Ubuntu, it gives me a myriad of issues with partitions that I don't understand the nuances.  How can I simply erase back to a blank drive and reinstall?

---

### Post by oldfred on 2022-06-27
Moving to the server sub-forum.
What are the specs of your server. It looks like it has a million options, from drives, CPUs, to even power cords.

Looks like a PC type Aptio UEFI/BIOS which may make it a bit more standard. But they mention settings to configure many extra things.

Do not know servers.

But with standard PC, you want gpt partitioning for UEFI install. And now should even use gpt partitioning over very old MBR(msdos) partitioning for BIOS/Legacy/CSM type installs.  With gpt you need an additional ESP - efi system partition. With BIOS & gpt, you need a bios_grub partition.

Does it have more than one drive. And then how are drives configured?
Are you installing server version?

I do not know servers but having more info may help those that do.

---

### Post by grahammechanical on 2022-06-27
So you have 2 drives, sda & sdb. Use the Ubuntu live session and run GParted. This program will let you set a new partition table for a drive. That will erase all data on the drive. The default choice is msdos do not choose that option. The GUID partition table (GPT) is better. GParted may give you the option to format the drive. Choose Ext4. Unless you want one of the other format types.

[https://gparted.org/display-doc.php%3Fname%3Dhelp-manual](https://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

Then you can use the Ubuntu live session to install Ubuntu using the Erase disk and install Ubuntu option. That will create the necessary partitions.

Do you know if the motherboard is BIOS or UEFI? We can install Ubuntu on a BIOS motherboard with a GUID Partition Table. If the motherboard is UEFI then you must use the UEFI utility to load Ubuntu in UEFI mode and then Ubuntu will install in UEFI mode.

Regards

---

### Post by solarczar on 2022-06-28
UEFI Utility?  Don't know what that is, but will be searching.  Found this after 3 days and it worked.

I followed some advice and did a new install using the advanced options (don't use the "erase disk and install ubuntu") using these partition settings:

[LIST=1]
[*]Create a 1 GB (1024 MB) ext4 partition on the ***beginning*** of the disk; mounted in "/boot"
[*]Create your desired install space in ext4 mounted in "/" **MINUS your swap area**
[*]Use remaining space for swap. (ALL partitions will be primary)
[*]In the boot install dropdown menu, select your "/boot" partition. **Not the defaulted drive root!**
[/LIST]

---

### Post by oldfred on 2022-06-28
That would be a BIOS install to old MBR partitioning. Really old instructions.

You should always install grub2's boot loader to a drive. Usually same drive as install, but it can be any drive. That drive then must be default boot drive in UEFI/BIOS settings.
With UEFI it always installs to first drive's ESP, and install options that work for BIOS to choose drive, do not work with UEFI.

UEFI would also need an ESP - efi system partition and really should use gpt partitioning.
BIOS with Ubuntu can use gpt, but needs the bios_grub partition.

---

### Post by solarczar on 2022-07-07
Ok, now I'm really confused.  You guys are a hell of lot smarter than me, so you may have to dumb it down a bit.  I'm not sure we can make it any more complicated?  Ok, I'm starting over and been reading this for a week and about to take the plunge.  I got Linux Mint working, using the "really old instructions", but I don't like it, so trying to get back to Ubuntu 22.04.  I can't figure out from the "New Instructions" exactly what to do.  It's all over the place. Why can't the smart people make it just recognize the hardware and UEFI bios settings and install?  Let me throw some spaghetti at this wall and see what happens.  As I read this statement..
[B]
Partitioning
[/B][B]New user with only 50GB for Linux only needs / (root) as ext4. And ESP if UEFI. 
If more space then smaller / of 25 to 30GB & rest as /home. Or more advanced use data partition(s) for your data.

[/B]
[LIST=1]
[*]Create a 1 GB (1024 MB) EFI partition on the ***beginning*** of the disk
[*]Create install space in ext4 mounted in "/" **MINUS your swap area**
[*]Use remaining space for swap. (ALL partitions will be primary)
[/LIST]

Does this sound right?

---

### Post by solarczar on 2022-07-07
Well that didn't work.  Got an error that I needed to have a BIOS Reserved space.  Added that after the EFI partition, and got an error that EFI could not be mounted.  This is so frustrating! All I care about is running my apps, and Linux is turning out to be the finicky player.

Any direction would be appreciated. 

[IMG]https://ubuntuforums.org/blob:https://ubuntuforums.org/b214f25c-6884-4378-aace-c22c2943488e[/IMG]

---

### Post by solarczar on 2022-07-07
Well, I think I figured out my problem.  I rebooted and instead of booting to the USB, was able to boot into EFI and was able to erase and reload Ubuntu.  Sorry for the drama, but I think I'm good now.

---

### Post by TheFu on 2022-07-08
> **solarczar said:**
>  I'm not sure we can make it any more complicated?  

Well, is that a challenge?  I can definitely make almost everything here really complicated, but I suspect that isn't truly desired.  ;)   
I'll go away now.  

This stuff is supposed to be fun, but the early stages have a very steep learning curve, especially for a desktop-only person, or, worse, someone with only non-Unix experience.  We were all like that, but sometimes forget all the frustrations we had 25+ yrs ago when we were beginners.  I doubt anyone is smarter than you. Our knowledge in this 1 area is just deeper than yours.

This is fun.  Remember that.

---

