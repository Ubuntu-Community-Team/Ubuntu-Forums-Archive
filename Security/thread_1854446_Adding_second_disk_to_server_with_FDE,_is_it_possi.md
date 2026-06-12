---
title: "Adding second disk to server with FDE, is it possible?"
date: 2011-10-04
forum: Security
---

### Post by 0x01 on 2011-10-04
Good morning all,

I currently have an Ubuntu Server (11.04) that was configured with FDE at install time.

I wonder if anyone would have any suggestions as to how or whether it is possible to add a second hard drive after the fact, preferably so that it gets mounted at boot time along with the first drive?

Most of the solutions I've found pertain to the use of truecrypt and pre-date the inclusion of FDE in the installer.

tia.

---

### Post by lcman on 2011-10-05
Just plug in the drive, partition, format, encrypt and add it in your fstab

---

### Post by 0x01 on 2011-10-24
> **lcman said:**
> Just plug in the drive, partition, format, encrypt and add it in your fstab

Have been playing around with this having followed a couple of tutorials and it mostly work, still have to get automounting on boot working but I think that's just due to a missing /etc/crypttab entry.

I do have one more question though if any one feels like fielding it.   Looking at the tutorials they differ slightly in what they suggest encrypting.

In [one]("http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/")  it suggests encrypting /dev/sdb  where as the [other]("http://www.hermann-uwe.de/blog/howto-disk-encryption-with-dm-crypt-luks-and-debian") it suggests encrypting /dev/sdb1.  I know with the former it should look like an empty disk where as the latter will look like an empty partition.   

 Is there any benefit or risks of doing one over the other (currently have /dev/sdb encrypted)

---

