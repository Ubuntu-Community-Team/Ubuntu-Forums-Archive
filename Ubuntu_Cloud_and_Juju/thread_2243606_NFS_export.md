---
title: "NFS export"
date: 2014-09-10
forum: Ubuntu Cloud and Juju
---

### Post by MakOwner on 2014-09-10
I want a single NFS export from an Ubuntu 14.04 LTS server.
Everything I have done so far still results in clients being denied mounts from the server.
 
I need a single, simple NFS export and NFSv3 will be more than sufficient.  It just seems wrong to have to fight this hard for something that in version prior to 12.04 worked out of the box.

Anyone have any clues or am I just wasting my time?

---

### Post by SeijiSensei on 2014-09-10
Try forcing version 3 on the client with the "vers=3" option.  You can put it in the list of options in /etc/fstab or in the mount command itself:
```
mount -o vers=3 server:/share /mount/point
```

---

### Post by MakOwner on 2014-09-10
> **SeijiSensei said:**
> Try forcing version 3 on the client with the "vers=3" option.  You can put it in the list of options in /etc/fstab or in the mount command itself:
```
mount -o vers=3 server:/share /mount/point
```

the fstab entry already looks like this:

```

nfs-server:/export 	/mnt/export 	nfs 	ro,vers=3,addr=192.168.nn.nn

```

mount -a results in a "stale mount" and I see NFSv4 errors.

Wrong server information -- oops.
Same stuff, but with ver=3 instead fo ver=4 as I first posted.

---

### Post by SeijiSensei on 2014-09-10
In my experience a stale mount can only be cleared by a reboot.

---

### Post by papibe on 2014-09-10
> **SeijiSensei said:**
> In my experience a stale mount can only be cleared by a reboot.
I've had some success forcing the unmount on the client (umount -f), and stopping and restarting the NFS service on the server.

Just a thought.
Regards.

---

### Post by MakOwner on 2014-09-10
The stale mount isn't the issue - I regardless of how it's cleared whether it's via forced dismount or a reboot, I still can't mount via NFSv3.

---

