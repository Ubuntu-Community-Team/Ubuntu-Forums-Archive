---
title: "Decrypt home directory from mounted and chrooted hard drive"
date: 2015-11-30
forum: Security
---

### Post by markfaine on 2015-11-30
I upgraded my SSD to 512 from 256 but the original SSD was entirely LUKS encrypted, including the home directory.

I was able to successfully mount the ubuntu root volume group  by following instructions [here]("http://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line").
I was then able to chroot into that volume group by following instructions [here]("http://superuser.com/questions/111152/whats-the-proper-way-to-prepare-chroot-to-recover-a-broken-linux-installation").

However, when I do sudo su - <username>, and then attempt ecryptfs-mount-private, I get an error: 

open: permission denied

and the home directory is still encrypted.  At this point, I'm tempted to take the laptop apart again, install the old hard drive, boot it and copy the home directory to another drive.  I was hoping to avoid that since it's tedious, physical work requiring a lot of manual dexterity which is in short supply with me these days.

---

