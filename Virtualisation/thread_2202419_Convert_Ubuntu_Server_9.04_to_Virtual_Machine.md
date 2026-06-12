---
title: "Convert Ubuntu Server 9.04 to Virtual Machine"
date: 2014-01-29
forum: Virtualisation
---

### Post by Thongrob on 2014-01-29
Now system running OS Ubuntu 9.04 and App (Web service) on Physical H/W (dell server  R300)  ...........  So i need to convert to on  vmware esxi.....

I do solution
 1. vmware cold clone : error  unknonw platform

 2. vmware vconvert 3.5/ 4.2 /4.3 /5.0/ 5.5  : error between converter



If you can advise me for this solve problem .....

---

### Post by coffeecat on 2014-01-29
Not an Ubuntu, Linux and Other OS Chat thread.

*Thread moved to **Virtualisation**.*

---

### Post by CharlesA on 2014-01-29
> **Thongrob said:**
> Now system running OS Ubuntu 9.04 and App (Web service) on Physical H/W (dell server  R300)  ...........  So i need to convert to on  vmware esxi.....

I do solution
 1. vmware cold clone : error  unknonw platform

 2. vmware vconvert 3.5/ 4.2 /4.3 /5.0/ 5.5  : error between converter



If you can advise me for this solve problem .....

I'd probably just use Clonezilla to clone the drive to an image (somewhere on the network), then create a VM with the same size disk in ESXi and restore the image to it.

You'd probably have to mess with the network configuration, but that will probably be the easiest way to migrate the machine.

Note: 9.04 has been End of Life since October 23, 2010, so it might not work and you'd have to take a huge upgrade path to get on a supported release.

---

### Post by Thongrob on 2014-01-29
> **CharlesA said:**
> I'd probably just use Clonezilla to clone the drive to an image (somewhere on the network), then create a VM with the same size disk in ESXi and restore the image to it.

You'd probably have to mess with the network configuration, but that will probably be the easiest way to migrate the machine.

Note: 9.04 has been End of Life since October 23, 2010, so it might not work and you'd have to take a huge upgrade path to get on a supported release.

Ok thank you for your answer

Now i test on the LAB before to do real system......   The VMware suggest to me  upgrade ubuntu 9.04 to 10 upper  but am not sure if upgrade new version impact to the old system and app//// ....   


Frist i try to use clonezilla

---

### Post by CharlesA on 2014-01-29
Yeah, definitely test it first on a cloned system and not the production box.

You would have to upgrade 9.04 -> 9.10 -> 10.04. I'm not sure if you can get to 12.04 directly from 10.04 or if you need to go thru 10.10 -> 11.04 -> 11.10 -> 12.04, but you should definitely test it out as 9.04 is ancient compared to 12.04.

---

### Post by Thongrob on 2014-01-29
Please help to suggest  how to upgrad from 9.04 to 10.04   Command

---

### Post by CharlesA on 2014-01-29
Check here:
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by Thongrob on 2014-01-30
> **CharlesA said:**
> Check here:
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

Hi Charles

