---
title: "About Wubi"
date: 2011-10-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-10-16
Have you guys been using Wubi, during Natty and Oneiric cycles?
I don't have experience with this software as I don't dual boot.

So far, after days talking to many users, it seems to be the main culprit for broken grubs. 

I'd like to know to which extent this is newbies fault or if the software actually is that bugged in your opinion.

For an example: I talked to a guy that was burning a DVD and playing games while Wubi was running, according to him. But most others swear they didn't do anything risky.

At any rate, I think we should try to test it as much as possible, during PP Alpha/Beta.

Thanks,
Effenberg

---

### Post by dino99 on 2011-10-16
As i understand this app: it has been a good project for students learning and improving coding skills, but that said, to me wubi is a non sense project and push a very bad opinion to new comers about what ubuntu (linux) quality is. Better and stable alternatives exist like vmware/virtualbox. Myself have spent lot of time to tell new comers to make a real install to get a real ubuntu experience, and show them how to do.

---

### Post by philinux on 2011-10-16
The main problem was grub getting updated. Which is not needed at all. 

When it does it overwrites the mbr. Result borked. 

To my mind wubi should pin grub version to prevent this. I think there is a bug report.

---

### Post by jerrylamos on 2011-10-16
On "unstable" "new development" all the way through up to release you can expect Ubuntu to "bork" grub unexpectadly.  I just had oneiric ocelot release level image install screw grub on an IBM Thinkpad T40.  Install got an "error" on "configuring apt" by which time "install" had overwritten grub but not put a usable image on it.  Launchpad bug. I don't expect Ubuntu development to be interested. 

If "install" fails it should at least put grub back where it was. Best case would be to leave grub totally alone until "install" is successful.  Next best would be to totally update Grub before proceeding with the install.  Install's "Ubiquity" is proverbially buggy.  

I had to use a Lucid Lynx LTS CD Live image and do grub recovery as in Ubuntu wiki community support.  It's a multiboot and all the other images were intact after grub was fixed.

I use the T40 circa 2005 to look for ubuntu bugs.  It's supposed to be able to boot from USB however USB support is marginal at best on it.

What I'm doing here is running on this $250 Acer Aspire 1 netbook.  (Local Wall Mart had a black model for $200.)  It's running precise pangolin on a USB hard drive.  It's a left over 2.5" hard drive in a $20 USB case.  Nice and quick and responsive.  You'd never guess it wasn't running the main hard drive.  If the USB hard drive is plugged in, bios is set to boot it, which is precise pangolin at the moment.  It's dual booted so there is a oneiric ocelot also on the USB.

On trying "install" on a "development image" I specify the USB hard drive as target for grub so hopefully the main hard drive is left alone. 

The 250 GB main hard drive has Windozzzzz... 7, natty narwhal, meerkat, and archive of data on it.

Good luck.  

Jerry

---

### Post by cariboo on 2011-10-16
@jerrylamos, when you create bug reports, could you post the bug numbers here, so we don't have to try to find them. You can use [noparse][lpbug] <bug-number>[/lpbug][/noparse] without having to create a link yourself.

---

### Post by ventrical on 2011-10-16
> **effenberg0x0 said:**
> Have you guys been using Wubi, during Natty and Oneiric cycles?
I don't have experience with this software as I don't dual boot.

So far, after days talking to many users, it seems to be the main culprit for broken grubs. 

I'd like to know to which extent this is newbies fault or if the software actually is that bugged in your opinion.

For an example: I talked to a guy that was burning a DVD and playing games while Wubi was running, according to him. But most others swear they didn't do anything risky.

At any rate, I think we should try to test it as much as possible, during PP Alpha/Beta.

Thanks,
Effenberg


 I used it as an experiment during Maveric testing on my Dell Opti and I didn't have any probs with it. It was just a little bit slower than usual.

---

### Post by kansasnoob on 2011-10-17
> **philinux said:**
> The main problem was grub getting updated. Which is not needed at all. 

When it does it overwrites the mbr. Result borked. 

To my mind wubi should pin grub version to prevent this. I think there is a bug report.

AFAIK that bug is now fixed. Forum member bcbc worked with Colin Watson for a long time on that bug :)

For confirmation regarding that a query at the Wubi Megathread will typically get some attention from bcbc:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by kansasnoob on 2011-10-17
I typically don't use Wubi due to this:

> Any gotcha?

Hibernation is not supported under Wubi, moreover Wubi filesystem is **more vulnerable to hard-reboots (turning off the power) and power outages** than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.


[http://wubi.sourceforge.net/faq.php](http://wubi.sourceforge.net/faq.php)

I live in a rural area where power outages are incredibly common :(

But I do iso-test the "Wubi offered if 4 NTFS/FAT primary partitions exist" feature of the live installer (ubiquity) just to be sure it works.

But quite often (maybe almost always) Wubi installs are not supported during a dev cycle until we reach the first Beta, or at least that has been the case previously ;)

I'm in hopes that the Lubuntu and Wubi devs will collaborate during Precise development so Lubuntu can be installed using Wubi. I find Wubi to be a great way to try out Ubuntu for a few weeks (or months) so a Win user can figure out if they like Ubuntu well enough to consider a true dual/multi-boot, or possibly even replacing Windows :D

---

