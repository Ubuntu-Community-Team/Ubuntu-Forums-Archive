---
title: "Change encrypted ZFS password, no reset needed?"
date: 2023-11-07
forum: Security
---

### Post by madeline-s on 2023-11-07
I had accidentally revealed my password and doxxed myself when I was showing an error on the social media I was using. I have a need to change my password for my disk encryption on Ubuntu as well as already having reset my password on other services. Is it possible to reset your ZFS encryption without resetting the device?

---

### Post by #&amp;thj^% on 2023-11-07
You will need to know which place the key/passphrase is stored:
```
cat /etc/crypttab
```
Then to add a new one you could use:
```
sudo cryptsetup luksAddKey /dev/sdaX
```
of coruse change "sdax" to the right device.
to remove a " key/passphrase" use:
```
sudo cryptsetup luksRemoveKey /dev/sdaxx
``` 
Now check to be sure at least one slot is shown:
```
sudo cryptsetup luksDump /dev/sdaxx
```
[COLOR="#FF0000"]NOTE: disclaimer if you remove the only key before adding another, you will render your disk inaccessible after rebooting![/COLOR]
Also I remember the keyboard would change layouts so keep a very close eye on that as well.
BACK UP BACK UP BACK UP first.
Good Luck
Maybe I lost you, mine went as follows:
```
sudo blkid | awk -F':' '/crypto_LUKS/{ print $1 }'
/dev/nvme0n1p2
/dev/nvme0n1p2
/dev/zd0

```
So my LUKS is "/dev/zd0" now i add my new passphrase:
```
sudo cryptsetup luksAddKey /dev/zd0
Enter any existing passphrase: 
Enter new passphrase for key slot: 
Verify passphrase: 

```
I won't remove the old one until I have a successful unlock.
Check to see if it added the extra key slot:
```
sudo cryptsetup luksDump /dev/zd0 | grep luks2
  0: luks2
  1: luks2

```
To remove the public known key>>>After you have a a good unlock.
```

sudo cryptsetup luksRemoveKey /dev/zd0
[sudo] password for me: 
Enter passphrase to be deleted: 
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> sudo cryptsetup luksDump /dev/zd0 | grep luks2
  1: luks2

```

---

### Post by #&amp;thj^% on 2023-12-13
Courtesy Bump for the OP

---

### Post by MAFoElffen on 2023-12-13
Was your "ZFS Encrypted" installed manually using instructions similar to OpenZFS? Or was it a canned installation from the Ubuntu Desktop installer? That makes a big difference. In how it is encrypted and what needs to be changed, where.

If installed manually, then it could be either a ZFS within a LUKS container, or ZFS native encrypted pools. If from the Ubuntu ZFS Encrypted Install script, then it is actually a hybrid- ZFS native encrypted via a keyfile, but that keyfile is stored within a hidden LUKS container keystore. I know that second one "sounds" more complicated, but is actually fairly easy to deal with. 

1fallen posted the instructions for that hybrid encryption. He asked me if I can explain that in a different way to see if we can guide you though that.

Waiting for your answer to those questions before I go on...

---

### Post by madeline-s on 2023-12-14
It was installed on the Ubuntu installation screen.

---

### Post by #&amp;thj^% on 2023-12-17
> **madeline-s said:**
> It was installed on the Ubuntu installation screen.

You snuck in under my radar LOL
Please show us this:
```
sudo blkid | awk -F':' '/crypto_LUKS/{ print $1 }'
```

---

### Post by MAFoElffen on 2023-12-19
> **1fallen said:**
> You snuck in under my radar LOL

I would say so. I subscribed to this and never got notified. Watching, in case I can be of help.

---

### Post by MAFoElffen on 2023-12-19
I'm just going to go ahead and post it... Hints for an Ubuntu Installer encrytpted, to change the password...

