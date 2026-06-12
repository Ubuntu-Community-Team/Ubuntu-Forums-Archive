---
title: "Encrypted partition mount by users"
date: 2013-05-21
forum: Security
---

### Post by Gelembjuk on 2013-05-21
Hello,
I created  encrypted partition on my Ubuntu 11.10.
I followed these instructions
[http://blog.creonfx.com/linux/how-to-encrypt-partition-under-ubuntu-11-10](http://blog.creonfx.com/linux/how-to-encrypt-partition-under-ubuntu-11-10)

but it works little different then i wanted. It mounts the partition on boot. I don't need this. I need it is mounted when a user needs it. And other problem it is not writable for users Only for root.

If i comment that line in /etc/fstab then the partition is not mounted on boot. then i can mount it as non root user. but it is not mounted to /media/cryptname . it is mounted to some long code name /media/xxxx-xxxxxx-xxxxxx... 
And it is not writable to a user. only to root

So my question is:
1. How to mount it to /media/cryptname(to the folder i want) but on user's request, not on boot .
2. How to make it writable for non root users.

Thanks.

---

### Post by Ranko Kohime on 2013-05-21
Add the following to the mount options for that partition in /etc/fstab

```
noauto
```

And uncomment it.  It will now stay unmounted, but it should show up as mountable in the file manager.

ETA: to expand on that, where it says "defaults" now, you want:

```
defaults,noauto
```

---

### Post by Gelembjuk on 2013-05-21
> **Ranko Kohime said:**
> Add the following to the mount options for that partition in /etc/fstab

```
noauto
```

And uncomment it.  It will now stay unmounted, but it should show up as mountable in the file manager.

ETA: to expand on that, where it says "defaults" now, you want:

```
defaults,noauto
```

I already tried this and it doesn't work as expected.
If i add noauto then it behaves with same way as it is commented at all.
If there is noauto then the device is not mounted. And it is visible on filemanager. i mount it but it is not mounted to the folder configured on fstab. it is mounted to auto created folder with long code name. and a user can not write to it
I also tried with defaults,noauto,user . This also doesn't help and a user can not write.


Other strange this is taht when i try to mount as root with
```
mount /media/cryptname
``` 
i see the error
```
mount: special device /dev/mapper/cryptname does not exists
```

maybe the problem is somehow related to the file /etc/crypttab? In other tutorials i didn't found this file is used when configure encrypted partitions.

---

### Post by Ranko Kohime on 2013-05-21
Ahh, yes.  /etc/crypttab must be filled in, or nothing can happen automatically.  I don't know why tutorials would omit that, unless they were dealing with transient drives.

Anyway, the crypttab format is like so:

```
$DRIVE_NAME /dev/disk/by-uuid/$UUID $KEYFILE $ENC_TYPE
```
Where $DRIVE_NAME is whatever name you feel like giving it, which will show up the decrypted drive to mount in /dev/mapper/$DRIVE_NAME.  That path is what you would use in /etc/fstab in place of, say, /dev/sdb1.

$UUID is obviously the UUID of the encrypted partition.

$KEYFILE and $ENC_TYPE are optional, and to the best of my knowledge, not used when the password is user-supplied at mount time.  But if, like me, you're using a keyfile to automate unlocking when it's requested, you would then specify the full location of the keyfile, and the encryption type.

---

