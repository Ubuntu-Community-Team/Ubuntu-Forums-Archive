---
title: "I can't mount my Vista partition!"
date: 2009-01-12
forum: The Cafe
---

### Post by Fixman on 2009-01-12
I have a hard drive with one partition formatted as NTFS, where I store windows Vista (and many other files). I usually set it to auto mount on /etc/fstab, however since a few days ago, it does not only not auto mount but neither does mount. When I do

```
 sudo mount /dev/sdb1 -o force 
```

It gives me this error:

```
 ntfs_attr_pread: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details. 
```

However, I can still boot normally from Vista without any problems. I tried using chkdsk as it told me, using ntfsfix, and even booting from the Live CD to see if it was a configuration problem with no avail. Can someone help me on this?

---

### Post by caljohnsmith on 2009-01-12
I'm assuming from the error that you posted that you actually included a mount point with the mount command you used, because the command should look something like:
```
 sudo mount -o force /dev/sdb1 /mount_point
```
How about posting the output of:
```

cat /etc/fstab
sudo fdisk -lu
sudo blkid -c /dev/null
```
And we can work from there if you want.

---

### Post by bartos on 2009-01-12
Make sure Vista is Not in hibernate mode. I have noticed it will not mount when booting and Vista has been put in hibernate mode.

---

### Post by treesurf on 2009-01-12
Wasn't there an ntfs update a few days ago?

---

### Post by Polygon on 2009-01-14
try to run vista and then do a checkdisk run on that partiton, it might be corrupted

---

