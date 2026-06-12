---
title: "How can I mount a backup of an encrypted home folder?"
date: 2016-01-25
forum: Security
---

### Post by macho3 on 2016-01-25
How can I mount a copy of the encrypted data in my home directory? What I'm getting is:

```
$ mount.ecryptfs $copy_of_encrypted_home/.Private /mnt/test
Exiting. Unable to obtain passwd info
```

How can I  provide my password (or  regenerate and provide a passphrase from my password) to decrypt and mount the data? If I should in fact be using some other command, e.g., ecryptfs-recover-private, how do I do so?

In case the broader context of why I want to do this is relevant, I just want to reassure myself that I can in fact mount the copy, which is on an external USB drive, should some unforeseen horror befall  the original system. I've backed up the whole  system to the drive as follows:

```
# rsync -avq --one-file-system / $dest_path_on_external_usb_drive
```

I figure this is  a dead-simple complete backup strategy that I can incrementally add to, and that the USB drive remains no more compromising than the original system  itself.

---

### Post by macho3 on 2016-01-28
I seem to have gotten this to work using ecryptfs-recover-private

It will ask for  your mount password, which if (like me) you foolishly  didn't save, you can recover by running ecryptfs-unwrap-passphrase and passing it your wrapped passphrase, which is in ~/.ecryptfs/wrapped-passphrase

---

