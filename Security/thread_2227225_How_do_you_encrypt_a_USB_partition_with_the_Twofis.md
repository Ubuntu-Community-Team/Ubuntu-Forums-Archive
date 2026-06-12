---
title: "How do you encrypt a USB partition with the Twofish cipher and SHA-512 hash?"
date: 2014-05-31
forum: Security
---

### Post by Tony_Sharp on 2014-05-31
Using something other than TrueCrypt.

I've been trying to string together the right flags in cryptsetup:

```
cryptsetup -y -h sha512 -c twofish-xts-plain64 -s 512 luksFormat /dev/sdx
```

But it hasn't been working. When I enter the code listed above, nothing happens; it doesn't even prompt me for a password. Trying this code with aes-xts-plain64 doesn't work either. Perhaps I'm doing something wrong? Or maybe there's a different program I could try. At this point I'd be willing to try anything.

---

### Post by Chayak on 2014-05-31
Truecrypt 7.1a is still perfectly safe to use.  Another group has already picked up the project and will continue development, and the code audit on 7.1a has shown no significant flaws so far.

---

### Post by Tony_Sharp on 2014-05-31
> **Chayak said:**
> Truecrypt 7.1a is still perfectly safe to use.  Another group has already picked up the project and will continue development, and the code audit on 7.1a has shown no significant flaws so far.
Thank you for the reply.

TrueCrypt is probably fine, but I'm still curious about the alternatives.

Someone on reddit mentioned a program called [tcplay]("https://github.com/bwalex/tc-play"). I used the following command to create the partition I wanted.

```
tcplay -c -d /dev/sdx -a SHA512 -b TWOFISH-256-XTS
```

tcplay is essentially a TrueCrypt clone, and is available in the Ubuntu repositories. -c tells tcplay to create a new volume. -d specifies device. -a specifies hash. -b specifies cipher.

If tcplay gives you problems, you can use the gnome-disk-utility (listed as Disks in the programs menu) to create a quick LUKS + Ext4 partition.

[Here's a helpful tutorial]("http://kasunc.blogspot.com/2013/12/usb-flash-drive-encryption-with-luks.html").

---

