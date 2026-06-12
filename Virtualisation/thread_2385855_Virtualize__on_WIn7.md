---
title: "Virtualize ?? on WIn7"
date: 2018-02-25
forum: Virtualisation
---

### Post by mcapaldo on 2018-02-25
I have a win7 64bit amd 8 core pc with a raid1 (2x6tb drives) for Media Center recordings.  I know I can't run windows raid 5 in Win 7.  BUT I CAN in Win8 or Win 10.    I want to replace the 2x6tb raid1 with a 3x3tb raid5.    Windows 8/10 do not have a built in way to easily expand a RAID5 (like ubuntu mdadm does).  There are 3rd party windows software that do this.    Would it be a good idea to install ubuntu 16.04 64bit on the boot SSD 120gb drive, and use mdadm to setup the raid5.  THEN setup a a virtual machine for windows 7, and somehow use the mdadm ubuntu raid within the virtual machine, without making a huge 6tb ish virtual drive on top of the linux mdadm.  I wanna have the raid5 3x3tb mdadm shared for the windows virtual machine.  Is this possible?

---

### Post by KillerKelvUK on 2018-02-26
> without making a huge 6tb ish virtual drive on top of the linux mdadm

What do you mean by this?

FWIW, I run a kbuntu host which has a 4x4tb raid 5 using mdadm which I provision as a simple ext4 volume which is then served across my local network via NFS and my Windows 10 guest (Pro) then mounts the NFS share and has full read/write access to it.

---

### Post by mcapaldo on 2018-03-01
Here is what I have...

Win7 64bit PC AMD * Core CPU, 32 GB RAM, 120GB SSD Boot/OS Drive, & Currently 2x 6tb mirrored drives.  Running Windows Media Center for a PC DVR.

What I am asking is this.....

On same above PC, Can I do this.....

1. Run Ubuntu 16.04 LTS 64 Bit with 3 x 3tb sata III in Raid 5 using linus MDADM.

2. install Virtual Box, and virtualize Windows 7 and Media Center on same above hardware.

3. Can I setup the 3x xtb raid5 mdadm and use it as a passthru in virtual box, so Windows 7 media center will record and save my widnows recordings all on the same box BUT to the mdadm raid5 (linux) via passthru or shared folder?

Is this doable?

Reason I am asking is cause it seems to be a PITA to get windows 8 or Win 10 (yea I know media center is not included in the base os install but there are people that are making it work).

I already have a backup server on another box, and do not want to have two pcs on all the time to record my shows.  I power up the backup server once or twice a week to backup my pcs and them power it down.

I would like to be able to trick win 7, or 8, or 10 into thinking its using a network share BUT its on the same box.  Just linux mdadm raid NOT windows Riad.

---

### Post by QIII on 2018-03-01
Hello!

You may want to reconsider your objective.  The graphics performance of VirtualBox is abysmal and you won't be satisfied with using media player on a VBox guest.

If you want good graphics performance on one or the other, plan on that as the host.  Then ask the question with that in mind.

Cheers!

---

### Post by CharlesA on 2018-03-01
> **QIII said:**
> Hello!

You may want to reconsider your objective.  The graphics performance of VirtualBox is abysmal and you won't be satisfied with using media player on a VBox guest.

If you want good graphics performance on one or the other, plan on that as the host.  Then ask the question with that in mind.

Cheers!

Vouching for that.

Although you could try using PCI passthrough if your system supports it (needs support from CPU and mobo) to pass thru a video card to the guest with VirtualBox, but that depends on quite a lot of factors.

Please see here: [https://www.virtualbox.org/manual/ch09.html#pcipassthrough](https://www.virtualbox.org/manual/ch09.html#pcipassthrough)

---

### Post by SeijiSensei on 2018-03-02
If you install the extension pack, you should be able to pass through access to the RAID device using "[Shared Folders]("https://help.ubuntu.com/community/VirtualBox/SharedFolders")."  You should be able to assign the array to a Windows drive letter using this method.

---