Do you have idea for restore image to virtual machine on vmware esxi...(I'm not sure you have knowledge of esxi )


Now the image save to external HDD .  when i create new virtual machine and map CD-ROM drive to ISO file of clonezilla  but for the extrenal HDD have image cannot brow to host .

---

### Post by CharlesA on 2014-01-30
> **Thongrob said:**
> Hi Charles

Do you have idea for restore image to virtual machine on vmware esxi...(I'm not sure you have knowledge of esxi )


Now the image save to external HDD .  when i create new virtual machine and map CD-ROM drive to ISO file of clonezilla  but for the extrenal HDD have image cannot brow to host .

Right, you would need to put it on a file share somewhere (or use Samba/NFS/ or SSH) because EXSi doesn't really support external devices.

If you have another box around, you can just install openssh-server on it and tell clonezilla the logon info and where the image is located. THat would probably be easier if you don't have Samba or whatever already set up.

I use Samba 90% of the time with Clonezilla because I am usually working with WIndows boxes.

---

### Post by Thongrob on 2014-01-30
> **CharlesA said:**
> Right, you would need to put it on a file share somewhere (or use Samba/NFS/ or SSH) because EXSi doesn't really support external devices.

If you have another box around, you can just install openssh-server on it and tell clonezilla the logon info and where the image is located. THat would probably be easier if you don't have Samba or whatever already set up.

I use Samba 90% of the time with Clonezilla because I am usually working with WIndows boxes.

 I'm not sure the clonezilla can clone OS on server have raid card also.  but on the my lab it 's restore on vmware workstation is OK....

For SAMBA can use windows file sharing or NAS Storage Can use or not ?

---

### Post by CharlesA on 2014-01-30
Depends on what kind of RAID card is in the machine.

If the image restored to vmware workstation ok, try it on ESXi and see what happens.

You can use Windows or a NAS for Samba, I've used it with a Windows 2008 AD before.

---

### Post by Thongrob on 2014-01-31
> **CharlesA said:**
> Depends on what kind of RAID card is in the machine.

If the image restored to vmware workstation ok, try it on ESXi and see what happens.

You can use Windows or a NAS for Samba, I've used it with a Windows 2008 AD before.



RAID card in server Dell R230:P

---

### Post by Thongrob on 2014-02-09
I read on the web clone zilla , not support software raid but to day i try to backup on hardware raid on Dell Serve R320....  If can Backup i will tell you later.....

> [h=3][COLOR=#3333ff]Limitations:[/COLOR][/h]
[LIST]
[*]The destination partition must be equal or larger than the source one.
[*]Differential/incremental backup is not implemented yet.
[*]Online imaging/cloning is not implemented yet. The partition to be imaged or cloned has to be unmounted.
[*][COLOR=#ff0000]Software RAID/fake RAID/firmware RAID is not supported by default. It can be done manually only[/COLOR].
[*]Due to the image format limitation, the image can not be explored or mounted. You can _NOT_ recovery single file from the image. However, you still have workaround to make it, read [this]("http://drbl.org/faq/fine-print.php?path=./2_System/43_read_ntfsimg_content.faq#43_read_ntfsimg_content.faq").
[*]Recovery Clonezilla live with multiple CDs or DVDs is not implemented yet. Now all the files have to be in one CD or DVD if you choose to create the recovery iso file.
[/LIST]


---

### Post by Thongrob on 2014-02-09
Yesterday , i can save image ubuntu on server dell r300 but try to restore on vmware esxi cannot......  when restore finish and reboot not anything boot

---

### Post by CharlesA on 2014-02-09
Ehhh...

I guess you could try the "back the whole thing up via tar and restore it on a clean install" but that's quite messy.

[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

---

### Post by Thongrob on 2014-02-09
information

> Linux 2.6.28-14-server #47-Ubuntu SMP Sat Jul 25 01:18:34 UTC 2009 i             686 GNU/Linux
[EMAIL="root@wsi-finance"]root@[/EMAIL]:~# /bin/uname -m
i686
[EMAIL="root@wsi-finance"]root@[/EMAIL]:~# df -lh
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/wsi--finance-root
                      141G   38G   96G  29% /
tmpfs                 5.0G     0  5.0G   0% /lib/init/rw
varrun                5.0G   84K  5.0G   1% /var/run
varlock               5.0G     0  5.0G   0% /var/lock
udev                  5.0G  136K  5.0G   1% /dev
tmpfs                 5.0G     0  5.0G   0% /dev/shm
lrm                   5.0G  2.2M  5.0G   1% /lib/modules/2.6.28-14-server/volati             le
/dev/sdb5             228M   27M  190M  13% /boot
[EMAIL="root@wsi-finance"]root@[/EMAIL]:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.04
Release:        9.04
Codename:       jaunty
[EMAIL="root@wsi-finance"]root@[/EMAIL]:~# fdisk -l
Disk /dev/sdb: 159.4 GB, 159450660864 bytes
255 heads, 63 sectors/track, 19385 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19354   155460973+  8e  Linux LVM
/dev/sdb2           19355       19385      249007+   5  Extended
/dev/sdb5           19355       19385      248976   83  Linux



---

### Post by Thongrob on 2014-02-09
As below image on ubuntu server 9.04:p

[ATTACH=CONFIG]250223[/ATTACH]



Function TAR can restor to VMWARE Esxi or not ? 



> **CharlesA said:**
> Ehhh...

I guess you could try the "back the whole thing up via tar and restore it on a clean install" but that's quite messy.

[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

---

### Post by CharlesA on 2014-02-09
Depends if you can boot a livecd with ESXi. I've not used it before, so I do not know what it is capable of.

---

### Post by Thongrob on 2014-02-10
i have 2 image for  2014-01-31-05-img  from ubuntu 9.04 on PC (Lab-test)

for 2014-02-09-05-img-finance from ubuntu 9.04 on Server Dell (Production)


Both image diffrent image file

[ATTACH=CONFIG]250228[/ATTACH]

---

