---
title: "VMware - Backup one small file on virtual image"
date: 2008-04-30
forum: Virtualisation
---

### Post by Phoenix Rising on 2008-04-30
I have an Ubuntu host running Windows XP as a guest (for access to QuickBooks Pro for my business accounting).  I have a very simple file or two that I'd need to back up nightly, but of course the space for the VM is a 20gb pre-set file.  Right now I just have Ubuntu copying the file every night to an external hard drive, and wiping files that are over 3 days old.

Is there a better/easier way to do this?  Ideally I'd only be copying over my accounting files, not the entire virtual image.  I'd prefer not to have to run the Windows VM 24/7 either, but would be willing if it's the only possible way.

---

### Post by Kokopelli on 2008-05-02
You should be able to use vmware mount.pl

```
vmware-mount.pl [virtual disk location] 1 -t ntfs /media/vd
```

[http://www.vmware.com/support/reference/linux/loopback_linux.html](http://www.vmware.com/support/reference/linux/loopback_linux.html)

personally I would probably set a cron job to check to see if the VM is running (vm-cmd getstate), if it is not then mount the partition, rdiff-backup the file, then unmount the partition.

EDIT: interesting second way to mount a vmdk (have not tried this personally)
[http://www.tuxfeed.com/2008/01/14/howto-mount-ntfs-vmware-virtual-disk-image-vmdk-readwrite/](http://www.tuxfeed.com/2008/01/14/howto-mount-ntfs-vmware-virtual-disk-image-vmdk-readwrite/)

---

