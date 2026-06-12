---
title: "Converting a physical windows 7 partition to an image for VirtualBox"
date: 2010-06-01
forum: Virtualisation
---

### Post by jimmyrose on 2010-06-01
I've decided it's time to upgrade my laptop to Ubuntu. It's got windows 7 on it by default and a bunch of applications I need which aren't Linux compatible. So what I want to do is rip the existing win7 partition and convert it to an image that virtualbox will load.

I'm still relatively new at Linux so bear with me. 

They talk about windows migration [here]("http://www.virtualbox.org/wiki/Migrate_Windows") but specifically for XP.

From what I understand, I just use the dd command (on the ubuntu live CD?) to rip the partition (by itself, not the whole drive w/ recovery partition) into a dd file onto a USB external hard drive. I then use vboxmanage to convert it to a .vdi and it should be fairly sweet from there. If I run into BSOD I'll have to get a windows 7 CD for a repair since the laptop didn't come with one.

Luckily I'll be able to test the win7 rip on my main PC running ubuntu before wiping the laptop.

Do I have the process right?

Am I right in assuming if everything goes belly up, I can just restore the .dd from the external with the live CD again?

Cheers in advance

---

### Post by TheFu on 2010-06-01
a) Your laptop probably came with an OEM version of Windows. It will probably not run under a virtual machine since it will check with WMI whether the underlying hardware is from the laptop manufacturer. If it is not, it will refuse to install.
b) If you did get a "retail" version of Windows7, then you probably want to try a "p2v" conversion to run it inside VirtualBox. You'll get to "re-activate" your license with Microsoft. Always fun. VWware makes a free p2v converter that creates files compatible with VirtualBox. The image conversion works for Linux installs since they recognize hardware changes at boot. For MS-Windows, I have doubts it will be successful. Important drivers will definitely change between the physical and virtualbox environments.

I'd recommend you double check that the MS-Windows programs cannot be run under WINE. I was shocked to discover that WINE supports most of MS-Office 2003 and 2007 fairly well these days without having to do anything funny to get 90% of the usefulness.

You are correct that storing the drive contents with `dd` will accomplish a mirror, but perhaps you'd prefer using Clonezilla or with partimage? These won't copy unused areas and they will compress the data. I use partimage myself, but know folks that like Clonezilla more.  I use `dd` all the time to exactly mirror disks so I can swap them should a failure happen. That isn't your purpose and being more efficient in storing the resulting image files is just a good idea.  Also, store the files with 10% par2 checksums so any bit rot can be corrected later.

You didn't mention your exact host or your exact client. That may be useful for someone else to help. The conversion link that you've included appears like a good way to head, assuming you'll be able to get/create a recovery disk. Perhaps you have an old WinXP license that you can use instead?

---

