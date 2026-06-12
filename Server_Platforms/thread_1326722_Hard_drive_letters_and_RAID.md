---
title: "Hard drive letters and RAID"
date: 2009-11-14
forum: Server Platforms
---

### Post by atuls on 2009-11-14
Hi all,

First of all, I'm kind new to ubuntu, so please forgive me if I ask some obvious questions.

Well, this is related to my file server with ubuntu 8.04 LTS. I'm using some old hardwares so there are only two SATA connectors. To expand the capability, I installed a Rosewill RC 207 SATA to PCIE adapter with 2 SATA ports.

I had my system installed on raid1 with 2 80GB disks connected to IDE. Their letters are sda and sdb. Yesterday, I was getting some new hard drives in to the system. Two were connected to the onborad SATA ports, which worked fine and assigned to sdc and sdd. The third storage disk was then connected to the SATA adapter, which nicely supports hot plug. Everything is fine until I reboot the system, when the third storage disk was reassigned to sda instead of originally sde. As a results, it affects system booting process. I could disconnect the disk, then hot plug it after system boots, but it will take some time to recover the 3-disk raid 5. I really hope that I can just assign that last disk to sde to save some trouble.

I've searched a little bit, but I was not able to find a resolution. I hope someone can point me in the right direction. Please let me know what you think, and feel free to ask me to provide addition info.

Thank you all in advance for the helps

Chris

---

### Post by Vegan on 2009-11-14
This is not unique to Linux. I suggest not using a mix of ATA and SATA disks.

This is due the BIOS not the OS.

---

### Post by fjgaude on 2009-11-14
You will need to use the UUID of the third drive so it will not effect the raid1 pair.

Find the UUID of the drives using terminal after you have booted with just the first two drives:

sudo ```
blkid
```

Gets all the drives UUIDs.

Or use this for just the /dev/sdc

```
vol_id --uuid /dev/sdc
```

Then use that UUID for what is now /dev/sdc in your /etc/fstab file. I assume sdc is formatted already?

---

### Post by fjgaude on 2009-11-14
I forgot, the commands have to have "sudo" in front of them.

```
sudo blkid
```

Can't seem to edit posts in the forums anymore.

---

