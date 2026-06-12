---
title: "encrypted ZFS - How can I autounlock with a keyfile?"
date: 2022-03-22
forum: Security
---

### Post by qupfer2 on 2022-03-22
Hi,

I have an 21.10 installation with ZFS and Disk Encryption. I want to disable the encryption for a while (just remote access). 
On my previous machiens (arch with btrfs) I just add the keyfile to luks and to the boot cmdline and I'm fine. This is obviously not possible with ZFS. 

Did anyone now, how to achive that? 
What I already try:

[LIST]
[*]create keyfile: dd if=/dev/urandom of=/boot/boot.key bs=1024 count=4
[*]add it to zd0: cryptsetup luksAddKey /dev/zd0 /boot/boot.key
[*]use blkid to get UUID of ZD0 (0b3f3e27-8270-4030-b4d5-6ad337dfb57d)
[*]add it to /etc/crypttab: keystore-rpool	UUID="0b3f3e27-8270-4030-b4d5-6ad337dfb57d"	/boot/boot.key	luks,discard,initramfs
[*]re-generate initramfs: update-initramfs -u -k all
[/LIST]


If I extract the initram, I find /cryptroot/crypttab and /cryptroot/keyfiles/keystor-rpool.key in it. 
The initramf-crypttab looks like: keystore-rpool UUID="0b3f3e27-8270-4030-b4d5-6ad337dfb57d" /cryptroot/keyfiles/keystor-rpool.key luks,discard

But if I reboot, I still get asked for the Password for device 0b3f3e27-8270-4030-b4d5-6ad337dfb57d. I entered 3 times a wrong one to get into the initram-shell and take a look.
 /cryptroot/keyfiles/keystor-rpool.key still exist, but the crypttab is an other. It contains now: keystore-rpool /dev/zvol/rpool/keystore none luks,discard

What did I wrong/forget?

Thanks

---

### Post by qupfer2 on 2022-03-23
Solved in a dirty way:

create file "[COLOR=#000000][FONT=&amp]/etc/initramfs-tools/hooks/rpool_key_copy.sh" and make it executable. 
[/FONT][/COLOR]
```
#!/bin/sh
cp /boot/boot.key $DESTDIR/rpool.key

```

and the dirty part, modify the original "[COLOR=#000000][FONT=&quot]/usr/share/initramfs-tools/scripts/zfs" and change

[/FONT][/COLOR]```

#original: echo "keystore-${pool} ${ks} none luks,discard" >> "${TABFILE}"
echo "keystore-${pool} ${ks} /${pool}.key luks,discard" >> "${TABFILE}"

```

---

### Post by CharlesA on 2022-03-25
As a stupid question - why not set up dropbear and unlock it via SSH with a keyfile since you have remote access only?

Some info here:
[https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2020.04%20Root%20on%20ZFS.html](https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2020.04%20Root%20on%20ZFS.html)

---

