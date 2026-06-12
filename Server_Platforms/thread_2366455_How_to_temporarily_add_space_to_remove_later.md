---
title: "How to temporarily add space to remove later?"
date: 2017-07-18
forum: Server Platforms
---

### Post by LHammonds on 2017-07-18
I use LVM and have separate partitions for root, opt, home, var and so on. (It is a virtual server so I can add space as needed)

I know how to add a hard drive, add that space to the LVM and then extend the LVM partition and the file system in it.

What I don't know how to do is to temporarily add space and remove it at a later point.

For example, let's say I know the following folder is going to grow a lot but only for a one-time use:

```
/var/www/html/uploads
```

How can I add space that can be removed a few weeks later...such as adding a 500 GB drive and mounting it to /var/www/html/uploads?  Once done, I want to remove that drive but not destroy the LVM.  In other words, I do NOT want to add the space to the overall LVM.

Thanks,
LHammonds

---

### Post by darkod on 2017-07-18
You can't mount a new disk directly to a folder that is not empty. So you would not be able to temporarily mount it and then remove it.

What do you mean by "destroy the LVM"? You can add a new disk (PV) to the LVM, extend the LV and filesystem onto it. Then when finished, you can shrink the filesystem, remove the used extents from that PV (if any) and at that point you can safely remove it from the LVM.

That sounds like what you require. You are not destroying the whole LVM, just removing used extents and removing one PV.

---

### Post by LHammonds on 2017-07-18
> **darkod said:**
> You can't mount a new disk directly to a folder that is not empty.Well, the mount point wouldn't have anything in it.  If it did, I'd simply move it temporarily until I mounted it...if possible.

> **darkod said:**
> What do you mean by "destroy the LVM"? You can add a new disk (PV) to the LVM, extend the LV and filesystem onto it. Then when finished, you can shrink the filesystem, remove the used extents from that PV (if any) and at that point you can safely remove it from the LVM.

That sounds like what you require. You are not destroying the whole LVM, just removing used extents and removing one PV.If the PV can be added to increase the storage capacity and later isolated and shrunk without messing anything up, that would be great option.  I have not done that before so I'm a bit leary to try it...at least on the production box.  I'll do some research on it and figure it out.  When I get it worked out, I'll update my tutorial pages to include how to do that as well since that sounds like something every admin should know.

Thanks for pointing me in the right direction.
LHammonds

EDIT:
Step 1 - Show physical volumes and how much space is used and free on each. (Need room to move data off the PV you want to disconnect)
```
pvs -o+pv_used
```
Step 2 - If there is room, specify the physical volume to move which will spread the data to the other PVs in the VG
```
pvmove /dev/sdc1
```
Step 3 - Remove the PV from the VG (which should have 0 space used if you run Step 1 again)
```
vgreduce LVM /dev/sdc1
```

Reference page: [RedHat Logical Volume Manager Administration](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/5/html/Logical_Volume_Manager_Administration/disk_remove_ex.html)

---

### Post by TheFu on 2017-07-20
> You can't mount a new disk directly to a folder that is not empty

Actually, you can.  It is just that all files and subdirs previously there would be hidden.

For a temporary use, I wouldn't bother with LVM.  Just remove any files from Downloads/ that you want to access before the temporary storage is removed.  Then directly mount the formatted partition to the Downloads/ directory and chown + chmod to what you need.   Use it for a few weeks.  Remove it when all done.  Be happy.

No need for LVM.

If you backup the Downloads/ directory, it might be worth excluding it from backups during this higher use period.

---

