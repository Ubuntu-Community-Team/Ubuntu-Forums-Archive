---
title: "how do I encrypt / ??"
date: 2008-05-15
forum: Security
---

### Post by zenkaon on 2008-05-15
Hello, I have ubuntu 8.04 working lovely. I have 4 partitions:

/                    
swap                
/fat32               
/windowsXP           

I use the fat32 drive to hold mp3s so I can play them from both Linux and Windows.

How do I go about encrypting my ext3 / and swap partitions?

Is it possible to encrypt the fat32 partition in a way that windows can read, if I give it the correct password?

I really don't want to have to re-install everything.

Thanks in advance for any help

---

### Post by jimv on 2008-05-15
I'm pretty sure that you can't encrypt / without switching to an encrypted filesystem or something....like Encrypted LVM during installation.

I mean, if you encrypted /, how would the machine boot?

Granted, I've never messed with encryption much, so I'm just conjecturing.

---

### Post by p_quarles on 2008-05-15
To encrypt the whole disk, you need to create a small, separate partition for the /boot directory. GRUB can read from that, then ask for your LUKS passphrase to read the encrypted volume. 

The guide that I used:
[http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html](http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html)

---

### Post by sphim on 2008-05-15
If you just want to encrypt specific files/folders, you could look at truecrypt, which is cross platform(OS X/Windows/Linux) and even has full disk encryption for windows (but not linux).
[http://www.truecrypt.org/](http://www.truecrypt.org/)

---

### Post by hyper_ch on 2008-05-16
> **zenkaon said:**
> How do I go about encrypting my ext3 / and swap partitions?
Easiest to encrypt upon installation...

> **zenkaon said:**
> Is it possible to encrypt the fat32 partition in a way that windows can read, if I give it the correct password?
Yes, use truecrypt... and maybe even use ntfs instead of fat32

> **zenkaon said:**
> I really don't want to have to re-install everything.
With full encryption you'll have to...

---

### Post by zenkaon on 2008-05-16
forgive me for being as blind as a bat, where can I find a url for a copy of the Alternative ubuntu 8.04 cd iso???

I'm actually writing this from the regular download ubutnu 8.04 live cd - it doesn't seem to have encryption install support.

---

### Post by Dr Small on 2008-05-16
[http://releases.ubuntu.com/8.04/ubuntu-8.04-alternate-i386.iso](http://releases.ubuntu.com/8.04/ubuntu-8.04-alternate-i386.iso)
[http://releases.ubuntu.com/8.04/ubuntu-8.04-alternate-i386.iso.torrent](http://releases.ubuntu.com/8.04/ubuntu-8.04-alternate-i386.iso.torrent)

```
166991d61e7c79a452b604f0d25d07f9 *ubuntu-8.04-alternate-i386.iso
```

I recommend downloading it via torrent.

---

### Post by hyper_ch on 2008-05-17
> **Dr Small said:**
> I recommend downloading it via torrent.
So do I as it will be automatically hash checked and hence you are sure that the downloaded .iso is ok.

---

### Post by zenkaon on 2008-05-17
cheers guys,

downloading via torrent now, will stay as a seeder for a good while.

Looking forward to a nice set of encrypted PCs.

---

