---
title: "home encryption of user home as file - using loop back"
date: 2009-06-01
forum: Security
---

### Post by nicolasdiogo on 2009-06-01
hi,

i am looking for information on how to setup home encrypted to users but instead of using partitions as described here:
[http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu]("http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu")

i would like to use encrypted files - so i image that i would need to mount these files in a loop.

the advantages that i seek is to be able to have various files (one for each user of the system) sharing a large partition but without forcing size restrictions on any individual user.

does anyone know of articles around these topics?

thanks a lot,


NIcolas

---

### Post by Agent ME on 2009-06-01
You might want to check out Ecryptfs. It encrypts files individually on the parent file-system, but mounts another folder where they are transparently accessible and encrypted automatically.

Run "ecryptfs-setup-private" and it will setup the "Private" folder, which is mounted when you log in automatically and unmounted when you log off.

---

### Post by nicolasdiogo on 2009-06-02
thanks for the suggestion,

i will have a look at it.

but that option would still leave a problem out how to deal with un-encrypted /tmp

regards

---

### Post by HermanAB on 2009-06-02
Note that /tmp is a RAM disk (tmpfs) and therefore ephemeral.  So when the system is powered down, /tmp is 'clean'.

The LUKS wizards are slowly improving which makes it relatively easy to use.  Have a look at the LUKS howto here: [http://aeronetworks.ca/linux](http://aeronetworks.ca/linux)

---

### Post by Agent ME on 2009-06-04
> **HermanAB said:**
> Note that /tmp is a RAM disk (tmpfs) and therefore ephemeral.  So when the system is powered down, /tmp is 'clean'.
Looking at the output of mount, it looks like you're wrong (at least for people who haven't explicitly set that up). Maybe you're thinking of /dev/shm?

I'm also curious about any ways to automatically encrypt /tmp and swap, with unsaved random keys.

---

### Post by factorgaming on 2009-06-12
hai! i also have same problem the home security is very essential.

---

### Post by rookcifer on 2009-06-12
> **Agent ME said:**
> Looking at the output of mount, it looks like you're wrong (at least for people who haven't explicitly set that up). Maybe you're thinking of /dev/shm?

I'm also curious about any ways to automatically encrypt /tmp and swap, with unsaved random keys.

```

echo swap /dev/sdx SWAP "-c aes-cbc-essiv -h whirlpool -s 512" >> /mnt/etc/crypttab
```

That will encrypt swap with a random key at boot.

However, why not just setup whole disk encryption by using LVM with dm-crypt/LUKS?  You can do it from the alternate CD.

---

### Post by Agent ME on 2009-06-12
> **rookcifer said:**
> ```

echo swap /dev/sdx SWAP "-c aes-cbc-essiv -h whirlpool -s 512" >> /mnt/etc/crypttab
```

That will encrypt swap with a random key at boot.
I have no file named /dev/sdx or /mnt/etc/crypttab; actually, my /mnt directory is empty. (And my understanding of /mnt is that it is like /media, a convenient place to mount file-systems, not a location for config files.) Sure these instructions aren't for a different linux distro?

> **rookcifer said:**
> However, why not just setup whole disk encryption by using LVM with dm-crypt/LUKS?  You can do it from the alternate CD.
Whole disk encryption is pretty useless for a multi-user desktop computer, as all users of it would need the password when turning it on, and the data on swap isn't lost if the same key is used every time.

---

