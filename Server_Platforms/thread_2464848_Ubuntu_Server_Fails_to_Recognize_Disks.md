---
title: "Ubuntu Server Fails to Recognize Disks"
date: 2021-07-13
forum: Server Platforms
---

### Post by sniper8752 on 2021-07-13
I am getting this error message on Server installation: "Block probing did not discover any disks.  Unfortunately, this means that installation will not be possible.". I have two HDDs plugged into a Dell PowerEdge T320.

---

### Post by scorp123 on 2021-07-14
> **sniper8752 said:**
>  I have two HDDs plugged into a Dell PowerEdge T320.

Not enough details. "plugged into" ... How exactly? USB? eSATA? SCSI? Some kind of RAID controller?

---

### Post by dragonfly41 on 2021-07-14
[Google searched]("https://askubuntu.com/questions/1302392/ubuntu-server-20-04-setup-stuck-at-block-probing-did-not-discover-any-disks")

---

### Post by sniper8752 on 2021-07-16
SAS/chasis.

---

### Post by MAFoElffen on 2021-07-16
So... On that Dell PowerEdge chassis/Motherboard, you have a disk controller in it's own proprietary slot. The motherboard itself only has a few true SATA connections. Those are usually just connected to DVD drives and the Dell Tape or Cartridge drives. There are cables that go from that disk controller card to the SATA/SAS backplane..

It would be handy to know which specific controller it is. I am familiar with a lot of different Dell PowerEdge chassis and differing RAID/Storage controllers.. Some have just software RAID and some Hard RAID. That controller has to see the Disks, before the BIOS sees it, which means if the BIOS doesn't pass on that info until that handoff. No OS is going to see the disks, until then. More info is needed to help you..

You can get a hint on the POST messages, which the controller, as it init's in BIOS POST, it's going to prompt that a "specific" controller in present, booted the ROM, and to press a key combination to get into it's setup/config... Please find out what controller is there., so we can give you specific instructions based on what controller is present.

If it is a T320, I'm thinking it probably came with a Dell PERC H310... For it, go into the setup for the card, and tell us if it has a pass-through mode or just RAID Types. As I remember, I'm thinking that 2012, that still just had RAID types..Define the individual disks as single-disk RAID0 members. Save and exit. Continue to boot into the installer. I know that it might seem like a quark that you have to mark it as RAID to use a single disk, but it works with that controller and chassis.

The installer should then see the disks... Note that that controller will only recognized disks as being 2TB or smaller. Even if they are bigger, it will only see them at that limited size. If you have larger, it will only let you partition the first 2TB's. (because that is what the system, below the OS will see it as.) If you need to use bigger disks in that server chassis, use a newer disk controller.

---

### Post by setpebmur on 2022-06-29
Hello, I Have a server and am seeing the same error as OP, and I as well have the PERC H310 MINI controller in RAID mode, here's my configuration: 

Server: Dell Poweredge R720.
Drive 0: 256GB SSD, non-RAID mode, Bootable.
Drive 1: 200GB SAS, non-RAID mode, Foreign.
Drives 2-7: 3700GB SATA, RAID mode, Online.

All drives in 2-7 are in a RAID-5 configuration. 

After checking for updates and configuring the LAN PHYs, the ubuntu 22.04 installer gives me the error [COLOR=#000000]"Block probing did not discover any disks. Unfortunately, this means that installation will not be possible." I tried the solution in the Stack Exchange question and running `[/COLOR][COLOR=var(--black-800)][FONT=var(--ff-mono)]umount /isodevice[/FONT][/COLOR][COLOR=#000000]` gave me a 'not found' error. Did I do something wrong in the configuration as far as the tips above? ^[/COLOR]

---

