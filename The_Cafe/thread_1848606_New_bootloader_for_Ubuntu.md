---
title: "New bootloader for Ubuntu?"
date: 2011-09-22
forum: The Cafe
---

### Post by j814wong on 2011-09-22
After seeing the LightDM login screen, I began to think think that a similar UI style could be used as for a bootloader.  Windows 8 has a new bootoader and it looks much nicer then the old ones.  Yes I know that aesthetic isn't the most important but to compete with Windows Ubuntu also shoudl focus on aesthetic more.  Streamline thigns but don't over simplify and make sure that it still has the functionality that power users want.
Solely my opinion.

The spot where users select their account could become the spot where users scroll to select the OS to boot into.  The top of the bootloader could display various information that can be hidden if desired.

---

### Post by IWantFroyo on 2011-09-22
The bootloader is meant to be quick on old computers. If you want something prettier, you can install something like BURG.
Forcing this change on everyone would be inconsiderate, however.

And besides, GRUB does its job extraordinarily well. To make it beautiful, you might have to end up hiding some of its complex functions.

---

### Post by dniMretsaM on 2011-09-22
I would say leave it. GRUB (2) is an excellent, fast bootloader. It's not meant to be pretty, it's meant to work. Personally, I think that's more important. When real work needs to be done, give me a good ol' textual interface. They're faster and no nonsense. BUT, if something can look good and still be really functional, I'd probably pick that. There is a thread on here about improving the appearance of GRUB, I'll see if I can find it.

