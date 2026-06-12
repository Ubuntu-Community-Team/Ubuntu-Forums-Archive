---
title: "Security of virtualized guest Ubuntu with Windows 10 host vs dual boot?"
date: 2020-01-23
forum: Virtualisation
---

### Post by AbleTassie on 2020-01-23
Hello all,

I have been using Linux and Ubuntu for several years and I have: **(1)** used Virtualbox with Windows XP as the guest and Ubuntu as the host and **(2)** I have also dual booted Ubuntu and Windows. I am considering running Windows 10 as the host with Ubuntu as the guest in Virtualbox and doing most of my contact with the internet through virtualized Ubuntu, rather than dual booting Windows 10 and Ubuntu. (The dual boot installation is more complicated now that UEFI has replaced BIOS on the newer PCs.)

But, I am wondering about the security of virtualized guest Ubuntu with Windows 10 as the host vs dual booting between Windows 10 and Ubuntu. 

QUESTION: Does anybody have any comments about the relative security of virtualizing Ubuntu like this, versus dual booting? 

I don't think that virtualizing Windows as the guest with Ubuntu as the host is an option anymore,  because I think the Windows 10 OS came pre-installed on the hard drive (my nephew, who is an IT guy, handled the early details of the PC). Any other comments will be appreciated.

Thanks,

A.

---

### Post by TheFu on 2020-01-23
If you lose the beachhead, then you lose the war.
Translation:  If Windows gets hacked, then all VMs are hacked too.
So the question becomes, do you trust MSFT to provide a stable, secure, platform?  

Just a few weeks ago, you could have downloaded a free Win10 license from Microsoft. Did that change?

Have you read the conditions in the EULA?  Can you accept those terms? There's a bunch of stuff in there that destroys data privacy.

"IT Guys" are busy, so how great is your nephew at Linux, BSD, Solaris, HP-UX, AIX? Sometimes they don't have or take the time to learn other OSes.

---

### Post by bunny9000 on 2020-01-25
Humm.

It depends. I forget exactly how the Windows 10 reactivation works. I guess if win 10 was pre-installed then backing it up using macrium reflect and loading into a virtual machine might really confuse it may reactivate. I think it's normally tied to your motherboard.

Anyway - switching to Linux as the host (preferable) and windows as the virtual guest would be safest as most viruses won't jump from windows to Linux so you could stuff up your windows OS and keep doing stuff in your Linux and if you were to keep regular snapshots you'd mostly be able to take the machine back to before it got broken or reload an image.

Whereas with Windows as the host and linux as your guest then you're only as safe as you choose to be using Windows. However, if you use the Linux VM to go to iffy sites then it won't get infected by a windows virus. Keep windows file sharing turned off in the Linux VM too and make sure you have the linux firewall turned on.

The only real advantage to dual boot is if you wanted the full on metal capabilities of the Linux OS on your machine. But this is only a good use case if you're editing video or trying to Linux game. Also, since Linux uses the EXT file system that by default windows can't 'see' or read / write from any data in the EXT partition may be safer. Linux can read and write to Windows NTFS and FAT32 filesystems by default. So, if you have Linux virtualized in Windows and a virus scrambles all your files, it will scramble the virtual machine disk image file and thus you lose your Windows data and Linux data.

If you dual boot though and you install the Linux boot loader to the same location as your Windows boot loader you may accidentally overwrite the windows one so when you come to remove Linux you may have to use a free recovery tool to rebuild your windows boot loader to be able to boot back into windows.

My conclusion would be to keep backups of your important data and keep those backups either in the cloud or locally off your daily machine.

The safest thing would probably be just to image your windows OS, store that image somewhere safe and install Linux over the top :lolflag:. But don't be too complacent. Linux can get viruses too. There is just less of them in the wild and a lot of false sense of security in the Linux community.

---

### Post by AbleTassie on 2020-03-16
I think you guys pretty much answered this, so I will mark as SOLVED.

Thanks Fu and bunny,

A.

---

