---
title: "[SOLVED] Full disk encryption and SD Card as token 8.04"
date: 2008-06-28
forum: Security
---

### Post by chunkymonkey on 2008-06-28
Hi everyone,

I'm brand new to ubuntu.  And I haven't managed to find any info on how to use an SD card to store a keyfile.

I've just installed Hardy 64-bit on my ASUS F3Sc laptop.
I wanted to enable full drive encryption and was following a howto by yungchin

[]("http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/")

The author included a link which allowed you to use a keyfile on a usb disk to unlock the system.

[http://wejn.org/how-to-make-passwordless-cryptsetup.html]("http://wejn.org/how-to-make-passwordless-cryptsetup.html") 

Because my laptop has an internal SD card reader.  I thought it would be cooler to store the keyfile on an SD card instead.  It's much less obvious because the card is flush with the case as opposed to the USB disk jutting out.  (Plus the added bonus is that if I go travelling, the SD card won't look out of place if I stick it with(in) my digicam.)

This is my solution to getting the keyfile from an SD card.
(I must point out that I'm still a newbie, so I can't guarantee that this will work with any other card readers or even any other laptops other than my own.  But I hope it'll at least point people in the right direction to get theirs working if they want.)

First you need to add some modules to the ramdisk

```
mmc_core 
ricoh_mmc 
mmc_block 
sdhci  
```

this is done by appending them to end of /etc/initramfs-tools/modules

Next you need to modify the script that is given in 
[http://wejn.org/how-to-make-passwordless-cryptsetup.html]("http://wejn.org/how-to-make-passwordless-cryptsetup.html") 

to mount the SD card and grab the keyfile from that first.

```

#!/bin/sh

# Part of passwordless cryptofs setup in Debian Etch.
# See: http://wejn.org/how-to-make-passwordless-cryptsetup.html
# Author: Wejn <wejn at box dot cz>
#
# Updated by Rodolfo Garcia (kix) <kix at kix dot com>
# For multiple partitions
# http://www.kix.es/
#
# Updated by Cromwel Flores <cromwel dot flores at gmail dot com>
# For MMC/SD card

# Disk partition type (ext2 or vfat)
PARTTYPE=vfat
# Key file in the disk
KEYFILE=root.key

# # # # # CODE # # # # #
MD=/tmp-mount

if [ "x$1" = "x" -o "x$1" = "xnone" ]; then
	KEYF=$KEYFILE
else
	KEYF=$1
fi

USBLOAD=0
FSLOAD=0
MMCLOAD=0
cat /proc/modules | busybox grep usb_storage >/dev/null 2>&1
USBLOAD=$?
cat /proc/modules | busybox grep $PARTTYPE >/dev/null 2>&1
FSLOAD=$?
cat /proc/modules | busybox grep mmc >/dev/null 2>&1
MMCLOAD=$?

#Check if all the required modules have been already loaded
if [ $USBLOAD -gt 0 ] || [ $FSLOAD -gt 0 ] || [ $MMCLOAD -gt 0 ]; then
	modprobe usb_storage 
	modprobe mmc_core 
	modprobe ricoh_mmc 
	modprobe mmc_block 
	modprobe sdhci 
	modprobe $PARTTYPE 
fi

OPENED=0

ls -d /sys/block/sd* >/dev/null 2>&1
SDS=$?

if [ $SDS -eq 0 ]; then
	echo "Trying to get the keyfile from physical keychain ..." >&2
	mkdir -p $MD

# Try getting file from SD Card
	echo "> Looking for keyfile in SD Card ..." >&2
	mount /dev/mmcblk0p1 $MD -t $PARTTYPE -o ro 2>/dev/null

	if [ -f $MD/$KEYF ]; then
		cat $MD/$KEYF
		umount $MD 2>/dev/null
		OPENED=1
	else
		echo "> Could not find keyfile in SD Card ..." >&2
	fi
	umount $MD 2>/dev/null

# Try getting file from USB Device
	if [ $OPENED -eq 0 ]; then
		echo "> Now looking for keyfile in USB disk(s)..." >&2
# Sleep to allow USB drive to be recognised
		sleep 7
		for SFS in /sys/block/sd*; do
			DEV=`busybox basename $SFS`
			F=$SFS/${DEV}1/dev
			if [ 0`cat $SFS/removable` -eq 1 -a -f $F ]; then
				echo "> Trying device: $DEV ..." >&2
				mount /dev/${DEV}1 $MD -t $PARTTYPE -o ro 2>/dev/null
				if [ -f $MD/$KEYF ]; then
					cat $MD/$KEYF
					umount $MD 2>/dev/null
					OPENED=1
					break
				fi
				umount $MD 2>/dev/null
			fi
		done
	fi
fi

# Could not read from physical token.  So ask manual input for passphrase.
# read -s -r PASSPHRASE </dev/console does not display input.
if [ $OPENED -eq 0 ]; then
	echo "> FAILED to find keyfile from a physical keychain ..." >&2
	echo -n "Try to enter your passphrase: " >&2
	read -s -r PASSPHRASE </dev/console
	echo -n "$PASSPHRASE"
	echo -e "\n> Attempting to use provided passphrase ..." >&2
else
	echo "Success loading keyfile from the keychain!" >&2
fi

```

My main contribution to the script is 

```
# Try getting file from SD Card
	echo "> Looking for keyfile in SD Card ..." >&2
	mount /dev/mmcblk0p1 $MD -t $PARTTYPE -o ro 2>/dev/null

	if [ -f $MD/$KEYF ]; then
		cat $MD/$KEYF
		umount $MD 2>/dev/null
		OPENED=1
	else
		echo "> Could not find keyfile in SD Card ..." >&2
	fi
	umount $MD 2>/dev/null


```

The poor bit of code is "/dev/mmcblk0p1" I had to hardcode this in, because I didn't know what it might be called.  This is potentially the stumbling block for everyone else because the device might be called something different on different machines. (I don't understand enough about about ubuntu yet to be sure.)

I hope this helps others.
If anyone else can make my kludge more elegant, please comment. :)

