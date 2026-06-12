---
title: "The new Z77 mobo and Ubuntu 12.04 and dualboot"
date: 2012-05-11
forum: The Cafe
---

### Post by loseby on 2012-05-11
The problem I has was if i tried to dual boot the system Windows 7 wouldnt boot correctly. 12.04 worked without a hitch. Tried heaps of things and in the after 3 windows reinstallations I gave up. No proof to back my theory up but I think something in the new BIOS system ( UEFI or whatever it is ) is doing some weird thingsand I have no idea. GRUB couldnt locate anything about Windows and if I unplugged the 12.04 drive nothing was there when I tried to boot win 7.


I have just removed the drive ( a ssd ) and put it in another machine ( a older 58 motherboard chipset and a bIOS that I understand )., just plugged it in, hit the 'del' key and went into BIOS and made the 12.04 SSD as 1st bootable drive. After booting  I did a grub update ( long story on what happened previously ) and 2 copies ofwin7 lodder was there.....REBOOTED and selected win7 from loader and it booted into windows.

Now I have a dual boot and it will mean swapping actual PC's so the dual boot is where I want it  ...   no idea why the Z77 wouldnt work and am posting this here because I am not after help, I am not going near it again but would be interested in some discussion on 'theories':P

---

### Post by Lucradia on 2012-05-11
Problem though isn't likely with the motherboard itself, it's likely the connections such as SATA 3.0 Gbps. I don't think the Z77 has any BIOS Locking system yet. If it does, it probably starts in unlocked mode, since you bought it alone.

It could also be the order in which you install OSes determines who will boot, and who will never be able to boot again. (You need to install Windows first, THEN Ubuntu. If you want to do Ubuntu on its own partition, have Windows take up the whole thing, then IN WINDOWS resize the partition smaller. Doing it in Ubuntu causes problems.)

If all else fails, use Fedora after installing Windows, seems to play nicer. (Though will leave you annoyed when you can't eject the CD Tray until Fedora starts up for the first time normally after installation.) Don't install Ubuntu via command line either, for some reason, it won't work if you install it to an NTFS Drive (if you didn't resize or are overwriting it.) it'll complain GRUB didn't install correctly. (LILO gives a Kernel Panic >_>)

Have had this last problem ever since I started using Ubuntu 10.x series and newer.

---

### Post by loseby on 2012-05-11
could be

but windows was installed on a seperate SSD and booted and updated..... worked perfectly

then I connected the Ubuntu 12.04  SSD and Windows basically wouldnt work


Curious to why a installation of Ubuntu would wreck a different hard drive...1st time was with a Seagate 1TB hard drive and last time was with a new SSD


... drives were connected to Sata III

---

### Post by wilee-nilee on 2012-05-11
To be honest I have watched all the threads you have made and my conclusion is you're learning, I suspect all your problems were basically user errors. No biggie we all start somewhere, you just have to have actual cause and effect.

Your thinking that Ubuntu broke something is an error. :)

It was the way you used it that broke anything.

The mobo is on the web as working fine.

---

### Post by Lucradia on 2012-05-11
> **wilee-nilee said:**
> To be honest I have watched all the threads you have made and my conclusion is you're learning, I suspect all your problems were basically user errors. No biggie we all start somewhere, you just have to have actual cause and effect.

Your thinking that Ubuntu broke something is an error. :)

It was the way you used it that broke anything.

The mobo is on the web as working fine.

Installing Ubuntu shouldn't break my MBR / boot. But it does. So it is ubuntu's fault >_> it only happens when I do it via command line though, with all default options checked, (but no DE / GUI added, just CLI Install.) One of four errors occurs every time:

1. GRUB Failed to Install Correctly. (Cannot ever continue. Have to use normal ubuntu disk, or re-install windows or use Wubi after installing windows.)

2. GRUB Installed Successfully. Can't Boot, black screen or purple screen occurs. (Have to repair GRUB via another distro or way.)

3. LILO Installed Successfully. Can't boot, gives Kernel Panic.

4. ubuntu noticed this harddrive is part DOS and part something else. Would you like to treat it as one or the other? (Treating it as the "Other" causes ubuntu not to boot. Treating it as DOS causes it not to boot. Have Ubuntu overwrite it completely with what it thinks best.)

Number 4 usually happens if Number 1 happens and I go to install it via the normal GNOME CD-ROM / DVD. Number 1 happens if Ubuntu tries to overwrite an NTFS Partition via CLI Install. Number 2 happens usually if it overwrites the NTFS Partition correctly, but fails to manage the Boot priorities.

After I get through all that, I have to quickly disable jockey-gtk, since installing either "Recommended Driver" causes the ubuntu OS never to show itself again (no way to revert either, since CLI won't show up via TTYs.) NVIDIA GTX 470's propietary drivers via jockey seems to be borked in ubuntu as such.

/endrant

That's nothing though. if I install Windows 7, I have no Internet :P (My motherboard's Intel LAN has no generic driver for Windows 7 and prior.)

---

### Post by wilee-nilee on 2012-05-11
> **Lucradia said:**
> Installing Ubuntu shouldn't break my MBR / boot. But it does. So it is ubuntu's fault >_> it only happens when I do it via command line though, with all default options checked, (but no DE / GUI added, just CLI Install.)

If you give me a detailed description I would bet I can show you where it is going wrong. This would include running the bootscript so I can see your setup.

Ubuntu will do what you tell it, and balk generally when it is a given a bad command or gui instructions.

Open source has a lot of control it generally is in the hands of the user.

If you can fix the boot after a broken install your argument makes no sense to be honest

---

