---
title: "Upgrade to new Hard Drive and Distro"
date: 2009-03-01
forum: System76 Support
---

### Post by eadwacer on 2009-03-01
I have a new Seagate 500GB HDD for my Ratel running 7.04 Feisty. I want to upgrade both the drive and the distro together, and I'd like to see if there's anything wrong with the following approach:

1. pull data cable from original 140MB HD
2. install unformatted 500GB
3. boot from live CD with 8.04
4. format drive, install 8.04
5. download System 76 drivers
6. download preferred software (Opera, Sunbird, Envy etc)
7. plug 140MB back in. (are there jumper issues here?)
8. move data files to new drive

This would seem to be a lot more efficient than going the 7.04->7.10->8.04 upgrade path, then moving my home directory, etc, to the new drive. I have a reasonably vanilla setup, so preserving strange settings isn't an issue.

I am asking here instead of the general forum, since I'm not sure if there are any Sys76 issues I need to be aware of, and nothing on the main forum addresses my exact problem. I am open to suggestions.

---

### Post by Lee_Machine on 2009-03-01
the days of master and slave jumpers are gone. Just plug your new HDs cable into the number 2 slot for SATA on your MB.

No need to pull the old one out. Just put in the new one in slot 2

There seems to be no issues. Why 8.04, and not 8.10? 

Go into BIOS and make sure your new HD is the first bootable device. I usually keep CD-ROM first and the first bootable HD 2nd.

When you boot into the new Distro go into Places and you will see your old HD click on it and it will be mounted. 

Have fun :P

Also one last note. Keep the old drive in so when you install the new OS GRUB will detect it and add it to your boot list.

---

### Post by eadwacer on 2009-03-01
Lee
Thanks. That was exactly what I needed. I'm new to SATA, and the Seagate has jumpers on the back. Turns out they are to limit the GB/s of transactions. I'm using 8.04, since that's the LTS version. 

Everything went smoothly, or, as smoothly as any of this does, until the installer choked on a bad file. Errormsg said it could be the CD (I think likely) or it could be a HD problem. My drive is a reconditioned one, sent me by them after the original one crashed (part of the Seagate HD fiasco of late last year). It formatted and partitioned OK, and it looks like the directory structure installed without trouble. I haven't tried to boot into the new version yet - just changed back to the old drive with F8 on startup.

Thanks again. It's this kind of community help that keeps the community going.

> **Lee_Machine said:**
> the days of master and slave jumpers are gone. Just plug your new HDs cable into the number 2 slot for SATA on your MB.
...
Also one last note. Keep the old drive in so when you install the new OS GRUB will detect it and add it to your boot list.

---

