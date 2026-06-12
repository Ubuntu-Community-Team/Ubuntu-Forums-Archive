---
title: "Random Mounts"
date: 2010-08-08
forum: Server Platforms
---

### Post by ptmuldoon on 2010-08-08
I have Ubuntu Server installed on a VIA NNS7800, that has builtin compact flash and and 8 drive sata bay.  Ubuntu is installed on the CF, using the sata drives for NAS storage.

My problem is that when the system boots, it keep changing the order of the drives being mounted.  In one instance, the CF card is sda, with the sata drives sdb -sde.

Then on another reboot, the CF is mounted as sde, with the sata drives given sda - sdd.

How can you permanently assign the drives so that they mount properly each time during boot up?

---

### Post by CharlesA on 2010-08-08
You can set it to mount using the UUID in fstab so that it doesn't matter if the drives are assigned the same sdxy designation.

You can find the UUID by running this:

```
sudo blkid /dev/sdxy
```

To add it to fstab just replace the /dev/sdxy with UUID in fstab:

```
UUID=05c730b5-680d-4d33-8e2e-76947d7a93fa       /array  ext4    noexec  0       0
```

---

### Post by ptmuldoon on 2010-08-09
Thanks

This is likely pretty silly/easy.   But after learning the UUID of each drive.  How do you copy and paste that info from a shell command?

Unbuntu Server doesn't use a graphical interface, and I can't quite figure out how to scroll back and highlight text in the shell to copy it to paste into fstab.

---

### Post by CharlesA on 2010-08-09
Just dump it into a file, then sort it later.

Example:

```
sudo blkid /dev/sdxy >> ~/uuid
```

You'd need to drop to a root shell to add them to /etc/fstab.

---

