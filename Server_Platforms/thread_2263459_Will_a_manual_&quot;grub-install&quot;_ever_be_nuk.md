---
title: "Will a manual &quot;grub-install&quot; ever be nuked by an `apt-get upgrade'?"
date: 2015-02-01
forum: Server Platforms
---

### Post by DiagonalArg on 2015-02-01
Hi all - 


I'd like to do a grub-install to a USB, with the first partition used for the /grub directory.  That directory will include a grub.cfg that presents a menu with options to chainload a core.img _file_ from one of the following partitions.  Those following partitions (2,3,4...) will contain the /boot directory for ubuntus running on various machines.  So, when I want to boot my laptop, I will plug in the USB, startup, select the menu entry for the laptop(*), that will call the core.img file in the laptop's /boot/grub directory (eg., partition 2), which will perhaps present a second menu based on that directory's grub.cfg, and then I should be off and running.

For this to work, I need to understand something about regular ubuntu updates.  In particular, does 'apt-get upgrade' ever update grub's core.img?  If so, can I keep it from installing that new core.img to the sectors after the MBR, which would nuke the grub that I have installed by hand?

Thanks (and if this is the wrong forum, please let me know which one I should move to),
/DA


------------
(*) In case you're worried, ubuntu's grub has an "hwmatch" function that can make the choice idiot-proof.  See next-to-last post: [http://ubuntuforums.org/showthread.php?t=2256471&page=2](http://ubuntuforums.org/showthread.php?t=2256471&page=2).  This might also be done using the UUID's of the various hard drives located on the machines to be booted, if these UUID's are visible (ie if this is not a cryptsetup disk with no luks header).

---

### Post by oldfred on 2015-02-01
You do not have to have the /boot folders on the flash drive. Just directly boot Ubuntu from your grub menu. And then skip core.img unless you want to load the grub menu of each install every time.

Debian based installs put a link to the most current kernel in /, so you can boot using link and always boot the most current update.

 menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}
menuentry "Boot from USB Drive" {
    set root=UUID=XXXX-YYYY
    linux /vmlinuz root=UUID=XXXX-YYYY ro quiet splash
    initrd /initrd.img
}

If you leave the /boot folder in each install:

 menuentry "debian grub2 on /dev/sda1" {
insmod ext2 
insmod multiboot
set root="(hd0,msdos1)"
multiboot /boot/grub/core.img
}

I also add an entry to boot an MBR in one of my drives, but drive order can be tricky, boot drive is always hd0 and my system rest of drives are in SATA port order (sda in example is hd1:

 menuentry "Ubuntu on sdb (from sdc) Chainboot" {
set root=(hd2)
chainloader +1
}

I also like to add a spacer between a few lines and a way to reboot.

 menuentry " " {
set root= 
}

       menuentry "Restart" {
        insmod reboot
        reboot
    }

           menuentry "Shutdown" {
        insmod halt
        halt
    }

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by DiagonalArg on 2015-02-01
Oldfred - please, you and I have already discussed this at the link in the footnote, and I have spent a fair bit of time on the grub forum.  I know what I want to do here, and this is the correct way to do it.  Answering the question by telling me to do something else is not the answer to the question.  Thank you.

---

### Post by oldfred on 2015-02-01
If you un-check all the install options with the dpkg-reconfigure command, so the the install devices list shows no drive/partition for reinstall, your core.img will not be overwritten.

[http://askubuntu.com/questions/458572/how-do-i-prevent-one-of-my-partitions-messing-with-lubuntu-grub-entries/458582#458582](http://askubuntu.com/questions/458572/how-do-i-prevent-one-of-my-partitions-messing-with-lubuntu-grub-entries/458582#458582)
[http://askubuntu.com/questions/503417/how-to-prevent-ubuntu-from-overwriting-grub-bootloader-after-update/503446#503446](http://askubuntu.com/questions/503417/how-to-prevent-ubuntu-from-overwriting-grub-bootloader-after-update/503446#503446)
#To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by DiagonalArg on 2015-02-01
OldFred - that's helpful. 

 **As shown in the first two links:**

```
debconf-show grub-pc | grep "grub-pc/install_devices"
```
shows which device was given to grub-install during installation, and that device will be used for updates.  To change/remove that device as a grub-install target, we can use:

```
dpkg-reconfigure grub-pc
```
**One thing is still not clear:** As you gather, I need the modules in /boot/grub and the core.img & grub.cfg files in that directory to be properly upgraded on `apt-get upgrade'.  I just want to avoid installation of that core.img to the sectors after the MBR. Now, as show in your 3rd link, dpkg-reconfigure will respond with:

> The grub-pc package is being upgraded.  This menu allows you to select which devices you'd like grub-install to be automatically run for, if any.
Checking the man page for 'grub-install', I see that it is responsible for *both* copying the grub images to /boot/grub, and for installing the core.img to the boot-sectors of the device.  I need to leave on the first part, but turn off the second.  So this seems a problem (?)  On the other hand, dpkg-reconfigure continues with:

> Running grub-install automatically is recommended in most situations, to prevent the installed GRUB core image from getting out of sync with GRUB modules of grub.cfg.
So it looks like grub.cfg and the modules (and core.img?) will be updated, regardless.  I'm just not clear if they will be copied to /boot/grub.

Thoughts?
/DA

---

### Post by oldfred on 2015-02-01
One or two users that I know posted back after using those commands did find that the MBR was not written by a second install of Ubuntu. And I believe that the part of grub in /boot was updated. Without testing I cannot be sure, but core.img in sectors after MBR has to match MBR as far as I know. 
You may just need to test to see for sure.

---

