---
title: "freeotfe, luks manager for android. what for linux"
date: 2012-04-30
forum: Security
---

### Post by nutpants on 2012-04-30
freeotfe for windows and luks manager for android are said to work together with the same encrypted container. (are compatible that is). is there anything in ubuntu that will read and write that encrypted container?
(.vol file not a encrypted partition)

thank you for any info.
(everything I have found is about partition encryption)

---

### Post by nutpants on 2012-05-04
there must be someone who can point out how to mount these files in ubuntu..

this is all i have found that might be relevant. 

cryptsetup (and the extended cryptsetup-luks) are valuable tools for performing lower-level configuration of the 'dm-crypt' target through libdevmapper. As yet, these are only directed at raw block devices, **[COLOR="Red"]and would require separate configuration of loopback devices to handle filesystems stored in ordinary files.[/COLOR]**

---

### Post by HermanAB on 2012-05-06
Here you go:
[www.aeronetworks.ca/howtos/LUKS-Mount-FreeOTFE.pdf](www.aeronetworks.ca/howtos/LUKS-Mount-FreeOTFE.pdf)

---

### Post by nutpants on 2012-05-07
Thank you for your effort but the pdf appears to be how to create a encrypted partition on a USB stick that will work both in Linux with luks and freeotfe for windows.

I need to work with the   "whatever.Vol" files that are created with luks manager for Android and are compatible with freeofte for windows.
The file not a partition

But thanks for the effort.

---

### Post by HermanAB on 2012-05-07
You'll have to run some experiments then.  It can be rather time consuming to find a solution so once you figured it out, do write a howto guide for everybody else!

---

### Post by nutpants on 2012-05-07
i have found this..

[http://www.mayrhofer.eu.org/encrypted-container-linux-and-windows](http://www.mayrhofer.eu.org/encrypted-container-linux-and-windows)

I can confirm that a volume created on my android phone with "luks manager"
is mountable in linux and a can write and read files off the container.
the files written from linux were read fine on my android phone. 

i expect that it will work fine with windows.

sudo losetup /dev/loop0 container.bin
sudo losetup -d /dev/loop0

after creating the container in android. i  only need the two commands above to mount the loop-back device. ( and to unmount it) when i clicked on the mount (in ubuntu 11.04) in nautilus ubuntu recognised it as encrypted and asked for a password.. it was all auto magically working from that point

so this should work fine for windows - ubuntu - android  might even work for mac.

if i have any issues with 12.04 lts tonight when i get home ill post them
but for now im marking this solved.

(the file created in ubuntu was not recognised in android so i could not mount it it might have to do with the settings from the web page(or a bug in luks manager))

---

### Post by idnael on 2012-06-23
hi nutpants

I also want to mount in Linux a luks file volume I created with LuksManager for android.


dd if=/dev/urandom of=/tmp/container.bin bs=1024 count=20000
sudo losetup /dev/loop2 /tmp/container.bin
sudo cryptsetup -c aes -s 256 --verify-passphrase luksFormat /dev/loop2

sudo cryptsetup luksOpen /dev/loop2 container

here I have this error:
Device /dev/loop2 is not a valid LUKS device.

how did it work for you?

---

### Post by rookcifer on 2012-06-24
> **idnael said:**
> here I have this error:
Device /dev/loop2 is not a valid LUKS device.

how did it work for you?

Because you don't have a loop2 device.  Try using loop0.

And, OP, LUKS is not an Android thing, it is a Linux thing (Android is Linux).

---

### Post by idnael on 2012-06-24
hi

I tried again and it worked!
thks


I wrote this shell script to mount and dismount the volumes as separate calls, instead of the "Press any key to unmount" used in mayrhofer script:



#!/bin/bash

# daniel jun 2012

if [ "$1" == "-h" ]; then
  cmdname=`basename $0`
  echo "Usage $cmdname containerfile mountpoint"
  echo "or    $cmdname -u containerfile"
  exit 1
fi

if [ `id -un` != "root" ]; then
  echo "Not executed as root, re-executing myself with sudo...."
  exec sudo bash $0 "$@"
fi

if [ "$1" == "-u" ]; then
  montar=
  shift
else
  montar=1
fi

CONTAINERFILE="$1"
LOOPNAME=crypted_`basename $CONTAINERFILE`

if [ $montar ] ;
then
  MNTDIR="$2"
  
  # see a free device, as /dev/loop0
  LOOPDEV=`losetup -f`

  losetup "$LOOPDEV" "$CONTAINERFILE"

  cryptsetup luksOpen "$LOOPDEV" "$LOOPNAME"

  # use the current user as owner of the files
  mount -t vfat -o nodev,noexec,nosuid,uid=$USER,gid=$USER,umask=007,codepage=850,iocharset=iso8859-15,shortname=mixed,quiet /dev/mapper/"$LOOPNAME" "$MNTDIR"

else

  # see the  loopdev used by calling losetup -a
  # The output is something like
  # /dev/loop0: [0014]:411020 (/home/daniel/container.bin)
  LOOPDEV=`losetup -a | grep $CONTAINERFILE | cut -d: -f1 `

  # See the mount point that is being used
  # The output of mount is like
  # /dev/mapper/cryptedContainer on /home/daniel/luksteste type vfat (rw,noexec,nosuid,nodev,uid=1000,gid=1000,umask=007,codepage=850,iocharset=iso8859-15,shortname=mixed,quiet)
  MNTDIR=`mount | grep "$LOOPNAME" | cut -f1 -d" "`

  umount "$MNTDIR"
  cryptsetup luksClose "$LOOPNAME"
  losetup -d $LOOPDEV

fi

---