---

### Post by Patsoe on 2008-07-25
Hi Crom, great job! 

> **chunkymonkey said:**
> 
The poor bit of code is "/dev/mmcblk0p1" I had to hardcode this in, because I didn't know what it might be called.  This is potentially the stumbling block for everyone else because the device might be called something different on different machines.


I was browsing around a bit and it seems that indeed the device name is hardware dependent. E.g. [here]("http://gentoo-wiki.com/HOWTO_Multicard_reader") a multicard reader is mentioned that makes SD cards available as /dev/sdc.

Perhaps a manageable approach would be to mount by uuid? (As far as I understand it, the uuid is a randomly generated string that is assigned to a partition at partitioning time, and it uniquely identifies the partition) You could then have the uuid declared at the top of the script, and that would be the only line other users of the script would need to change.

---

### Post by elektronaut on 2009-06-15
I couldn't get this working in 9.04. Is there something that needs to be changed?

---

### Post by chunkymonkey on 2009-06-16
Patsoe:  Yep, UUID would be one way, but it would mean that you'd be stuffed if you lost the particular card that you're using.

Elektronaut:  I haven't managed to get this to work in either Intrepid or Jaunty.  I have a feeling that because they've changed the boot order to make both Intrepid Jaunty boot faster, they've moved things around, which has stuffed this particular method up.

I'm not really an expert in how to do this, I've only adapted other avaliable scripts and how to's that are around.

For the record, I'm still using Hardy and not any of the later releases.

So I have no idea how to get this to work with Jaunty.

---

### Post by elektronaut on 2009-06-16
Hmm, doesn't even work if I strip the script of all SD-Card and USB-Stick handling and simply point to the unencrypted key file in /boot. This certainly doesn't make sense, it's just a test.

Unfortunately I couldn't find a similar HowTo for Jaunty yet.

---

