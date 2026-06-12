---
title: "Something like Boot Camp for Linux?"
date: 2009-06-06
forum: The Cafe
---

### Post by Ozor Mox on 2009-06-06
Does anyone else think this would be really good? How come Mac users get to install Windows nicely alongside their existing setups, whereas Linux users have to install Windows first otherwise it will trash everything that comes in its path! Yes I know Windows can be installed after, but it generally seems to be not recommended.

Also, Windows could be run with a VM instead of a dual boot, for everything except apps that need 3D acceleration, like games. Reading the [comparison of virtual machines](http://en.wikipedia.org/wiki/Comparison_of_platform_virtual_machines) on Wikipedia, I can't understand why VirtualBox and VMWare have either limited or experimental 3D hardware acceleration, but Parallels Desktop for Mac has it enabled. Even Parallels for Windows and Linux doesn't have it.

---

### Post by CharmyBee on 2009-06-06
Because Microsoft and playing nicely with other OSes is not written in history.

---

### Post by MaxIBoy on 2009-06-06
> **Ozor Mox said:**
> Does anyone else think this would be really good? How come Mac users get to install Windows nicely alongside their existing setups, whereas Linux users have to install Windows first otherwise it will trash everything that comes in its path! Yes I know Windows can be installed after, but it generally seems to be not recommended.Everyone here agrees with you. I think at least part of the issue is that Windows is not designed with dual-booting in mind, and might even have been designed to discourage dual-booting. I don't know, I don't work at Microsoft.

There is some software you can run under Windows to install Ubuntu (wubi.) 

In Linux, you can resize your partitions, install Windows, and then attempt to pick up the pieces afterwards when Windows messes up GRUB. A workaround for that would be pretty cool, although it may require modifying Windows, which is illegal. 

> Also, Windows could be run with a VM instead of a dual boot, for everything except apps that need 3D acceleration, like games.It's called a hypervisor (by analogy to 'supervisor.') [http://en.wikipedia.org/wiki/Hypervisor](http://en.wikipedia.org/wiki/Hypervisor). I could see a possibility to integrate Virtualbox with the boot-up process, giving you a simple menu when you start up.> Reading the [comparison of virtual machines]("http://en.wikipedia.org/wiki/Comparison_of_platform_virtual_machines") on Wikipedia, I can't understand why VirtualBox and VMWare have either limited or experimental 3D hardware acceleration, but Parallels Desktop for Mac has it enabled. Even Parallels for Windows and Linux doesn't have it.Parallels is an Apple product, so they want to encourage people to use OS X more.

---

### Post by mamamia88 on 2009-06-06
i don't quite understand what you are getting at. if linux is installed first just boot from live cd create an ntfs patition then boot off windows cd install windows the boot from linux cd again and restore grub.  i don't think thats too complicated.

---

### Post by DeadSuperHero on 2009-06-06
You know, GRUB has always served me well. It's not necessarily pretty, but it sure does a good job at detecting the OS'es on other partitions and hard drives.

---

### Post by schauerlich on 2009-06-07
> **MaxIBoy said:**
> Parallels is an Apple product, so they want to encourage people to use OS X more.

Parallels is made by Parallels, Inc. Apple did not develop it.

---

### Post by aysiu on 2009-06-07
I'm sure it could be done, but I don't think it makes sense from a sociological perspective.

See, Mac users primarily use Mac OS X, which comes preinstalled on Apple computers. So if they're going to also use Windows, Windows will almost always be the second OS installed. That makes Boot Camp necessary for Macs, since Microsoft doesn't like Windows to play nice with non-Microsoft OSes.

On the other hand, most Linux users are ex-Windows users. If they are trying out Linux in a dual-boot, they most likely either bought a computer with Windows preinstalled or built their own computer on which they installed Windows. In any case, Windows was there first, so Grub automatically adds Windows to the boot menu and everything's fine.

The situations in which one has Linux installed first and then wants to add Windows to the dual-boot later are few and far between. I suspect if this weren't the case, you'd definitely see something like Boot Camp for Linux appear on SourceForge.

---

### Post by Vostrocity on 2009-06-07
Seriously!? I never heard of this installing Windows first thing, so I wasn't planning on that. Now I won't be able to install Win7! :mad:

---

### Post by Sashin on 2009-06-07
You can install windows after, it'll just screw up your grub.

After you install windows 7, boot up with a live CD and reinstall grub and then BAMM! problem solved.

---

### Post by Vostrocity on 2009-06-07
So the Ubuntu disk let's you install GRUB by itsself without touching your Ubuntu installation?

---

### Post by Sashin on 2009-06-07
Yes, it does. I've done it before, although nowadays I just use VirtualBox to run windows XP and 7.

---

### Post by gn2 on 2009-06-07
> **Vostrocity said:**
> So the Ubuntu disk let's you install GRUB by itsself without touching your Ubuntu installation?

Yes, but you don't actually need to have grub installed at all.
You can use a SuperGrub CD or GAG CD.

Lots of info [here]("http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html") and [here]("http://members.iinet.net.au/~herman546/p12.html").

---

### Post by michaeldt on 2009-06-07
Personally, I just dual boot with two different hard drives. Of course that's not an option for most laptop users but it saves the hassle of Windows overwriting GRUB.

---

### Post by 3rdalbum on 2009-06-07
> **Ozor Mox said:**
> Does anyone else think this would be really good? How come Mac users get to install Windows nicely alongside their existing setups, whereas Linux users have to install Windows first otherwise it will trash everything that comes in its path!

Macintoshes do not use a BIOS, so the Windows installation process does not touch the Macintosh's boot sequence (it was possible to install Windows on a Macintosh before Boot Camp, you know).

---

### Post by Tipped OuT on 2009-06-07
> **3rdalbum said:**
> Macintoshes do not use a BIOS, so the Windows installation process does not touch the Macintosh's boot sequence (it was possible to install Windows on a Macintosh before Boot Camp, you know).

No BIOS!? That's crazy! :o

That's like a car with no engine!

---

### Post by Ozor Mox on 2009-06-07
I didn't know you could restore GRUB from the Ubuntu live CD, that could be very useful information for me!

I do know it is possible, pretty much anything has the potential to be possible with Linux. It's just so...messy! I want Windows to my secondary OS, not something I have to clean up after!

> **michaeldt said:**
> Personally, I just dual boot with two different hard drives. Of course that's not an option for most laptop users but it saves the hassle of Windows overwriting GRUB.

If you could tell me how you did that without disconnecting your primary hard drive I'd be very grateful. I would also love to know how you set up your GRUB to boot from the second hard drive. I'm a little worried about messing up my installation. It wouldn't be the end of the world, just a bit irritating.

---

### Post by mamamia88 on 2009-06-07
it's very easy just follow these instruscitions [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Dimitriid on 2009-06-07
> **Ozor Mox said:**
> 
If you could tell me how you did that without disconnecting your primary hard drive I'd be very grateful. I would also love to know how you set up your GRUB to boot from the second hard drive. I'm a little worried about messing up my installation. It wouldn't be the end of the world, just a bit irritating.

If your laptop is at least somehow recent I'm reasonably certain it would be able to boot to USB? Then you could use an external hdd. More uncommon ( but faster ) would be external SATA.

If speed is a concern you can always book to a USB and use Puppylinux and run entirely from RAM.

---

### Post by .Maleficus. on 2009-06-07
> **Tipped OuT said:**
> No BIOS!? That's crazy! :o

That's like a car with no engine!
Macs use what's called EFI - Extensible Firmware Interface.  It was made by Intel as a BIOS replacement, and in 2006, the Intel Macs shipped with it.

[http://en.wikipedia.org/wiki/Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Extensible_Firmware_Interface)

---

### Post by init1 on 2009-06-07
> **Mr. Psychopath said:**
> You know, GRUB has always served me well. It's not necessarily pretty, but it sure does a good job at detecting the OS'es on other partitions and hard drives.
It can be very pretty if its configured. OpenSuse has a very nice GRUB theme.

---

### Post by MaxIBoy on 2009-06-07
> **Tipped OuT said:**
> No BIOS!? That's crazy! :o

That's like a car with no engine!More like a car without any keys-- some cars have push-button starters, you know.

Also, more and more non-Mac motherboards are also using EFIs instead of BIOSen. I don't know whether that's a good thing, it depends on whether something like Coreboot would also be possible on EFI.

---

### Post by MikeTheC on 2009-06-07
Well, by shipping motherboards using EFI and not BIOS, it sure does tend to imply a forced-upgrade future, doesn't it? :shock:

Of course, Linux supports EFI and has done for quite some time, so no issues here.

Regarding the comment about Apple and a lack of BIOS, the only systems Apple has shipped that probably came with a BIOS are the early Intel developer's boxen that Apple shipped out for about a year when they announced they were going x86.

Macs have NEVER otherwise used BIOS. Back in the PPC days we had a Apple-unique technology. There ultimately were a number of iterations of it, but the two biggest classifications of it are the "OldWorldROM" and "NewWorldROM" Macs. The principle differences between them (as far as this discussion is concerned) were what Apple allowed to initially boot the system. On OldWorldROM systems, the *only* OS that could boot a given unit was an Apple-shipped OS. Period.

The way you could sort of "get around" this was to put a partition on the front end of the HDD which had some version of Mac OS Classic and the BootX control panel/extension combination, which would then halt the boot process, strip what was loaded out of RAM, insert the desired Linux RAMdisk + Kernel into RAM, establish the basics of where to start to boot up from, and then let 'er rip. In fact, I still have a PowerMac G3 Desktop sitting right here next to me (at present not connected to anything) which is set up in this way with Debian Etch.

With NewWorldROM Macs, you could boot with anything you wanted that simply supported the architecture. The so-called "Blue-and-White" G3 Towers, iMacs, iBooks, Titanium PowerBooks and all newer systems are NewWorldROM systems.

Then, of course, as already discussed, are the Intel-based Macs.

The other thing is that Mac OS X doesn't support MBR for booting purposes. The hardware will, but if you want to boot Mac OS X on an Intel-based Mac, you have to use GUID partitioning. That's the reason for BootCamp, principally, since naturally Windows XP/Vista/7 do not support GUID, but only MBR.

This whole thing is a complete and total royal pain in the a** if you ask me. But hey, that's how it is.

---

