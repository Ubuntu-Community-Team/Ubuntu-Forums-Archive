---
title: "LVM Problem"
date: 2007-03-04
forum: Server Platforms
---

### Post by ScatterBrain on 2007-03-04
I've got a Dell Server with a Perc4/SC RAID controller attached to a PowerVault 220s storage array.

In the setup I have two RAID arrays - both RAID 5.  Over the weekend, I added a new physical drive to one of these arrays.  I used the tools for the PERC card to extend the Logical Drive's total storage space.  This all went fine.

Now that I have the space available, I wanted to extend the LVM logical drive and XFS filesystem on top of the LVM logical drive.  But as yet, I've not discovered a way for LVM to grow into this new space.  Everything that I can find seem to want me to add a true physical drive the Volume group.  That's not the way this setup needs to work.

Here's some information:

```
root@firebrand:~# lvdisplay
  --- Logical volume ---
  LV Name                /dev/monthly_vg/monthly_lv
  VG Name                monthly_vg
  LV UUID                45gWDw-Hqdj-DeAa-08P0-kW3A-bToN-PAHzfg
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                838.12 GB
  Current LE             214559
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           253:0

  --- Logical volume ---
  LV Name                /dev/daily_vg/daily_lv
  VG Name                daily_vg
  LV UUID                sQmIwF-ALY2-bfqG-DsA5-sPhF-jorH-PdXCuu
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                1.09 TB
  Current LE             284958
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           253:1

root@firebrand:~# pvdisplay
  --- Physical volume ---
  PV Name               /dev/sdd
  VG Name               monthly_vg
  PV Size               838.12 GB / not usable 0
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              214559
  Free PE               0
  Allocated PE          214559
  PV UUID               cuwgE3-85nP-745p-C4m7-0vIF-Qj2p-g21Q1E

  --- Physical volume ---
  PV Name               /dev/sdc
  VG Name               daily_vg
  PV Size               1.09 TB / not usable 0
  Allocatable           yes
  PE Size (KByte)       4096
  Total PE              285694
  Free PE               736
  Allocated PE          284958
  PV UUID               7Yo67c-bnEw-tFEA-FV03-DEpa-zjSV-HkVEcV


```The PV /dev/sdc and VG /daily_vg is the LVM setup that I'm wanting to extend.  I should have in excess of 300GB to add to the drive, but I can't seem to find it.

```
root@firebrand:~# cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD800JD-75MS Rev: 10.0
  Type:   Direct-Access                    ANSI SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD800JD-75MS Rev: 10.0
  Type:   Direct-Access                    ANSI SCSI revision: 05
Host: scsi2 Channel: 00 Id: 06 Lun: 00
  Vendor: DELL     Model: PV22XS           Rev: E.18
  Type:   Processor                        ANSI SCSI revision: 03
Host: scsi2 Channel: 01 Id: 00 Lun: 00
  Vendor: MegaRAID Model: LD 0 RAID5 1430G Rev: 351X
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi2 Channel: 01 Id: 01 Lun: 00
  Vendor: MegaRAID Model: LD 1 RAID5  858G Rev: 351X
  Type:   Direct-Access                    ANSI SCSI revision: 02
```The SCSI Disc with 1430GB is the actual RAID array on which the LVM in question is sitting on.  Before I started the process the array was just over 1TB in size.

Can someone point me to the right documents/commands so that I can grab the extra space?

If it matters, I'm running Dapper (6.06 LTS) on the server.

Thanks in advance,
ScatterBrain

---

### Post by abbzer0 on 2007-04-20
Well, I'm about to pick up a Powervault 200S array this morning and add it to my Poweredge 2500.  I'll let you know if things work out for me, rather, if I find out any secrets to help you.  Best of luck.

---

### Post by Werner_vd_Walt on 2008-01-09
Scatter did you ever overcome your problem? I'm sitting with exactly the same issue and have not been able to find any resolution in the LVM docs?

:confused:

Werner

---

### Post by colinwilson on 2008-01-09
can you do a vgdisplay for me?

---

### Post by koenn on 2008-01-10
not that I ever done this, but from what i read about LVM, this should be pretty straightforward : 
- extend a logical volume
- let the filesystem grow

[http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html](http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html)

---

### Post by Werner_vd_Walt on 2008-01-11
Actually its not that simple. I have created a step-by-step below detailing the process after the necessary research:

