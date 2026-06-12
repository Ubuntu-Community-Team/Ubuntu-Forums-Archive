---
title: "CryptSetup--default-encryption-strength?"
date: 2005-05-02
forum: Server Platforms
---

### Post by StartMenu on 2005-05-02
Ok, here's what I'v done:
(from [http://www.ubuntulinux.org/wiki/EncryptedFilesystemHowto](http://www.ubuntulinux.org/wiki/EncryptedFilesystemHowto))
_____________
sudo apt-get install cryptsetup
sudo su -  (to make yourself root)
echo aes >> /etc/modules
echo dm_mod   >> /etc/modules
echo dm_crypt >> /etc/modules
sudo cryptsetup -y create crypt /dev/hda7
sudo su - (do this as root) 
echo "crypt /dev/hda7" >> /etc/crypttab
echo "/dev/mapper/crypt /crypt reiserfs defaults 0 1" >> /etc/fstab
sudo mkfs.reiserfs /dev/mapper/crypt
sudo mount /crypt
____________________

and from there i now had a working partition that required a pw to login at boot (it prompted me for a pw in that install process)

I did some snooping around trying to figure out what exactly I was encrypting the partition with and it seems the aes algorithm is the default, but i was still currious as to the bit length (cipher strength)... so here's my question -- derived from the file /proc/crypto:

??**Why does it say min keysize 16/max keysize 32 -- to my knowledge that is extremely low**??

Could it be that this is just a requirement for my password length and the default cripto key length is 128 or 256? If you know which please enlighten me.

for reference, here is my file data:
 GNU nano 1.2.4                    File: crypto
name         : md5
module       : kernel
type         : digest
blocksize    : 64
digestsize   : 16

name         : aes
module       : aes_i586
type         : cipher
blocksize    : 16
min keysize  : 16
max keysize  : 32

Thank You muchly!

---

### Post by StartMenu on 2005-05-02
Well learned what it was before any of you could post, so I'll just answer it myself for the google cache..

crypsetup --help


"-s, --key-size=BITS         The size of the encryption key (default: 256)"

---

### Post by LordHunter317 on 2005-05-05
[QUOTE=StartMenu]Well learned what it was before any of you could post, so I'll just answer it myself for the google cache..

crypsetup --help


"-s, --key-size=BITS         The size of the encryption key (default: 256)"[/QUOTE]
 The keysize in the file is apparently in bytes.  16*8 = 128 and 32*8 = 256.

---

