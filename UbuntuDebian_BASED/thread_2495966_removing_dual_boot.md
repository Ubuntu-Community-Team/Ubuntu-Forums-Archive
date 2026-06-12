---
title: "removing dual boot"
date: 2024-03-09
forum: Ubuntu/Debian BASED
---

### Post by jkimble62 on 2024-03-09
i have tried a few different "flavors" of linux. now my boot menu if crazy with the last OS Neon, and want to uninstall it...
i want the other 3 OS in the menu (yea im booting to 4 diff OS's) i am a newbie and not good terminal/command line, so i am uninformed (not stupid, yes stupid) LOL

---

### Post by guiverc on 2024-03-09
You've provided no actual OS details, which is the starting point.

Almost all my systems are dual boot, many of my boxes having many installs (up to four), this box has two versions of Ubuntu & a windows, another has Ubuntu, Fedora & OpenSuSE.

There are two booting modes; modern hardware tends to booting using uEFI which relies on a ESP or EFI System Partition which is given control. You can have many partitions on a disk, but only one will be marked as the ESP (ie. only a single partition can be active as ESP).  With legacy boot, only a single drive will be active which is controlled by the machine *firmware* or BIOS settings. That drive's first sector, the MBR will be used to control boot.

Only a single OS controls the booting system however, and this is the one you need to matter.. On this machine I'm using now, it's Ubuntu *noble*, so to make changes I'd boot into that OS and make changes there.

To have it update what is available, I simply need to run `update-grub` (though this is the command for Ubuntu & Debian, it'll differ if I was using OpenSuSE, Fedora etc)

```

root@d7050-next:~#   update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/lubuntu-grub-theme.cfg'
Generating grub configuration file ...
Found theme: /usr/share/grub/themes/lubuntu-grub-theme/theme.txt
Found linux image: /boot/vmlinuz-6.8.0-11-generic
Found initrd image: /boot/initrd.img-6.8.0-11-generic
Found linux image: /boot/vmlinuz-6.6.0-14-generic
Found initrd image: /boot/initrd.img-6.6.0-14-generic
Found linux image: /boot/vmlinuz-6.2.0-21-generic
Found initrd image: /boot/initrd.img-6.2.0-21-generic
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Found Ubuntu 22.04.4 LTS (22.04) on /dev/sda7
Adding boot menu entry for UEFI Firmware Settings ...
done

```

ie. I can see it detected the current system (*where it listed the kernels*), and also a windows 11 boot managerand my other OS which is Ubuntu 22.04.

If I'd removed the windows system off the disk, that would not have been found and thus would not be offered in grub.

If however I'd run that same command in Ubuntu 22.04 LTS instead of my current Ubuntu *noble*, the output may have looked pretty much identical (except it'd listed Ubuntu 22.04 LTS kernels, and just had an entry near the end which said Ubuntu development release alpha being offered, however that is what I'd see on screen when it was run but it **may have made ANY DIFFERENCE** to what I see when I boot depending on how your system boots.

This system boots using uEFI, however not all machines do.  That can make a difference (*with BIOS I'd not have used the 'may have made no difference' but instead used 'would not have made any difference'*). Your BIOS settings can control what happens.

If I want to make an OS control the boot process; I boot it and instead of `update-grub` I'll use the `grub-install` which will make that OS control the boot.

I have a machine which has 3x Ubuntu installed plus a Debian install.  I use it for QA purposes & somewhat regularly re-install Ubuntu systems on it; it currently has a *jammy* (22.04), *mantic* (23.10), *noble* (24.04) & Debian (*trixie*). When I re-install one of *jammy* or *noble* currently (*which is done roughly weekly for each*) which ever I re-install will control the booting of that OS, and its grub will control boot. I confirm all OSes are good as part of the QA process, lastly will be my boot of the Debian GNU/Linux system where I'll also run an `grub-install` to make it take ownership of the boot process (*my preference on that box*). If you last installed Neon, it'll likely control the boot process; so ensure another OS you'll keep controls it BEFORE you delete the Neon partition(s).

Also note grub versions can matter, Grub 2.06 changed the defaults of prior versions of grub; so if you're using an OS that uses grub 2.06 & later, there maybe more involved.. Ubuntu & Debian are different in this regard (just as Debian/Ubuntu are different in commands to OpenSuSE/Fedora in prior commands I used), but Ubuntu has kept the behavior of older versions of Grub as the default; for Debian/Fedora/OpenSuSE & others I just have to use a text editor to switch the default so the 'update-grub' equivalent command will scan for other OSes like I describe above. ie.  the OSes involved & versions can influence what is required (*and you didn't provide specifics or releases*).

---

### Post by jkimble62 on 2024-03-09
what info can i provide to you to help???
is there a command line to get that info?
im sorry im so uninformed and need help. but thank you for helping me

---

### Post by oldfred on 2024-03-09
You have to make sure your preferred install is the one in control.
Usually UEFI/BIOS/grub make last install the default boot. If you uninstall that one, before changing to your preferred, you may not be able to boot.
Make sure you have good backups & a live installer for current version of every system you may want to keep.

this will show where everything is. Its default repair will pick one install, maybe not the one you want. Only use advanced mode if running fixes with multiple installs.  If we see the detailed report we then can made detailed instructions.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Let us know which install you want as default boot.
And good to know hardware, brand/model system and what video card/chip?

---

### Post by coffeecat on 2024-03-10
Not a chat thread, so moved to a technical support sub-forum. Three of the OP's operating systems are unknown, but since the only OS identified is KDE Neon, which is not an official flavour of Ubuntu, I've moved this to the ***Ubuntu/Debian based*** sub-forum.

---

### Post by jkimble62 on 2024-03-10
sorry i posted this here because i want to use unbuntu as my primary boot and trying to how to uninstall other OS's

---

