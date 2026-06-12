---
title: "NTFS  volume + Quota / smbcquotas not working"
date: 2016-04-17
forum: Server Platforms
---

### Post by smoll on 2016-04-17
I have a server with samba shares, whose partitions are formatted NTFS for ease of recovery purposes (RAID-1 of 2 mirrored HDDs, OS residing on a seperate HDD).

Are quotas not possible for NTFS volumes? I have tried everything I can find via google searching, but every example found is either ext3/4, or XFS. I was under the impression quota would work for NTFS, as smbcquotas can 'set or get quotas of NTFS-5 shares' (and supposedly ntfs-3 ?). I have tried various reiterations of quota, smbcquota (which fails presumably because quota does not set for the NFTS partition), (a)quota.user, etc. I have even searched for quotas use with fuseblk, but no luck. And btw, not planning to use samba with LDAP if that matters any.
Can someone please help? Maybe it is a version incompatibility, or needing another package? I am at wits end. Thank you !
---

ubuntu server 12 LTS distribution upgraded to 14.04.4 LTS, quota 4.01-3, quotatools 1.4.12-1, samba 2:4.1.6+dfsg-1ubuntu2.14.04.13
---

/etc/fstab:
/dev/md0p1    /mnt/RAID1o    ntfs-3g defaults,usrjquota=aquota.user,grpjquota=aquota.group,jqfmt=vfsv0    0    0

remounting via 'mount -o remount' does not work "Remounting is not supported at present. you have to umount volume and then mount it once again.", so...
sudo umount -a
sudo mount -a
sudo mount | grep RAID1o >>> 
/dev/md0p1 on /mnt/RAID1o type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

sudo quotacheck -cvuga >>>
quotacheck: Cannot find filesystem to check or filesystem not mounted with quota option.

---

### Post by MAFoElffen on 2016-04-19
Were you looking for this?
[https://www.samba.org/samba/docs/man/manpages/smbcquotas.1.html](https://www.samba.org/samba/docs/man/manpages/smbcquotas.1.html)

---

### Post by smoll on 2016-04-19
MAFoELffen-
have previously read smbcquotas man page; smbcquotas does NOT work /errors out, due to underlying quotas not identifying volume correctly (please see above).  (I will have to post the exact smbcquota error later when I am at the server.)
not sure what /where the second link (101pages?) shows info on this problem?
this link was about the most useful i could find internetwise:   [http://theurbanpenguin.com/wp/index.php/lpic-3-300-smbcquotas/](http://theurbanpenguin.com/wp/index.php/lpic-3-300-smbcquotas/)
and yes i have read /done the research for quota, which works simply no problems on an ext3/4 volume (tested already).

---

### Post by MAFoElffen on 2016-04-21
At first, I didn't think there would be an issue of a quota (thought it might be file system immaterial) on an underlying filesystem. But under further investigation... You are may be on to something with NTFS. I had to do some digging, but found this on the Samba Mailing List:
> 
smbcquotas does support quota management for "root" NTFS shares, for instance, if you have w2k server and both C: and C:\Some_folder are shared, You can manage quotas on "C:", but You cannot manage quotas with smbcquotas on "C:\Some_folder", just because quota doesn't apply per-share, on most filesystems (UFS, NTFS, EXT3) quota is "per filesystem".


split your drive onto several filesystems and there's no other way to get quota support "per share"

So there does seem to a limit. But as this person had explained, it does seem to be different than it works elsewhere. (???) Now you have my curiosity... so digging deeper.

---

