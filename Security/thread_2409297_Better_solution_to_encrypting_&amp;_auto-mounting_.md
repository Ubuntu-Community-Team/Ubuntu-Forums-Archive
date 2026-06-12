---
title: "Better solution to encrypting &amp; auto-mounting secondary drive?"
date: 2018-12-31
forum: Security
---

### Post by Dáire Fagan on 2018-12-31
I have encrypted a 1TB HDD and set it to auto-mount in Ubuntu.

I would like to know if my method below can be done better, more use of the command line and less use of Gnome Disks, and if it can be auto-mounted without storing the passphrase in plaintext, albeit on my encrypted root partition - though if possible, I would like the option be able to fall back on a passphrase in future if the key is lost?

Randomising the disk (aware of overwriting controversy, before this it was recently zeroed, and shredded 3 times on device name - not partition):

```
sudo dd bs=16M if=/dev/urandom of=/dev/sdc
```

Create a new empty GPT partition table, and write table to disk and exit:

```
sudo fdisk /dev/sdc
g
w
```

Create partition, show info, and write changes to disk and exit:

```
sudo fdisk /dev/sdc
n # all defaults accepted
p
w
```

Encrypt:

```
sudo cryptsetup -v -y -c aes-xts-plain64 -s 512 -h sha512 -i 5000 --use-urandom luksFormat /dev/sdc1
sudo cryptsetup luksOpen /dev/sdc1 friendlyname
mkfs.ext4 /dev/mapper/friendlyname

```

Auto-mounting and naming:

In Gnome Disks, with LUKS open, I selected the visible Ext4 partition, the *Cog icon* for *Additional partition options* and *Edit Filesystem...* then I set the label to friendlyname.

I then selected *Edit mount options*... and set it as so before rebooting:

[ATTACH=CONFIG]282058[/ATTACH]

This added a line to /etc/fstab:

```
/dev/disk/by-uuid/<actual UUID> /mnt/friendlyname auto nosuid,nodev,nofail,x-gvfs-show 0 0
```

And it added the following to /etc/crypttab:

```
friendlyname UUID=<actual UUID> /etc/luks-keys/friendlyname nofail
```

Set permissions:

```
sudo chown -R dusf:dusf /mnt/friendlyname/
```

---

### Post by TheFu on 2019-01-03
Seems reasonable, assuming it all works. Multiple zero and shredding seems overkill unless you are tied to DoD mandates. Once with random data prior to creating the dmcrypt block is more than sufficient, IMHO.

LUKS can hold 8 decryption keys. Add and remove them by "slot" using cryptsetup.  The manpage is pretty clear about it.

If you don't want to be prompted to enter the key at boot, what is the point?  If it automatically decrypts, what is the security?  
Maybe placing the decryption key onto flash storage which you connect during boot, but remove immediately would be an option?  [https://askubuntu.com/questions/839288/unlocking-luks-partition-with-keyfile-on-usb-does-not-work](https://askubuntu.com/questions/839288/unlocking-luks-partition-with-keyfile-on-usb-does-not-work) has more discussion about this.

I don't use the flash storage method myself.  Use 2FA to decrypt my laptop.  A passphrase followed by some very long input from a hardware device which requires a physical button press. The device appears to be a USB keyboard.

I would only mount storage under /mnt/ if it was temporary and for administration use.  Mounts that are effectively permanent belong elsewhere according to the file system hierarchy standards. Following standards is good.

---

