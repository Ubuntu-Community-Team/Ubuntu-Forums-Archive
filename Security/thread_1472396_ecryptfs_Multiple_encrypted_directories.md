---
title: "ecryptfs: Multiple encrypted directories"
date: 2010-05-04
forum: Security
---

### Post by broseman on 2010-05-04
hi folks.

Could someone help me with multiple encrypted directories (via ecryptfs)? I just installed lucid (and therefore got an encrypted $HOME) but still has an encrypted Private on a separate partition, which I need to use as well.

mount -i OLDPRIVATEDIR

gives me "Mount point does not exist"

But i can mount the old Private with "sudo mount -t ecryptfs OLDPRIVATEDIR"

Now I need to auto-mount the old Private -- besides auto-mounting my new $HOME.

Thanks for your help.

---

### Post by broseman on 2010-05-06
Please,

could someone give me a hint?

Thanks a lot!

---

### Post by broseman on 2010-05-07
Ok, here is what I found out:

Multiple encrypted directories are not yet implemented in ecryptfs.
However, there is kind of a workaround:

1. Editing /etc/fstab for mounting the separate partition:

```
UUID=<the-uuid-of-your-device>       <mount point>    ext3    defaults        0       2
```

2. Editing /etc/fstab for mounting the Private directory

```
<encrypted folder, i.e. .Private> <mount point, i.e. Private> user,noauto,rw,ecryptfs_sig=<the-used-signature>,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs 0 0
```

3. Starting a bash-script after login

/home/<user>/.decryptPrivate.sh
```
#! /bin/sh
printf "%s" <your mount passphrase> | ecryptfs-add-passphrase -
mount -i <mount point as stated in the fstab>
```

You could start this bash script via "system" < "preferences" < "start programms"

Please note: **This is obviously a security issue!** You will have your holy mount passphrase readable in your home directory. Since your home directory is encrypted this could be ok for you, but i do not recommend this workaround.


Thanks for listening

broseman

---