### Post by Lucradia on 2012-05-11
> **wilee-nilee said:**
> If you give me a detailed description I would bet I can show you where it is going wrong. This would include running the bootscript so I can see your setup.

Ubuntu will do what you tell it, and balk generally when it is a given a bad command or gui instructions.

Open source has a lot of control it generally is in the hands of the user.

If you can fix the boot after a broken install your argument makes no sense to be honest

it happens DURING install. CLI Install won't even CONTINUE setup if GRUB fails to install.  (Red screen of death, brings me back to the CLI Install List.)

use the [mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD") for what I mean. (Do CLI Only Install, not the normal install.)

---

### Post by wilee-nilee on 2012-05-11
> **Lucradia said:**
> it happens DURING install. CLI Install won't even CONTINUE setup if GRUB fails to install.  (Red screen of death, brings me back to the CLI Install List.)

use the [mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD") for what I mean. (Do CLI Only Install, not the normal install.)

I will try it in a virtual.

---

### Post by wilee-nilee on 2012-05-11
@Lucradia

Are you doing the expert cli?

---

### Post by wilee-nilee on 2012-05-11
> **Lucradia said:**
> it happens DURING install. CLI Install won't even CONTINUE setup if GRUB fails to install.  (Red screen of death, brings me back to the CLI Install List.)

use the [mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD") for what I mean. (Do CLI Only Install, not the normal install.)

I did a expert cli install no problems, not sure if this is the  same cli you are using. I did see this message I chose the  targeted.

[ATTACH]217715[/ATTACH]

I rebooted grub loaded me to the cli login and I installed lxde and  everything looks good. Let me know if this was the cli you used if you  can. It  would be nice to get you able to install the way you want.

I wonder if you are running a raid or gpt setup, that is why I mention the bootscript earlier it will tell us.

---

### Post by Bandit on 2012-05-11
I have ran into this before, but it was trying to install dual boot onto a stripped array and the installation would hang up at the end were it was supposed to install GRUB. From what I gathered its a long standing Debian install bug thats be greatly ignored.

Best bet to keep this straighted out is to keep both Windows and Ubuntu on your main bootable drive (sda perhaps) as well as GRUB, if you put Ubuntu on a seperate drive, or windows, sometimes it will get ignored or cause GRUB to have a brain fart. 

Like Ludi mentioned, install windows first becuase the win bootloader doesnt like other OS's, then Ubuntu. GRUB will be installed to the MBR, it has to be or how else will to see both systems. And you will want Lin and Win on separate partitions. Ideally if you have 100GB drive, partition the Win with 50GB when you install win and let Linux have the rest on its installation, less 5GB for swap. This is the best way IMHO.

If after installing everything is peachy, but the drive will not boot up in the system. Check your boot order to make sure that particular drive is set to boot. All else remove the other drive to see make dang sure its the only one set to boot. If if that still doesnt work, check HDD compatibility with that motherboard. Yes in some cases hard drives will not work with some boards, its a rare thing, but happens.

---

### Post by loseby on 2012-05-11
> **wilee-nilee said:**
> To be honest I have watched all the threads you have made and my conclusion is you're learning, I suspect all your problems were basically user errors. No biggie we all start somewhere, you just have to have actual cause and effect.

Your thinking that Ubuntu broke something is an error. :)

It was the way you used it that broke anything.

The mobo is on the web as working fine.

I am learning and I dont think Ubuntu broke something. Have the dual boot working fine on this 58 chipset motherboard. Also Ubuntu worked very well on the Z77 as a solo boot and even when I made it a dual boot but in that case Windows was destroyed.

And thats was has me puzzled  ....  I dont intend changing anything any more ...but I would Like to know why

---

### Post by wilee-nilee on 2012-05-11
> **losbey said:**
> I am learning and I dont think Ubuntu broke something. Have the dual boot working fine on this 58 chipset motherboard. Also Ubuntu worked very well on the Z77 as a solo boot and even when I made it a dual boot but in that case Windows was destroyed.

And thats was has me puzzled  ....  I dont intend changing anything any more ...but I would Like to know why

I doubt we will find out to be honest, use the custom install named something else in the gui on the install that asks where you want it. You have complete control from there you can resize and rewrite partitions there, and point grub to the correct place as well.

This custom install method is quite similar to the custom install of a MS install as well, I would never trust a auto install when you can use a custom. You are then sure where your new OS is going.

---

### Post by oldfred on 2012-05-11
@   	losbey
Part of the issue is the new Z77 has UEFI which adds a level of complexity. I think all UEFI systems also boot in BIOS mode so that should always work. But if one system is BIOS and another UEFI then you definitely will have issues.

All the users that successfully installed with UEFI partitioned in advance with gpt and efi partition first. Then all the partitions required for Windows and/or Ubuntu. then they boot the installer in UEFI mode.  That is a lot different than the standard BIOS/MBR installs we all are used to.

 I do not think any of the auto modes work yet with UEFI with perhaps the single install to an empty drive. But even that may not work as grub had issues with very large / (root ) partitions.

---

### Post by loseby on 2012-05-12
> **oldfred said:**
> @   	losbey
Part of the issue is the new Z77 has UEFI which adds a level of complexity. I think all UEFI systems also boot in BIOS mode so that should always work. But if one system is BIOS and another UEFI then you definitely will have issues.



I think you are right oldfred   ... I dont have any real experience on the new UEFI Bios or how it works.  I have noticed that in Boot Option priorities that the list only displays the device with the highest priority for that device


Anyway have physically moved computers and now have the dual boot where I want it and the Z77 is now setup as a pure gaming machine. 


anyway, thanks to all for the replies

---