[EDIT]Found the thread. [Clicky](http://ubuntuforums.org/showthread.php?t=1810063)[/EDIT]

> **IWantFroyo said:**
> The bootloader is meant to be quick on old computers. If you want something prettier, you can install something like BURG.
Forcing this change on everyone would be inconsiderate, however.

And besides, GRUB does its job extraordinarily well. To make it beautiful, you might have to end up hiding some of its complex functions.

As far as I know, BURG is no longer under development. So installing it isn't recommended.

---

### Post by iponeverything on 2011-09-22
> **j814wong said:**
> After seeing the LightDM login screen, I began to think think that a similar UI style could be used as for a bootloader.  Windows 8 has a new bootoader and it looks much nicer then the old ones.  Yes I know that aesthetic isn't the most important but to compete with Windows Ubuntu also shoudl focus on aesthetic more.  Streamline thigns but don't over simplify and make sure that it still has the functionality that power users want.
Solely my opinion.

The spot where users select their account could become the spot where users scroll to select the OS to boot into.  The top of the bootloader could display various information that can be hidden if desired.

there is no competition, no shareholders to please, no forced upgrades or planed obsolescence -- 

your pretty new boot loader is nothing more than pink leg irons. 

What linux has going for over other operating systems is that is not propriety.

---

### Post by BrokenKingpin on 2011-09-23
You can add a background to the current GRUB can you not (I think Mint does this)? What else do you really need for a menu that shows for 3 seconds, if not less. I have some issues with GRUB2, but certainly not with the way it looks.

---

### Post by grahammechanical on 2011-09-23
This is a link to a utility called Grub Customizer. I recommend it.

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

You should be able to get some Grub splash images from the Ubuntu Software Centre. It is easy to place one in the right folder, Or use Grub Customizer to do it and you get a pretty picture underneath the menu. I have chosen the glasses image. And it does not clash with the working of Grub.

Note this quote

> if an image resides in /boot/grub it will be used

Regards.

---

### Post by aura7 on 2011-09-23
Try customizing grub using startup manager

---

### Post by Blasphemist on 2011-09-23
My opinion is that the boot loader is important for more than its functionality. It is the first thing people see when they turn on the computer, even if they run windows for that boot. Grub looks less professional than that of Apple which has nice buttons. The link above to the appearance improvement was an attempt but didn't work out. 

There doesn't seem to me to be any reason that any functionality need be lost in making it look better. Grub also is great for dual boot but less than ideal for multiboot. Burg and Lilo aren't being developed. Grub2 is also being adopted by those distros that have been still using grub legacy. It seems like to me that better handling of UEFI and GPT is first priority but appearance shouldn't be forgotten. It's pretty basic so maybe even someone like me will learn enough to contribute this, eventually.

---

### Post by srs5694 on 2011-09-23
Boot loader issues are about to change radically (and have already changed for some people), since the old BIOS style of booting is on the way out, to be replaced with the EFI/UEFI method. The underlying technical issues for the two boot systems are very different, and some of these impact -- or at least *should* impact -- boot loader design. In particular, in the BIOS system, one piece of on-disk code -- the first 440 bytes of the MBR -- ultimately controls the rest of the boot process. This makes it vulnerable to "MBR hijacking" (typically when another OS installs), and in a multi-boot environment, you can get a confusing chain of different OS selection menus.

Under EFI, by contrast, OS-specific boot loaders install themselves to the EFI System Partition (ESP), and as many can coexist there as you like. The EFI is supposed to present a boot menu of its own, although in most implementations, this menu is awkward to get to or confusing in one way or another. One of GRUB's big design goals is to boot as many OS kernels as possible (Linux, FreeBSD, GNU HURD, etc.), but the design of the EFI system makes smaller and more OS-specific boot loaders more sensible. I've seen some comments lately to the effect that the Linux kernel is evolving to create more direct ties to the EFI boot process, but I don't know the details of what this means. My suspicion is that there are plans to compile the kernel in a way that enables it to function as its own boot loader, but I'd like to emphasize that this is speculation based on passing comments I've read elsewhere.

A very graphical boot loader for EFI and UEFI already exists. It's called [rEFIt,](http://refit.sourceforge.net) and although it was designed for EFI-based Macs, it works on UEFI-based PCs, too. (It's got some glitches and limitations, but I've written some patches for that which I've submitted to rEFIt's author and plan to publicly release soon.) IMHO, the combination of rEFIt and ELILO is the best current UEFI boot loader solution for a multi-boot Linux-with-whatever UEFI system. ELILO provides the simple configuration and reliability that's most critical, while rEFIt provides a pretty front-end that many users want. The down side is that the scripts that most distributions, including Ubuntu, use to help handle things like kernel upgrades don't work with ELILO, so unless and until distributions embrace ELILO, some manual configuration will be required.

---

### Post by dava4444 on 2011-09-23
mmmmmm

I'd like a Pepsi to Apples 'Coke', there are projects out there that have made a start (open iboot) not intended for Ubuntu, but may be port-able.

purple background and drive selector.

if you want to put Ubuntu on an older comp thats cool too, a hw rating system could implimented.. that actually sounds smart.. hhhuhh? dunno.


but grub is oooougly.

---

### Post by el_koraco on 2011-09-23
> **srs5694 said:**
> My suspicion is that there are plans to compile the kernel in a way that enables it to function as its own boot loader, but I'd like to emphasize that this is speculation based on passing comments I've read elsewhere.

AFAIK, the idea is to have EFI boot a minimal generic kernel, which would then pass the job to the full kernel. Sounds more like a coreboot-like implementation than what we have today.

---

### Post by beew on 2011-09-23
> **j814wong said:**
> After seeing the LightDM login screen, I began to think think that a similar UI style could be used as for a bootloader.  Windows 8 has a new bootoader and it looks much nicer then the old ones.  Yes I know that aesthetic isn't the most important but to compete with Windows Ubuntu also shoudl focus on aesthetic more.  Streamline thigns but don't over simplify and make sure that it still has the functionality that power users want.
Solely my opinion.

The spot where users select their account could become the spot where users scroll to select the OS to boot into.  The top of the bootloader could display various information that can be hidden if desired.

I care a lot more about fast boot up time than what the boot screen looks like. In a fast boot (as in my current Ubuntu install) the boot screen would be there for only 10-15s, so who cares what it look like?

---

### Post by Blasphemist on 2011-09-23
> **srs5694 said:**
> Boot loader issues are about to change radically (and have already changed for some people), since the old BIOS style of booting is on the way out, to be replaced with the EFI/UEFI method. The underlying technical issues for the two boot systems are very different, and some of these impact -- or at least *should* impact -- boot loader design. In particular, in the BIOS system, one piece of on-disk code -- the first 440 bytes of the MBR -- ultimately controls the rest of the boot process. This makes it vulnerable to "MBR hijacking" (typically when another OS installs), and in a multi-boot environment, you can get a confusing chain of different OS selection menus.

Under EFI, by contrast, OS-specific boot loaders install themselves to the EFI System Partition (ESP), and as many can coexist there as you like. The EFI is supposed to present a boot menu of its own, although in most implementations, this menu is awkward to get to or confusing in one way or another. One of GRUB's big design goals is to boot as many OS kernels as possible (Linux, FreeBSD, GNU HURD, etc.), but the design of the EFI system makes smaller and more OS-specific boot loaders more sensible. I've seen some comments lately to the effect that the Linux kernel is evolving to create more direct ties to the EFI boot process, but I don't know the details of what this means. My suspicion is that there are plans to compile the kernel in a way that enables it to function as its own boot loader, but I'd like to emphasize that this is speculation based on passing comments I've read elsewhere.

A very graphical boot loader for EFI and UEFI already exists. It's called [rEFIt,](http://refit.sourceforge.net) and although it was designed for EFI-based Macs, it works on UEFI-based PCs, too. (It's got some glitches and limitations, but I've written some patches for that which I've submitted to rEFIt's author and plan to publicly release soon.) IMHO, the combination of rEFIt and ELILO is the best current UEFI boot loader solution for a multi-boot Linux-with-whatever UEFI system. ELILO provides the simple configuration and reliability that's most critical, while rEFIt provides a pretty front-end that many users want. The down side is that the scripts that most distributions, including Ubuntu, use to help handle things like kernel upgrades don't work with ELILO, so unless and until distributions embrace ELILO, some manual configuration will be required.
Thanks srs! If you were buying a new laptop today and you found 2 that were all things considered equal deals, and one had BIOS and one EFI, would you choose one over the other if you plan to run a bunch of distros? 

I don't expect to ever buy apple. If I get a Win 8 or an upgrade to it free with a laptop that is a better buy than I can get otherwise, so be it. But I do plan to run at least 5 or 6 distros at a time for the foreseeable future.

I saw some things on the rEFIt site that make me think an intel mac isn't a good candidate for linux given the X 3D and apple firmware issues. Would an intel or amd windows EFI based system have the same issue or is that apple firmware specific? 

I'll watch for anything I can learn about linux kernel futures. Hopefully MS won't get everyone locking the dang things down too much.

---

### Post by srs5694 on 2011-09-23
> **srs5694 said:**
> A very graphical boot loader for EFI and UEFI already exists. It's called [rEFIt,]("http://refit.sourceforge.net") and although it was designed for EFI-based Macs, it works on UEFI-based PCs, too. (It's got some glitches and limitations, but I've written some patches for that which I've submitted to rEFIt's author and plan to publicly release soon.)

FWIW, I've now posted my patched rEFIt [here.](http://www.rodsbooks.com/efi-bootloaders/refit.html) That page is part of [a new set of pages](http://www.rodsbooks.com/efi-bootloaders/index.html) I've created on the topic of managing EFI/UEFI boot loaders.

---

### Post by srs5694 on 2011-09-23
> **Blasphemist said:**
> Thanks srs! If you were buying a new laptop today and you found 2 that were all things considered equal deals, and one had BIOS and one EFI, would you choose one over the other if you plan to run a bunch of distros? 

From a Linux-only perspective, the following are relevant points:


[list]
[*]EFI is likely to boot slightly more quickly.
[*]Most distributions (including Ubuntu) have fair to poor EFI support. This affects installation and boot loader maintenance, not system operation once it's booted. Personally, I know my way around the pitfalls, so these don't bother me, but they trip up a lot of people, judging by posts here.
[*]Boot loader maintenance is, at least theoretically, easier with EFI than with BIOS. In a multi-Linux installation, though, this isn't likely to be a big deal, since you can manage them both in the same sorts of ways.
[*]In the future, there may be run-time advantages to EFI, but I don't know what specific things might materialize.
[*]EFI generally will be more future-proof, although that's less likely to be an issue in an all-Linux configuration than in a multi-boot configuration or if you think you might switch to another OS in the future.
[/list]


Since most or all modern UEFI-based PCs include a BIOS compatibility mode, the safest course is probably to get a UEFI-based system but use BIOS mode to install and use Linux, at least for the moment. This will result in the easiest installs for now and the greatest flexibility for the future.

> I saw some things on the rEFIt site that make me think an intel mac isn't a good candidate for linux given the X 3D and apple firmware issues. Would an intel or amd windows EFI based system have the same issue or is that apple firmware specific?

The number of systems with which I have experience is still limited, but my suspicion is that such issues are largely Apple-specific. Also, I think some of the information on the rEFIt site may be outdated. You can check the Apple sub-forum here to see what sorts of problems people are having.

---

### Post by 3rdalbum on 2011-09-24
Most problems with power management are due to buggy/hacky BIOS implementations, right?

With UEFI theoretically there shouldn't be those problems.

I also like what the old Macs used to do - you could literally drag and drop a System Folder onto a disk and then that disk would be bootable. You didn't need to "install a bootloader" or any of that jazz; as long as it had an operating system it was bootable. I'm guessing UEFI could be made to do something like that?

---

