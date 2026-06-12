---
title: "RAID on supermicro"
date: 2010-04-29
forum: Server Platforms
---

### Post by maudigan on 2010-04-29
I'm have a Supermicro 6016T-MT barebone server. I'm running 4 250gig sata drives. I've never set raid up before, and I was having problems. To give you an idea of what the server has the manual had this to say about the raid controller:

> Serial ATA
An on-chip (ICH10R) SATA controller is integrated into the X8DTL-i to provide a
six-port, 3 Gb/sec SATA subsystem, which is RAID 0, 1, 5 and 10 supported. The
SATA drives are hot-swappable units.

I ran the BIOS, selected adaptec raid controller bios (it was between intel and adaptec). I ran that utility and made a raid 10 setup for the 4 drives.

I ran the ubuntu server edition 9.10 installer
During the install I get the following prompt:

```
One or more drives containing Serial ATA RAID configurations have been found. Would you like to activate these RAID devices.

Activate Serial ATA raid devices?
```

I opt <yes>

Then I get the partition discs menu

```
This is an overview of your currently configured partitions and mount points. Select a partition to modify its settings (file system, mount point, etc.), a free apce to create partitions, or a device to initialize its partition table.

       Configure iSCSI volumes

       Undo changes to partitions
       Finish partitioning and write changes to disk
```

I opt "Finish partitioning and write changes to disk" and I get the following message 

```
No root file system is defined.

Please correct this from the partitioning menu.
```

Where do I go from there? I normally would try some things out... but there aren't any options to play around with. If someone can help me, don't talk to fast please. I'm still fairly new to linux/servers, and totally new to RAID setup. Only thing I've got going for me at this point is cool hair.

---

### Post by msmith0957 on 2010-06-15
Has this issue ever been resolved? I am working with a similar Supermicro server, a 6025B-T which has an Adaptec AIC 7902 card. I previously had the server running FreeBSD with 3x 320gb disks in RAID 5 but after a recent crash (not disk related, more or less my fault) I have decided I want to switch to Ubuntu.

When I try to install the latest versions of Ubuntu (tried Server and Desktop) I'm assuming it isn't recognizing the RAID array. I think I have to add a boot option to specify the adapter I'm using, so I found this page [http://lxr.linux.no/linux+v2.6.22/Documentation/kernel-parameters.txt](http://lxr.linux.no/linux+v2.6.22/Documentation/kernel-parameters.txt) which lists all the parameters and noticed my card is listed with options as shown here, [http://lxr.linux.no/linux+v2.6.22/Documentation/scsi/aic79xx.txt](http://lxr.linux.no/linux+v2.6.22/Documentation/scsi/aic79xx.txt) . The problem is, I just simply don't know which options I should use to get this going. I selected install with the option aic79xx.aic79xx=no_reset but nothing really happened with that. If someone could lead me in the right direction, that would be great, Thanks!

As a disclaimer, I think I should add that I'm a new comer to Ubuntu and fairly new to the *nix scene in general :popcorn:

---

### Post by msmith0957 on 2010-06-15
I forgot I was using the Intel option in the bios, not adaptec, so when I ran lspci from the Ubuntu server x64 disc, it mentioned:

```
00:1f.2 RAID bus controller: Intel Corporation 631xESB/632xESB SATA RAID Controller (rev 09)
```

I'm thinking I have to add a kernel module manually using modprob, but now I'm not sure which module to add. It seems like in that kernel-paramters.txt there's nothing I could use. What should I do?

update: I found this page, and I think should show me which modules to add: [http://cateee.net/lkddb/web-lkddb/SATA_AHCI.html](http://cateee.net/lkddb/web-lkddb/SATA_AHCI.html) . Problem is, it lists 'ahci' and 'libahci'. ahci is already loaded as it was listed when I ran lsmod, but when I tried 'modprobe libahci', i got the message:

```
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong to /etc/modprobe.d/.
FATAL: Module libahci not found.
```

Where should I go from here? Or should I be looking at this? [http://lxr.linux.no/linux/drivers/ata/Kconfig](http://lxr.linux.no/linux/drivers/ata/Kconfig) ?

I should mention that I have the intent of keeping at least one existing partition intact on the existing raid 5 array. So messing with the array at this point is out of the question.. But if it really is the only way, I suppose I could attempt to back it up somewhere, just would be a hassle to do so in my case considering I don't have a single drive large enough to store it all.

---

### Post by uOpt on 2010-06-15
I would only ever use mdadm (or ZFS or later btrfs). This onboard stuff leads nowhere.

---

### Post by msmith0957 on 2010-06-16
well I'm already using it I just need to know how to have Ubuntu recognize it properly.. What should I try next ?

---

### Post by msmith0957 on 2010-06-20
*bump*

---

### Post by koenn on 2010-06-20
first of, don't let the OP in this thread throw you off.

This is a harware raid controller. What you need to do first, is configure a RAID with the dedicated config utility that should be accessible while  the machine boots (you'll have to press a certain key during the POST)

The 'volumes' or 'LUNs' that you configure their, will present themselves as disks/partitions to the operating system later on, so you can thread them as ordinary disks - i.e. mkfs and be done with it, or use the partitioner during the install to create filesystems. This is probably where the OP went wrong. 

What you do need is a driver/module that supports the Adaptec RAID controller, otherwise your operating system won't see the volumes you  created (as they are controlled and managed by the adaptec controller)

the module you're looking for is     * aic79xx
according to this page [http://hardware4linux.info/component/34851/](http://hardware4linux.info/component/34851/)

On a running system, you could try 'insmod'. When installing, the (Debian) installer offers an option to load additional modules, somewhere.
Unless all of that has been changed recently in Ubuntu. Then you need to go find a manual.

---

