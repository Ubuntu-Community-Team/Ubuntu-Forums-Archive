---
title: "Trying to get script to unlock LUKS with SD Card"
date: 2010-11-06
forum: Security
---

### Post by thegodfaza on 2010-11-06
Right now I'm using the following script to either unlock my drive with a hardware key or a pass phrase. The script works great with flash drives but I can't get it to work with my SD Card reader. The SD Card is recognised as /dev/mmcblk[disk]p[partition] (/dev/mmcblk0p1). I already added support to my initrd.img for the mmc_core and mmc_block modules. I'm not sure why it's not being detected. The SD Card is set up identically to the other hardware keys I have, just with it's own unique key so if lost / stolen the key can be disabled. I wanted to ask here first before I try to get into contact with the author of the script.

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
# Updated by TJ <linux@tjworld.net> 7 July 2008
# For use with Ubuntu Hardy, usplash, automatic detection of USB devices,
# detection and examination of *all* partitions on the device (not just partition #1), 
# automatic detection of partition type, refactored, commented, debugging code.
#
# Updated by Hendrik van Antwerpen <hendrik at van-antwerpen dot net> 3 Sept 2008
# For encrypted key device support, also added stty support for not
# showing your password in console mode.

# define counter-intuitive shell logic values (based on /bin/true & /bin/false)
# NB. use FALSE only to *set* something to false, but don't test for
# equality, because a program might return any non-zero on error

# Updated by Dominique Bellenger <dev at domesdomain dot de>
# for usage with Ubuntu 10.04 Lucid Lynx
# - Removed non working USB device check
# - changed vol_id to blkid, changed sed expression
# - changed TRUE and FALSE to be 1 and 0
# - changed usplash usage to plymouth usage
# - removed possibility to read from an encrypted device (why would I want to do this? The script is unnecessary if I have to type in a password)

TRUE=1
FALSE=0

# set DEBUG=$TRUE to display debug messages, DEBUG=$FALSE to be quiet
DEBUG=$FALSE

PLYMOUTH=$FALSE
# test for plymouth and if plymouth is running
if [ -x /bin/plymouth ] && plymouth --ping; then
        PLYMOUTH=$TRUE
fi

# is stty available? default false
STTY=$FALSE
STTYCMD=false
# check for stty executable
if [ -x /bin/stty ]; then
	STTY=$TRUE
	STTYCMD=/bin/stty
elif [ `(busybox stty >/dev/null 2>&1; echo $?)` -eq 0 ]; then
	STTY=$TRUE
	STTYCMD="busybox stty"
fi

# print message to plymouth or stderr
# usage: msg "message" [switch]
# switch : switch used for echo to stderr (ignored for plymouth)
# when using plymouth the command will cause "message" to be
# printed according to the "plymouth message" definition.
# using the switch -n will allow echo to write multiple messages
# to the same line
msg ()
{
	if [ $# -gt 0 ]; then
		# handle multi-line messages
		echo $2 | while read LINE; do
			if [ $PLYMOUTH -eq $TRUE ]; then
				/bin/plymouth message --text="$1 $LINE"		
			#else
				# use stderr for all messages
				echo $3 "$2" >&2
			fi
		done
	fi
}

dbg ()
{
	if [ $DEBUG -eq $TRUE ]; then
		msg "$@"
	fi
}

# read password from console or with plymouth
# usage: readpass "prompt"
readpass ()
{
	if [ $# -gt 0 ]; then
		if [ $PLYMOUTH -eq $TRUE ]; then
			PASS=`/bin/plymouth ask-for-password --prompt="$1"`
		else
			[ $STTY -ne $TRUE ] && msg "WARNING stty not found, password will be visible"
			echo -n "$1" >&2
			$STTYCMD -echo
			read -s PASS </dev/console >/dev/null
			[ $STTY -eq $TRUE ] && echo >&2
			$STTYCMD echo
		fi
	fi
	echo -n "$PASS"
}

msg "Checking USB devices for decryption key ..."

# flag tracking key-file availability
OPENED=$FALSE

# temporary mount path for USB key
MD=/tmp-usb-mount

if [ "x$1" = "x" -o "x$1" = "xnone" ]; then
	# default key-file on the USB disk
	KEYFILE=.cryptfs.key
else
	KEYFILE=$1
fi

# If the file already exists use it.
# This is useful where an encrypted volume contains keyfile(s) for later
# volumes and is now mounted and accessible
if [ -f $KEYFILE ]; then
	dbg "Found $KEYFILE"
	cat $KEYFILE
	OPENED=$TRUE
	DEV="existing mount"
	LABEL=""
else
	# Is the USB driver loaded?
	cat /proc/modules | busybox grep usb_storage >/dev/null 2>&1
	USBLOAD=0$?
	if [ $USBLOAD -gt 0 ]; then
		dbg "Loading driver 'usb_storage'"
		modprobe usb_storage >/dev/null 2>&1
	fi

	modprobe mmc_core >/dev/null 2>&1
	modprobe mmc_block >/dev/null 2>&1

	# give the system time to settle and open the USB devices
	sleep 5

	# Are there any SCSI block devices?
	ls -d /sys/block/sd* >/dev/null 2>&1
	SBD=$?

	if [ $SBD -eq 0 ]; then
		mkdir -p $MD
		dbg "Trying to get key-file '$KEYFILE' ..."
		for SFS in /sys/block/sd*/sd??; do
			dbg "Examining $SFS"
			# Is the device removable?
			REMOVABLE=`cat ${SFS}/../removable`
			dbg "REMOVABLE=$REMOVABLE"
			if [ $REMOVABLE -eq $TRUE -a -f $SFS/dev ]; then
				dbg "*possible key device*"
				DEV=`basename $SFS`
				# Check if key device itself is encrypted
				dbg "device $DEV"
				# Use vol_id to determine label
				LABEL="`/sbin/blkid /dev/${DEV} | sed -n 's/.*UUID="\([^"]*\).*/\1/p'`"
				dbg "label $LABEL"
				# Use vol_id to determine fstype
				FSTYPE="`/sbin/blkid /dev/${DEV} | sed -n 's/.*TYPE="\([a-zA-Z0-9-]*\).*/\1/p'`"
				dbg "fstype $FSTYPE"
				# Is the file-system driver loaded?
				cat /proc/modules | busybox grep $FSTYPE >/dev/null 2>&1
				FSLOAD=0$?
				if [ $FSLOAD -gt 0 ]; then
					dbg "loading driver for $FSTYPE"
					# load the correct file-system driver
					modprobe $FSTYPE >/dev/null 2>&1
				fi
				mkdir $MD > /dev/null 2>&1
				dbg "mounting /dev/$DEV on $MD"
				mount /dev/${DEV} $MD -t $FSTYPE -o ro >/dev/null 2>&1
				dbg "(`mount | grep $DEV`)"
				if [ -f $MD/$KEYFILE ]; then
					dbg "found $MD/$KEYFILE"
					cat $MD/$KEYFILE
					OPENED=$TRUE
				fi
				dbg "umount $MD"
				umount $MD >/dev/null 2>&1
				rmdir $MD > /dev/null 2>&1
				dbg "done\n\n"
				if [ $OPENED -eq $TRUE ]; then
					break
				fi
			else
				dbg "device `basename $SFS` ignored"
			fi
        done
	fi
fi


if [ $OPENED -ne $TRUE ]; then
	msg "FAILED to find suitable USB key-file ..."
	readpass "Enter LUKS Password: "
	msg " "
else
	msg "Success loading key-file from $SFS ($LABEL)"
fi
```

---