This is what I do:
```

lsblk -e7 -o name,label,size,fstype,type
#NAME             LABEL               SIZE FSTYPE      TYPE
#sr0              Ubuntu 23.04 amd64  4.6G iso9660     rom
#zd0                                  500M crypto_LUKS disk
#&#9492;&#9472;keystore-rpool keystore-rpool      484M ext4        crypt
#vda                                   25G             disk
#&#9500;&#9472;vda1                               512M vfat        part
#&#9500;&#9472;vda2                                 2G crypto_LUKS part
#&#9474; &#9492;&#9472;cryptoswap   cryptoswap            2G swap        crypt
#&#9500;&#9472;vda3           bpool               1.2G zfs_member  part
#&#9492;&#9472;vda4           rpool              21.3G zfs_member  part

sudo su -

cryptsetup luksDump /dev/zd0
#LUKS header information
#Version:           2
#Epoch:             3
#Metadata area:     16384 [bytes]
#Keyslots area:     16744448 [bytes]
#UUID:              326da95c-66bd-4dec-a796-fc58e32e6126
#Label:             (no label)
#Subsystem:         (no subsystem)
#Flags:           (no flags)
#
#Data segments:
#  0: crypt
#    offset: 16777216 [bytes]
#    length: (whole device)
#    cipher: aes-xts-plain64
#    sector: 512 [bytes]
#
#Keyslots:
#  0: luks2
#    Key:        512 bits
#    Priority:   normal
#    Cipher:     aes-xts-plain64
#    Cipher key: 512 bits
#    PBKDF:      argon2id
#    Time cost:  9
#    Memory:     1048576
#    Threads:    4
#    Salt:       1a 43 22 12 87 ba 0a 7c 15 99 90 87 0f f2 7b ec 
#                4f e6 62 77 21 74 15 41 ac c7 30 e7 76 d4 8b a8 
#    AF stripes: 4000
#    AF hash:    sha256
#    Area offset:32768 [bytes]
#    Area length:258048 [bytes]
#    Digest ID:  0
#Tokens:
#Digests:
#  0: pbkdf2
#    Hash:       sha256
#    Iterations: 158299
#    Salt:       40 ff b3 79 e3 ce 82 72 57 13 05 33 e6 a2 b7 86 
#                83 3d b9 e5 5c e6 73 21 2f 63 1d 75 8c 6d 85 7d 
#    Digest:     8f 0b cc 90 30 e2 52 88 c0 cd ce f5 a0 89 61 a1 
#                02 17 b7 9d 17 38 13 59 83 7b fb ac ea 6d 82 e4 
                
cryptsetup luksOpen -v --test-passphrase --key-slot 0 /dev/zd0 && echo correct
#No usable token is available.
#Enter passphrase for /dev/zd0: 
#Key slot 0 unlocked.
#Command successful.
#correct

cryptsetup luksAddKey -v /dev/zd0
cryptsetup luksOpen -v --test-passphrase --key-slot 1 /dev/zd0 && echo correct
cryptsetup luksKillSlot /dev/zd0 0

```
The rpool native encrypted keyfile, was not exposed so should not need to be replaced... But at some point, you should probably add another keyphrase to a keyslot as a backup, then mount and backup the keyfile from inside /dev/zd0 to keep locked up somewhere secure, for the just-in-cases.

---

### Post by TheFu on 2023-12-20
The good news is that LUKS encryption is split into 2 pieces.  The data and the header.  The passphrase that humans can handle are for the header only, not the data.  There are 8 slots for the LUKS header, which means you can have 8 different decryption "passphrases" which can be used with different hardware or just by typing them in.

I use 4 different slots for my LUKS encrypted stuff.  2 use different yubikeys in a challenge/response mode, 1 is a very, very, very, long passphrase that I doubt I'd ever be able to type in and the other is a 30 character total static passphrase with 50% of it provided by a device that acts like a keyboard and 50% I have to type in.  All of these can unlock the storage.

So, what you should do is to first add a new passphrase to a different LUKS "slot" and ensure that works.  Be certain you know which slot is used.  Now would be a good time to improve security of the unlock and perhaps add a yubikey too.
After those are working, you can delete the old slot credentials.

If you know what you are doing, this is a 30 second thing.  Those LUKS guys really are brilliant.  If only our password manager people were as smart, I'd be much happier. sigh.

---

### Post by MAFoElffen on 2023-12-20
+1 -- I love LUKS. LUKS1 has 8 keyslots & LUKS2 has 32 keyslots... Lots of things you can do with that.

The one limitation is one for booting with Grub2 2.06. The keyslot for the container that the root resides in has to be pbkdf2, even though LUKS2's default is argon2. There are patches for that but... I don't know that they have been back-ported. It wasn't as of a few months ago.

The keyslots can be left at argon2 if you are using Mantic and newer, that uses Grub2 2.16.

---

