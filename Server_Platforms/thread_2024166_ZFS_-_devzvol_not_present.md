---
title: "ZFS - /dev/zvol not present"
date: 2012-07-13
forum: Server Platforms
---

### Post by Biggs427 on 2012-07-13
I ran into a problem trying to share a zvol with iSCSI (ietd).
 
I found the solution and decided to post it here in case someone have the same problem.
 
I was able to create a raidz pool with zpool without problem.
```
zpool create tank raidz /dev/sda /dev/sdb /dev/sdc ... and so on
```
 
Next I created a zvol:
```
zfs create tank/bigvol
```
 
I was able to mount the drive with zfs mount but the /dev/zd0 (which should be the tank/bigvol volume) was not created nor the /dev/zvol.
 
Playing with the zfs tool + googling, I found that what was missing was the -V switch.  
So I recreated the zvol using it: 
```
zfs create -V 5000G tank/bigvol
```
 
Now the /dev/zd0 and /dev/zvol are present, even after a reboot.
 
I can then share the /dev/zd0 with ietd.
 
My ietd.conf looks like it:
```

[FONT=Courier New]Target iqn.2012-07.blabla:storage.bigvol[/FONT]
[FONT=Courier New]  Lun 0 Path=/dev/zd0,Type=fileio[/FONT]
[FONT=Courier New]  ...[/FONT]
[FONT=Courier New]  Put you ietd.conf config here[/FONT]

```
 
Now everything is working and is blazingly fast compared to FreeNAS. :shock:
 
This config was done using Ubuntu Server 11.10 X64 and the PPC ZFS for Linux 0.6.066-rc9.
 
Hope that this could help other.

---

