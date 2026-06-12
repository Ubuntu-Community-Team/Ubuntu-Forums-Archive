---
title: "disk mount"
date: 2012-06-23
forum: Server Platforms
---

### Post by lolium on 2012-06-23
hey guys,

not the best when it comes to things like hardware etc...

I broke my raid array the other day to have 4 separate disks rather then 4 disks in raid 10 as i don't need raid. When I re-installed 10.04 server ed, my 2nd disk is showing as being mounted on /var/lib/ureadahead/debugfs - not sure why this is as i thought everything would be handled by the 3 partitions on my primary drive, is it safe to unmount this disk, and also how will this be getting mounted as i cant see this is fstab?

would you need more output from fdisk/df to help with this?

Regards

---

### Post by darkod on 2012-06-23
I don't know why it gets mounted to that mount point.

To get a disk/partition mounted on boot, and if we are talking about ext4 partition for example, the entry in /etc/fstab you will need to make would look like:
```
/dev/sdb1   /mount-point   ext4   defaults   0   0
```Of course, the location /mount-point needs to exist, so if it's a new folder you will need to create it first.

PS. Was the raid software raid or fakeraid? If it was fakeraid I guess it would be best if you make sure the meta data is removed, to avoid any issues in the future. You can do that for all disks with:
```
sudo dmraid -E -r /dev/sdX
```

---

