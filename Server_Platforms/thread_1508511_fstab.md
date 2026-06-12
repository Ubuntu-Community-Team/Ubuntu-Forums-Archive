---
title: "fstab"
date: 2010-06-13
forum: Server Platforms
---

### Post by davidmaxwaterman on 2010-06-13
Hi,

I have a couple of lines in my fstab that mount two file systems, one on a 1TiB disk and another on an md raid5 array on 6 disks.

Last night, when I tried to boot it, it failed with some XFS error and it just hung there. Nothing I tried could make it boot.

This morning, I unplugged the disks on the array and the single disk, and that allowed it to boot. I thus commented out the lines in fstab, shutdown, plugged the disks back in, and then rebooted. That worked fine.

Now I can see that my array is rebuilding.

My question is: how can I specify in fstab that it should continue to boot if the array fails to mount for some reason?

I was thinking of something like the 'bg' option, but that seems to be for nfs mounts.

Thanks,

Max.

---

