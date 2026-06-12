---
title: "update grub2 without hardware access"
date: 2012-06-21
forum: Server Platforms
---

### Post by awry on 2012-06-21
Does anyone know of a convenient way to update grub2's menu, while skipping the hardware probes? 

I am scripting the creation of various disk images. I mount an image, make some changes to it via chroot, then pack it up into a new image. I need to alter the kernel cmdline parameters for some of these images.

The supported method for changing the kernel command line is to change the value of GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub, and then run update-grub. This method does not work via chroot, where the device nodes of the running system might not match the devices expected by the chrooted grub, resulting in 'grub-probe: error: cannot find a device for /.

My current hack has been to unleash sed on /boot/grub/grub.cfg (anathema, I know). This succeeds in making my images bootable, but regresses badly with a run of update-grub from the newly-booted image.

This was a non-issue with grub-legacy, and feels like a case of some developer trying to protect me from myself. There is simply no good reason that I should be prevented from updating my kernel cmdline, just because grub can't figure out my hardware configuration at this moment.

Is this debian-specific, or does it come from upstream?

---

### Post by oldfred on 2012-06-21
How to: Create a Customized GRUB2 Screen that is Maintenance Free.
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

Link with several of links below:
How to edit bootloader? Feb 2011
[http://ubuntuforums.org/showthread.php?t=1694681](http://ubuntuforums.org/showthread.php?t=1694681)

I turn off os-prober and only let Ubuntu update new kernels. I have all my custom entries in 40_custom but that requires a sudo update-grub.
But you can use the configure file to link to a file to use to boot and only edit the file. I now use that for all my ISOs which I can then update without a sudo update-grub.

My entry in 40_custom. hd2,4 is drive & partition where folder /iso is.
```
menuentry 'Live ISOs' {
configfile (hd2,4)/iso/livecdimage.cfg
} 

```

then I just have a text file in drive hd2,4 with entries like this. I also added a reminder when I reinstall to make sure I have the 40_custom entry.

```

# livecdimage.cfg
# Add this to 40_custom to load this file:
# menuentry 'Live ISOs' {
# configfile (hd2,4)/iso/livecdimage.cfg
# } 

menuentry "Uubuntu 12.10 Quantal ISO 64bit" {

    set isofile="/iso/quantal-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

```

---

### Post by awry on 2012-06-22
Thanks, but that doesn't quite meet my requirements.

> **oldfred said:**
> I turn off os-prober and only let Ubuntu update new kernels.

By that I suppose you mean that you edit /etc/default/grub and set GRUB_DISABLE_OS_PROBER=true. It's the first thing I did.

This setting only affects whether grub looks for additional operating systems on your computer (e.g. Windows, Mac OS, etc.) to add to the boot menu. update-grub will still try to inspect your disks to find out what device / is on, resulting in '/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).'

I did find that if I bind mount /dev from the running system into the chroot, update-grub will run, but produces an erroneous grub.cfg with references to the device where the image is mounted on the running system, instead of references to the root device for the image. :-(

> **oldfred said:**
> 
My entry in 40_custom. hd2,4 is drive & partition where folder /iso is.
```
menuentry 'Live ISOs' {
configfile (hd2,4)/iso/livecdimage.cfg
} 

```

then I just have a text file in drive hd2,4 with entries like this. I also added a reminder when I reinstall to make sure I have the 40_custom entry.

```

# livecdimage.cfg
# Add this to 40_custom to load this file:
# menuentry 'Live ISOs' {
# configfile (hd2,4)/iso/livecdimage.cfg
# } 

menuentry "Uubuntu 12.10 Quantal ISO 64bit" {

    set isofile="/iso/quantal-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

```

This is helpful information (didn't know that was possible), but it doesn't completely solve my problem (or qualify as convenient).

First, adding a new file in /etc/grub.d is a non-starter, because I can't run update-grub.

Moreover, I don't want to add new entries; I need to edit existing ones. Simply adding the new entries is not enough, when the existing ones are broken. 

At minimum, this would require adding a new entry as you describe, and manually editing grub.cfg to change the default menu selection.
Then I would still need a way to *remove* the existing (non-booting) entries from the menu. 

All of which brings me right back to my current hack, unleashing sed on grub.cfg. Which I find ironic, since the whole point of the new grub2 configuration system was supposedly to remove the need for directly hacking on grub.cfg.

---

### Post by oldfred on 2012-06-22
What you want to do is an exception. For most not editing grub.cfg prevents the old issue of editing menu.lst and corrupting it so you could not boot.

I do not know why you cannot turn off all the scripts and just manually edit grub.cfg if you prefer.

I also directly boot ISO and add entires to my installs of ISO in my flash drives. For that I just install grub to the flash drive and manually add grub.cfg. Since there is no Ubuntu there is no automatic updates of grub.cfg. I can only manually edit grub.cfg for changes.

Herman has lots of useful info on grub only partitions or directly booting with grub or grub2.
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition)
Grub2
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_)
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries)

---

