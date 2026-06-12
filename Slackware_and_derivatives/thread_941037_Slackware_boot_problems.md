---
title: "Slackware boot problems"
date: 2008-10-07
forum: Slackware and derivatives
---

### Post by BSG75 on 2008-10-07
I just finished installing Slackware 12.1. Everything went fine until I boot up. I keep getting the error 
Kernel panic-not syncing: VFS: Unable to mount root fs on Unknown-block(253,0)
I have heard that similer problems are common, but I can't find a good soulution. Any ideas

---

### Post by disturbed1 on 2008-10-08
You'll get better support [Here]("http://www.linuxquestions.org/questions/slackware-installation-40/") <-click. Be sure to at the very least include a little bit of hardware information. Motherboard make and model, or the chipset and controller chipset.

The error means the kernel was unable to locate your root file system/unable to mount the partition. Most likely, if you're not booting with the huge-smp kernel, your intrid isn't correct. Or you have a BIOS issue, and may need to pass noapic. Or you have a hard drive controller that is support by lib ata, and need to pass hda=noprobe. 

Look for a bios update for your PC.

Also take a look at google. There's roughly 1,650 hits on your _exact_ issue :)

---

### Post by tommcd on 2008-10-09
> **disturbed1 said:**
>   Or you have a hard drive controller that is support by lib ata, and need to pass hda=noprobe. 


I think this may be the problem. See the Slackware 12.1 Changes And Hints.txt:
[http://slackware.oregonstate.edu/slackware-12.1/CHANGES_AND_HINTS.TXT](http://slackware.oregonstate.edu/slackware-12.1/CHANGES_AND_HINTS.TXT)
> If you notice extremely long wait times when formatting partitions in the 
  installer, and you're installing on a Thinkpad that has a SATA drive, it's
  possible that the wrong driver is being used, which disables DMA on the drive
  (and could happen on other machines). A bit more detail about it is here:
    [http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux#No_DMA_on_system_hard_disk](http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux#No_DMA_on_system_hard_disk)
  Try passing "hda=noprobe" to the kernel when booting the installer, and it
  should use the correct libata driver.


Is your hard drive sata or ide? You could try booting from a live CD, mount and chroot into your Slackware install, and changing your fstab entries from 'hda' to 'sda'. Change hda to sda in lilo.conf also, and append hda=noprobe to the kernel section; or put it in the global section. Then rerun lilo. Try booting with the huge-smp kernel first.  Then try and reboot into Slack. 

Or just try a reinstall with passing "hda=noprobe" to the kernel when booting the installer, as it says in Changes and Hints. This same thing happened to me when I installed Slack 12.1 on my laptop, and hda=noprobe fixed it.

---