These steps show you how to extend your LVM configuration and file system on an existing hardware RAID volume that you added extra disc space to and it got extended.  If you just add a separate new disc without extending the existing volume then you can do a normal vgextend as LVM will pick up the new device and use it.
 With an existing RAID volume expansion LVM cannot “see” the extra space and can therefore not use it, unless you create a second partition from the new space and then give that to LVM.
 Using the method below you still only maintain one RAID volume and partition but make LVM aware of the extra space and extends your file system to be able to use it.
 Lastly, if you are making use of software RAID then you also don't have to jump through these hoops but just do a vgextend.
 

 Please note that some of these steps may seem like duplication or as unnecessary, but as you are making changes to a live file system you stand a very good chance of losing all your data if you don't double-check everything as you are going along.
 As always when working with stored data, please make sure that you have a current, valid backup of your data just in case something goes wrong and you have to restore from it.
 All of these steps are taken at your own risk.  Do not blame me if you happen to loose data.  That being said I have tried and tested every one of these steps myself on a live system with about 2TB of data and everything worked 100% with no data loss.
 Also I prefer making use of tools like cfdisk instead of fdisk but you can substitute where necessary with your personal preference tools.
 

 [LIST=1]
[*]Using your RAID 	tools extend the RAID volume with the extra disc(s) added.  This can 	usually be done on a live running system as its happening 	transparently to the O/S.
[*]Once the RAID volume 	has been successfully extended at a hardware level then type **fdisk 	-l** to get a list of all the current physical storage devices and 	their partitions.  Find the ***/dev/sd?*** device reference 	in the list for your extended RAID volume.
[*]Type **cfdisk -P s 	/dev/sd[*****deviceref*****]** 	to get a breakdown of the partition and space allocation for the 	physical RAID device and confirm that the extra free (extended) 	space is indeed available.
[*]Type **df -h** to 	check the current size of the RAID volume filesystem.
[*]Type **umount 	/dev/[*****volumegroup*****]/[*****logicalvolume*****]** 	to unmount your current RAID volume file system.
[*]Type **cfdisk 	/dev/sd[*****deviceref*****]** to open the partition 	layout of the RAID volume.  You should see two partitions – the 	original LVM partition and the new extended free space.
[*]The next step seems 	totally counter-intuitive but according to all the documentation I 	have read it is correct.
[*]Delete the current 	LVM partition, and immediately thereafter create a new partition 	that occupies the full new space available.
[*]Set the new 	partition type to LVM.
[*]Write the changes.
[*]Quit cfdisk and 	reboot the machine.
[*]Type **cfdisk -P s 	/dev/sd[*****deviceref*****]** and confirm that the new 	partition is in actual fact occupying all the space and that there 	is no more free space indicated.
[*]Type **umount 	/dev/[*****volumegroup*****]/[*****logicalvolume*****]** 	to unmount your current RAID volume file system.
[*]Type **pvdisplay 	/dev/sd[*****deviceref*****][*****partition#*****]** 	to confirm the current size of the LVM volume and that there are 0 	available free PEs.
[*]Type **pvresize 	/dev/sd[*****deviceref*****][*****partition#*****]** 	to resize the LVM volume to occupy the full space available on the 	RAID volume.
[*]Type **pvdisplay 	/dev/sd[*****deviceref*****][*****partition#*****]** 	again to confirm that the LVM volume has been resized to fit the new 	RAID partition size and that you now have free PEs available again.
[*]Type **vgdisplay 	[*****volumegroup*****]-[*****logicalvolume*****]** 	and take note of the volume group size and the number of free PEs 	available.
[*]Type **lvextend -v 	-l +[#FreePEs] /dev/[*****volumegroup*****]/[*****logicalvolume*****]** 	to extend your logical volume to fully occupy the volume group 	space.
[*]Type **vgdisplay 	[*****volumegroup*****]-[*****logicalvolume*****]** 	again to confirm that the logical volume has been resized to fit the 	new LVM volume size and that you now have 0 free PEs available.
[*]Type **e2fsck -f -v 	/dev/[*****volumegroup*****]/[*****logicalvolume*****]** 	to check the current file system for any errors before resizing it.
[*]Type **resize2fs -p 	/dev/[*****volumegroup*****]/[*****logicalvolume*****]** 	to resize the file system to fit the logical volume.
[*]Type **e2fsck -f -v 	/dev/[*****volumegroup*****]/[*****logicalvolume*****]** 	to check the current file system for any errors after resizing it.
[*]Type **e2fsck -D 	/dev/[*****volumegroup*****]/[*****logicalvolume*****]** 	to optimize the directory structures.
[*]Manually mount the 	file system again or reboot and let it auto-mount.
[*]Type **df -h** to 	check that the file system has successfully been resized.
[/LIST] I hope this helps...

Werner

---

### Post by koenn on 2008-01-11
Impressive

---

