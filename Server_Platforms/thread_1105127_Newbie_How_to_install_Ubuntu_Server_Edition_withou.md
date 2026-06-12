---
title: "Newbie: How to install Ubuntu Server Edition without a CD drive?!"
date: 2009-03-24
forum: Server Platforms
---

### Post by frammy7 on 2009-03-24
Hi all.
I'm a bit of a newbie to Linux and Ubuntu really, but I want to install a copy of Ubuntu Server Edition (possibly version 6.06/6.10, rather than 8.10, as I only have 128MB of RAM and 512MB storage to play with), but on a system which has _no CD drive_ - it can only boot from a USB drive or via the network.

Is there a simple way to put Ubuntu Server Edition on it??

I have tried downloading a Server Edition .iso file (ubuntu-6.06.2-server-i386.iso), and putting that on a USB stick with UNetbootin - but when I run it, it still moans about not being able to find the CD drive... I have also tried the 'alternative install' CD .iso... again with no luck...

I can install 'standard' Ubuntu using the '6.10_NetInstall' version, and that works 100% - but is there an equivalent simple way for the Server Edition??? (as I don't really understand what PXE, GRUB, etc is!)...

Any help would be amazing!
Thanks!

---

### Post by BkkBonanza on 2009-03-24
If you put the usb stick in and it still says it's looking for a cd drive then most likely you need to go into the BIOS and tell it to boot from usb not cd. Often they have a list of devices and you need to move the chosen one to the top of the list. And if that machine doesn't seem to have usb boot support (many older ones don't) then you can't boot from usb. I installed Fedora once from network but it was real messy and I don't know if Unbuntu has such an option.

---

### Post by frammy7 on 2009-03-24
> **BkkBonaza said:**
> If you put the usb stick in and it still says it's looking for a cd drive then most likely you need to go into the BIOS and tell it to boot from usb not cd. Often they have a list of devices and you need to move the chosen one to the top of the list.

Hi BkkBonaza.
Thanks for your reply - I think the boot order is ok, as what I meant was that it starts to boot from the USB stick, and goes through the 1st parts of the Ubuntu setup procedure fine - then it looks for the CD drive to continue the installation... which doesn't exist... (and there doesn't seem to be an option to tell it to look somewhere else - it just says its failed to find one and cancels the install)...
So I'm stuck unless I can convince it to install from somewhere else other than a CD...

---

### Post by lifi on 2009-03-24
I had this problem too. After hours trying around, i decided to download the "ubuntu-8.04.2-desktop-i386.iso", install it with unetbootin on usb-stick and it worked... yea well, you have to install the server-things (e.g. apache, php,...) by hand. Though it doesnt take much time.

---

### Post by frammy7 on 2009-03-24
> **lifi said:**
> I had this problem too. After hours trying around, i decided to download the "ubuntu-8.04.2-desktop-i386.iso", install it with unetbootin on usb-stick and it worked... yea well, you have to install the server-things (e.g. apache, php,...) by hand. Though it doesnt take much time.

That could work! Although as disk space is an issue, I would rather install *just* the Server Edition stuff, rather than both - but if no-one else has any ideas...?! I think something along those lines may have to do - Its annoying though, as I love the rest of Ubuntu - how hard is it to have a net-install version for the Server Edition?!

---

### Post by BkkBonanza on 2009-03-26
Another way is to take the hard disk out and put it in another machine briefly to get the install from cd done. Then put it back. Or some variation on that.

If you do use the desktop version then it's not so bad. You can easily remove X-windows and desktop stuff after and install the server packages. You won't really end up with both. Just more work.

---

### Post by allenreed on 2009-03-26
I know this is besides the point but I'm going to say it any way. I downloaded the ISO image and burned it to a CD but i cant even get it to boot the CD. When i restart my comp and i tried the CD in another computer it worked but it doesn't work on my server and I want to see if any one else has any idea's!

---

### Post by mrsteveman1 on 2009-03-26
Actually what you have to do is drop down to a commandline once the installer boots and insert the kernel module for the vfat filesystem, then mount the stick where the installer expects to find the CD. Unfortunately i don't have a system to test it on or vmware on this machine or i would check it right now. Someone else may remember where it expects to see the cd mounted, maybe /cdrom/ ?

I seem to remember that 6.06 and some other versions didn't even have the vfat module making it impossible to read the stick, but that may have changed.

---

### Post by primaxx on 2009-03-26
> **allenreed said:**
> I know this is besides the point but I'm going to say it any way. I downloaded the ISO image and burned it to a CD but i cant even get it to boot the CD. When i restart my comp and i tried the CD in another computer it worked but it doesn't work on my server and I want to see if any one else has any idea's!

Have you checked the BIOS on your server? (Just to make sure it is configured to boot from cd before hdd...)

---

### Post by frammy7 on 2009-03-27
> **BkkBonaza said:**
> Another way is to take the hard disk out and put it in another machine briefly to get the install from cd done. Then put it back. Or some variation on that.

If you do use the desktop version then it's not so bad. You can easily remove X-windows and desktop stuff after and install the server packages. You won't really end up with both. Just more work.

Taking the drive out would be difficult as its all solid state... I think some variation of installing the desktop then adding/removing the server apps and desktop may work though - so I will give it a try... thanks!


> Actually what you have to do is drop down to a commandline once the installer boots and insert the kernel module for the vfat filesystem, then mount the stick where the installer expects to find the CD.

for me... that just sounds like I'm going to break it, lol - but I have found a few how-to's so I can give it a go...

... I just wanted a NetInstall version of the Server Ed. - how hard would it be for Ubuntu to create one??

---

### Post by falconed7 on 2009-03-27
This should help you.

[https://help.ubuntu.com/community/UbuntuServerFlashDriveInstaller](https://help.ubuntu.com/community/UbuntuServerFlashDriveInstaller)

---

### Post by frammy7 on 2009-03-27
> **falconed7 said:**
> This should help you.

[https://help.ubuntu.com/community/UbuntuServerFlashDriveInstaller](https://help.ubuntu.com/community/UbuntuServerFlashDriveInstaller)

:o now how come I didn't find this page?! lol. THANK YOU! - crossing my fingers it will work :)

---

### Post by mrsteveman1 on 2009-03-27
From what i see on that page it appears there is still not a vfat module in the initrd on the server install disk for some reason (which is why you need to download another vmlinuz and initrd file), so what i suggested will not work unfortunately. 

If you follow those directions however it SHOULD work :)

---

### Post by Bachstelze on 2009-03-27
This always worked for me (I use it to install on my EeePC):

> cat /etc/mtab to find out my usb was at /dev/sdb1, mounted as /media/Flashdisk:

    * syslinux -s /dev/sdb1
    * mount -o loop /home/stilus/Desktop/mini.iso /media/cdrom0/
    * cp -r /media/cdrom0/* /media/Flashdisk
    * cd /media/Flashdisk
    * mv isolinux.cfg syslinux.cfg
    * cd /
    * umount /media/Flashdisk 

Plugged this Flashdisk in my to-be-installed system, and that was that: let the netinstall begin!! -- stilus 

(From [https://help.ubuntu.com/community/Installation/FromUSBStick#Comments%20and%20Troubleshooting](https://help.ubuntu.com/community/Installation/FromUSBStick#Comments%20and%20Troubleshooting))

The minimal ISO can be downloaded from the archive mirrors, for example here:
[http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/mini.iso)

(You might want to browse through the archive if you want a different version/architecture, the naming scheme is always the same.)

---

### Post by frammy7 on 2009-04-01
Thanks for all the ideas! I haven't had a chance to try them out yet, as work has been rather hectic - but it sounds like there is a solution there for me - so I will give them a go soon!

Thanks again for all the help!

---

