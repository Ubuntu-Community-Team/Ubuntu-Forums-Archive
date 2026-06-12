---
title: "cryptoloop support in 16.04"
date: 2016-12-11
forum: Security
---

### Post by crankycyclops on 2016-12-11
Hi,

I created a blowfish encrypted loopback device in Ubuntu 14.04 like so:

sudo dd of=backups.loopback bs=1G seek=775 count=0 (for a sparse file that would grow as I added files)
sudo modprobe cryptoloop
sudo losetup -e blowfish /dev/loop0 backups.loopback

I then created an ext4 filesystem on /dev/loop0.

Later on, whenever I rebooted, I could mount this like so:

mount -o loop,encryption=blowfish /backups.loopback /mnt/backups

Now, in Ubuntu 16.04, this no longer works.

I've heard that I can mount this via cryptsetup, which is backward compatible with cryptoloop, but I have yet to make this work. Can anyone help me out? Thank you!

---

### Post by crankycyclops on 2016-12-11
I solved this. I hope it helps someone else. I have to issue the following commands:

sudo losetup /dev/loop0 /backups.loopback
sudo cryptsetup create -c blowfish backups /dev/loop0
sudo mount /dev/loop0 /mnt/backups

Would be nice to still be able to do this in one command instead of 3, but the important thing is I can access my data :)

---

### Post by ajgreeny on 2016-12-11
Great! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by HermanAB on 2016-12-11
Err... AFAIK, cryptoloop is not secure.  Maybe someone fixed it recently, but you should check it.

---

