---
title: "Luks Encryption"
date: 2009-04-26
forum: Security
---

### Post by mist_01 on 2009-04-26
I am trying to set up a luks encrypted file system such that it mounts at boot.  I have created the partition and filesystem, but I cannot get it to mount at boot.  

Here is my /etc/crypttab:
secure /dev/sdb2 none luks,check=ext3,retry=1

Here a line from /etc/fstab: (**** is my username)
UUID=3acc971d-2087-4f5e-aced-64508769f28a /home/****/secure ext3 defaults 0 0

And here is my /etc/modules:
lp
dm-mod
dm-crypt
sha256
aes-i586


The problem seems to be with crypttab.  After boot, secure is not listed under /dev/mapper.  I can maually open it with the command "sudo cryptsetup luksOpen /dev/[your device] name" and then mount it.  However, I would like this to work on boot.  Any ideas?

Thanks for the help!

---

### Post by nunki on 2009-04-26
Your fstab should list the mapper name
```

/dev/mapper/secure /home/****/secure ext3 defaults 0 0

```

---

### Post by mist_01 on 2009-04-26
I have changed that, but I still have a problem since /dev/mapper/secure does not exist.  I can manually make it, but everytime I reboot, I lose it.

---

### Post by unutbu on 2009-04-26
Find the UUID of /dev/sdb2:
```

sudo cryptsetup luksDump /dev/sdb2 | grep UUID

```
Edit /etc/crypttab:

```
secure /dev/disk/by-uuid/3acc971d-2087-4f5e-aced-64508769f28a none luks
```

Make sure 3acc971d-2087-4f5e-aced-64508769f28a matches the UUID reported by the "cryptsetup luksDump" command.

Edit /etc/fstab:
```

/dev/mapper/secure /home/****/secure ext3 defaults 0 2 

```

---

### Post by mist_01 on 2009-04-26
I got it working. The last few changes did it.  Thank you to both of you.

God Bless,
Mist_01

---

