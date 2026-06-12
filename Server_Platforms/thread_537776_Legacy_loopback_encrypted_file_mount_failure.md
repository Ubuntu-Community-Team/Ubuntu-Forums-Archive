---
title: "Legacy loopback encrypted file mount failure"
date: 2007-08-29
forum: Server Platforms
---

### Post by Alexis Phoenix on 2007-08-29
I have an encrypted loopback container file on an external drive, which I created using a Debian system (2.6.something custom kernel) and used with no problems for a long time.
I used to mount it with:
# mount -o loop,encryption=aes crypto.file /mnt/secure
this was very easy and always worked.

On Ubuntu Feisty (my first Ubuntu) I can no longer mount this file as above.  I can attach it to a loop device with losetup:
[FONT="Courier New"]# modprobe aes
# modprobe cryptoloop
# lostetup -e aes /dev/loop0 /home/me/crypto.file
# Password: *(my password)*
# mount -t ext2 /dev/loop0 /mnt/secure* (I have to specify the filesystem now)*
# --- mount gives failure message ---[/FONT]
I check dmesg (as mount suggests) and it says something like "cannot find ext2 filesystem on /dev/loop0"

I tried also 
[FONT="Courier New"]# lostetup /dev/loop0 /home/me/crypto.file
# mount -t ext2 -o encryption=aes /dev/loop0 /mnt/secure
# Password: *(my password)*
# --- mount fails in the same way ---[/FONT]

I want to mount the container on this machine (as the old one is slow) so I can move the data into a more secure LUKS container file but at the moment can't do anything with it.

So can anyone help?  Should I be using cryptsetup for this (and I have only just got my head around the above!)

---

### Post by p_quarles on 2007-08-29
Yeah, cryptsetup is a required step in Ubuntu, I believe. Before I can mount my loopback devices, I enter:
```
sudo cryptsetup create *devicename* /dev/loop0
```
This is, by the way, after losetup and before mount. 

Hope this helps.

---

### Post by Alexis Phoenix on 2007-08-30
Yay!  It works :-)   (with sudo)
Thank you very much :-))

---

