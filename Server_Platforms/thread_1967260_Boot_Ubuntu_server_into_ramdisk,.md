---
title: "Boot Ubuntu server into ramdisk,"
date: 2012-04-28
forum: Server Platforms
---

### Post by justin.perkins on 2012-04-28
I have been working on setting up Ubuntu server 11.04 to boot either a ramdisk or on the blockdevice (usb, in my case). A livecd-to-usb standard setup wasn't working very well for me. I have created a modified version of the "local" script and use it on 11.04. After applying the patch (or hand editing local with the changes of course) you only need update-initramfs -u, and boot linux with a "ramboot" kernel argument, and your system will boot a normal linux system fully into ram. Making persistent changes is as easy as rsync'ing the ramdisk filesystem onto the boot-device. In my case, a usb-pen, but it could easily be any suitable bootable block device. You can, of course, just reboot without the "ramboot" argument and make changes, as you will be back on the block device, then reboot into ramboot again, but there is no need, except it makes it very clear when you're in which state. 

0) "sudo su" 

(you don't have to do this step, but then you will need to make sure you sudo everything that might require it) I tend to just "sudo su" when I'm doing this type of systems modifications. 

1) download or copy/paste the contents of this patch to a file:  

"/usr/share/initramfs-tools/scripts/ramboot.patch" -- [http://pastebin.com/Awae1RuJ](http://pastebin.com/Awae1RuJ)
**also included at end**

2) cd /usr/share/initramfs-tools/scripts; cp local local.bak   #just in case

3) patch local ramboot.patch

This applies the changes defined in ramboot.patch, to your local script. /usr/share/initramfs-tools/scripts/local is the normal bootup script configurator which configures the rootmount function for init. The patch was created by "diff local local.modified > ramboot.patch"

4) cp /bin/busybox /usr/lib/initramfs-tools/bin/busybox

This makes your initramfs.img file slightly larger then it would be normally, but the difference is about 1.5 megabytes, not major. I wanted the human readable output from df -h, which the stripped down busybox's df doesn't support. If you care about keeping the 300k version of busybox around, make sure to cp /usr/lib/initramfs-tools/bin/busybox /small_busybox, then return it to it's former name/location after step 5.

5) update-initramfs -u

6) comment out your normal / fstab entry, this sed does it. well, make sure you like the results of this sed before going ahead. It may replace too much if you have a more complex fstab going on. 

```

sed -e 's/^UUID=/none   \/               tmpfs   defaults        0 0\n#UUID=/' </etc/fstab >/tmp/fstab;cp /tmp/fstab /etc/

```7) *optional* you will most likely want to create a /etc/grub.d/06_custom, with the kernel argument "ramboot" included, and a title that implies that. 

(or 40_custom if you want the ramboot menu entry to be at the end of the list, instead of at the top)
e.g. 06_custom -- [http://pastebin.com/frpkHGXf](http://pastebin.com/frpkHGXf)

you will need to fill in your correct kernel-version and initrd.img-verion and also the filesystem uuid of your root device into this 06_custom file or else it will not work. 

you can find the kernel/initrd.img information by just looking in /boot/ with "ls /boot" and the following command should output your root filesystem uuid:

  blkid|grep `df /|grep dev|cut -d ' ' -f1`|cut -d '"' -f2

Once your 06_custom has the correct uuid, kernel and initrd.img paths and file names, you can update-grub, and try it out!

8 ) *if you did step 7* update-grub to add the custom entries to your /boot/grub/grub.cfg file. 


Note: I have a small system with the root partition only including about 1.2g of data to copy into ram. If your system doesn't have enough spare memory, this script will safely boot normally (or at least try!) I found remastersys, and persistent usb-casper installs to not exactly be suitable for my needs. 

This is used on a scst-iscsi server currently, and it's only real weakness is that if you don't save changes to the system, and lose power, or some other mistake (init 0, oh no, I forgot to check in my work back to subversion! disaster!) then the ramdisk system doesn't make anything persistent. I don't have a ton of air-time on this config yet, but since I had looked around for this type of information, found lots of ways that were not exactly suitable, or just plain confusing to me, I thought I'd put this out there. perhaps it will save someone a little teeth pulling *8^) 

remastersys and the root-ro scripts helped me to this point. they are both useful but different projects. remastersys packages your running system, to both deploy/clone, or just run as a live.iso version of the system, or backup I guess. root-ro is a dual-ramdisk blockdevice-filesystem mounted union-style, with the ramdisk writeable, and the blockdev read-only. then to sync you can just remount the blockdev rw, rsync one branch to the other, and remount it ro. This was almost perfect, but I wanted the usb-pen to be unmounted/able to be removed and the system would maintain it's state, which this solution does. 

:edit: This addressed a serious issue with using a usb-pen as a root device on a enterprise class iscsi server that it was very painful to reboot, even every couple of months. After some large amount of time, weeks or even months, the iscsi servers would appear to "lose" the usb device. We started calling it "going to sleep". It takes so long, and then once it happens there is nothing for it, but to reboot, it was very difficult to figure out WHY the device would randomly "go away". Thus, we started trying to think about how we could not care if the usb-pen "went away" for a while. I would dearly like some information if anyone has it, about why/how a usb-pen could randomly become unresponsive, but this solution works around that issue. 

root-ro bottom of the page -- [https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash](https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash)

remastersys -- [http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

You can easily rsync or copy -r from the ramboot (mounted on /) and the disk/device which it came from originally when running in ram, to make that change "persistent". 
I save the uuid of the device that the ramboot booted from, so you can always find it afterwards. It is in /.bootdisk_byuuid on the ramdisk, and you could easily set a script to mount this device somewhere, do the rsync, and umount it again, and call that script "ramtodisk" or whatever. 

NB! you may want to back up your /boot/initrd.img<yourverison>  file so in case something goes wrong, your system is still bootable. I saved mine to /boot/initrd while doing work on this. when I had glitches with grub/init, I just edited my initrd to point to the backup /boot/initrd file and got back to debugging.  anyways, I am guessing that this is more guidelines not cookbook. have fun! it takes my 1.2gig system 9:30ish to boot on usb 1.1, 1:30-45 on usb 2.0, and ~=35 seconds on usb 3.0 to load into ram.  more and more juicy every year! *8^)

here's ramboot.patch
```

2a3,13
> parse_cmdline() {
>     RAM=""
>     for x in $(cat /proc/cmdline); do
>         case $x in
>           ramboot)
>               RAM="Yes" ;;
>             quiet)
>                 quiet=y ;;
>         esac
>     done
> }
66c77
<
---
>       parse_cmdline
90,91c101,164
<       # Mount root
<       mount ${roflag} ${FSTYPE:+-t ${FSTYPE} }${ROOTFLAGS} ${ROOT} ${rootmnt}
---
>       # Mount root - custom ramboot.patch
>       # By: Justin Perkins -- 4/25/12 Email: justin.perkins@vm-labs.com
>       if [ -z "${RAM}" ]; then
>               mount ${roflag} ${FSTYPE:+-t ${FSTYPE} }${ROOTFLAGS} ${ROOT} ${rootmnt}
>       else
>               mkdir /ramboot
>               mount ${roflag} -t ${FSTYPE} ${ROOTFLAGS} ${ROOT} /ramboot
>               log_begin_msg "Detecting system resources"
>               size=$(df|grep ramboot|tr -s ' '|cut -d ' ' -f3)
>               datasize=${size}
>               size=$(expr ${size} + ${size} / 20 )    #5% more to be sure
>               freespace=$(awk '/^MemFree:/{f=$2} /^Cached:/{c=$2} END{print f+c}' /proc/meminfo)
>               log_end_msg
>               if [ "${freespace}" -lt "${size}" ] ; then
>                       echo "Not enough system RAM, ${freespace}k > ${size}k."
>                       echo "Attempting normal rootmount."
>                       mount ${roflag} ${FSTYPE:+-t ${FSTYPE} }${ROOTFLAGS} ${ROOT} ${rootmnt}
>               else
>                       if [ "$quiet" != "y" ] ; then
>                               tstart_min=$(date|cut -d ' ' -f4|cut -d : -f2)
>                               tstart_sec=$(date|cut -d ' ' -f4|cut -d : -f3)
>                               mount -t tmpfs -o size=100% none ${rootmnt}
>                               cd ${rootmnt}
>                               size=$(df -h|grep ramboot|tr -s ' '|cut -d ' ' -f3)     #reuse size
>                               echo "System size: ${size} (${datasize}k) this may take a couple of minutes."
>                               log_begin_msg "Copying system files into RAM"
>                               echo -e -n "\b"
>                               cp -rfa /ramboot/* ${rootmnt} &
>                               pid=$!
>                               while [ ! ${pid} == "done" ] ; do
>                                       alive=$(ps -o pid,args|grep -E ${pid}|grep -v grep)
>                                       alive=$(echo ${alive}|cut -d ' ' -f1)
>                                       if [ -z ${alive} ] ; then pid="done" ; fi
>                                       printf "."
>                                       sleep 1
>                               done
>                               log_end_msg
>                               echo ${ROOT} > ${rootmnt}/.bootdisk_byuuid
>                               tend_min=$(date|cut -d ' ' -f4|cut -d : -f2)
>                               tend_sec=$(date|cut -d ' ' -f4|cut -d : -f3)
>                               if [ ${tend_sec} -lt ${tstart_sec} ] ; then
>                                       tend_sec=$(expr ${tend_sec} + 60)
>                                       tend_min=$(expr ${tend_min} - 1)
>                               fi
>                               if [ ${tend_min} -lt ${tstart_min} ] ; then
>                                       tend_min=$(expr ${tend_min} + 60)
>                           fi
>                           tduration_min=$(expr ${tend_min} - ${tstart_min})
>                           tduration_sec=$(expr ${tend_sec} - ${tstart_sec})
>                           echo "Copy complete, duration: $tduration_min minutes $tduration_sec seconds."
>                           freespace=$(awk '/^MemFree:/{f=$2} END{print f}' /proc/meminfo)
>                           freespace=$(expr ${freespace} + 425000)         #this accounts for the temporal settling issue
>                           echo "You have approximately ${freespace}k free RAM after loading the ramboot."
>                           if [ ${freespace} -lt "502400" ] ; then echo "Warning! you have critically low system RAM free after ramboot." ; fi
>
>                   else
>                           cp -rfa /ramboot/* ${rootmnt}
>                           echo ${ROOT} > ${rootmnt}/.bootdisk_byuuid
>                           freespace=$(awk '/^MemFree:/{f=$2} END{print f}' /proc/meminfo)
>                           if [ ${freespace} -lt "102400" ] ; then echo "Warning! you have critically low system RAM free after ramboot." ; fi
>                   fi
>           fi
>           umount /ramboot
>   fi      #end custom ramboot.patch


```06_custom
```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
#uuid_<placeholder>, and vmlinuz-<placeholder>, and initrd.img-<placeholder> and
#set root='(hd0,2)' need to be replaced with your system's values, although, if you
#get the hd0,2 wrong, but the uuid correct, grub will grep around and find it anyhow. 
menuentry "Ubuntu, with Linux Custom-Ramboot" {
     recordfail
     set root='(hd0,2)'
     search --no-floppy --fs-uuid --set=root uuid_placeholder
     linux /boot/vmlinuz-<placeholder> root=UUID=<uuid-placeholder> ro ramboot
     initrd /boot/initrd.img-<placeholder>
}

```::EDIT::  I forgot something VERY important! when you are done with rebuilding the initramfs, you MUST make a change to your /etc/fstab, I was tired I guess when I posted last night, and forgot this, esssssential detail:

this should do the edit:
```

sed -e 's/^UUID=/none   \/               tmpfs   defaults        0 0\n#UUID=/' </etc/fstab >/tmp/fstab;cp /tmp/fstab /etc/

``` sorry if you already got past needing this!

This just comments out the uuid / entry in fstab, and puts a none tmpfs entry in. 

This leads me to one thing, if anyone can tell me why the none entry in the fstab still works when loading the "normal" boot, I'm curious about that. I figured w/o researching/testing that it would need a script to switch cases, but it seems to run fine on the physical disk, or ramboot, with the "none" entry for / in fstab that the above sed does.

---

### Post by Jonathan L on 2012-04-28
Justin

This looks like great work.  Hope to try it shortly.

Kind regards,
Jonathan.

---

### Post by justin.perkins on 2012-05-08
It has been brought to my attention that the contents of the ramboot.patch is malformed in some way, and won't work. 


Justin, 

   I currently using ubuntu 11.04.   I've tried to run the ramboot.patch but is giving me the following error :

**** `<' expected at line 14 of patch

   Is there anything I can change in the script to fix the error?   Can I use the same patch in ubuntu 12.04?



I tried to get fancy with the patch. There are a couple of possible pitfalls, but I suspect I should not have been so sure of my ability to manually edit a .patch file successfully, it's tricky, but doable. Obviously my initial tries were more successful then this one! (I was skipping steps to remove some company-name stuff from the public posted version, nothing important, but a malformed .patch is made from fail.) 

ok so here is the whole custom local script, you will want to backup /usr/share/initramfs-tools/scripts/local, then replace it with the contents of this code block:

local.ramboot
```


# Local filesystem mounting			-*- shell-script -*-

parse_cmdline() {
    RAM=""
    for x in $(cat /proc/cmdline); do
        case $x in
	    ramboot)
		RAM="Yes" ;;
            quiet)
                quiet=y ;;
        esac
    done
}
pre_mountroot()
{
	[ "$quiet" != "y" ] && log_begin_msg "Running /scripts/local-top"
	run_scripts /scripts/local-top
	[ "$quiet" != "y" ] && log_end_msg

	# Don't wait for a root device that doesn't have a corresponding
	# device in /dev (ie, mtd0)
	if [ "${ROOT#/dev}" = "${ROOT}" ]; then
		return
	fi

	while [ -z "${FSTYPE}" ]; do
		FSTYPE=$(wait-for-root "${ROOT}" ${ROOTDELAY:-30})

		# Load ubi with the correct MTD partition and return since
		# fstype doesn't work with a char device like ubi.
		if [ -n "$UBIMTD" ]; then
			modprobe ubi mtd=$UBIMTD
			return
		fi

		# Run failure hooks, hoping one of them can fix up the system
		# and we can restart the wait loop.  If they all fail, abort
		# and move on to the panic handler and shell.
		if [ -z "${FSTYPE}" ] && ! try_failure_hooks; then
			break
		fi
	done

	# We've given up, but we'll let the user fix matters if they can
	while [ -z "${FSTYPE}" -a ! -e "${ROOT}" ]; do
		# give hint about renamed root
		case "${ROOT}" in
		/dev/hd*)
			suffix="${ROOT#/dev/hd}"
			major="${suffix%[[:digit:]]}"
			major="${major%[[:digit:]]}"
			if [ -d "/sys/block/sd${major}" ]; then
				echo "WARNING bootdevice may be renamed. Try root=/dev/sd${suffix}"
			fi
			;;
		/dev/sd*)
			suffix="${ROOT#/dev/sd}"
			major="${suffix%[[:digit:]]}"
			major="${major%[[:digit:]]}"
			if [ -d "/sys/block/hd${major}" ]; then
				echo "WARNING bootdevice may be renamed. Try root=/dev/hd${suffix}"
			fi
			;;
		esac
		echo "Gave up waiting for root device.  Common problems:"
		echo " - Boot args (cat /proc/cmdline)"
		echo "   - Check rootdelay= (did the system wait long enough?)"
		echo "   - Check root= (did the system wait for the right device?)"
		echo " - Missing modules (cat /proc/modules; ls /dev)"
		panic "ALERT!  ${ROOT} does not exist.  Dropping to a shell!"
	done
}

mountroot()
{
	pre_mountroot
	parse_cmdline
	# Get the root filesystem type if not set
	if [ -z "${ROOTFSTYPE}" ]; then
		[ -n "${FSTYPE}" ] || FSTYPE=$(blkid -s TYPE -o value "${ROOT}")
		ROOTFSTYPE="${FSTYPE}"
	else
		FSTYPE=${ROOTFSTYPE}
	fi

	[ "$quiet" != "y" ] && log_begin_msg "Running /scripts/local-premount"
	run_scripts /scripts/local-premount
	[ "$quiet" != "y" ] && log_end_msg

	if [ "${readonly}" = "y" ] && \
	   [ -z "$LOOP" ]; then
		roflag=-r
	else
		roflag=-w
	fi

	# FIXME This has no error checking
	[ -n "${FSTYPE}" ] && modprobe ${FSTYPE}

	# FIXME This has no error checking
	# Mount root - custom ramboot.patch 
	if [ -z "${RAM}" ]; then
		mount ${roflag} ${FSTYPE:+-t ${FSTYPE} }${ROOTFLAGS} ${ROOT} ${rootmnt}
	else
		mkdir /ramboot
		mount ${roflag} -t ${FSTYPE} ${ROOTFLAGS} ${ROOT} /ramboot
		log_begin_msg "Detecting system resources"
		size=$(df|grep ramboot|tr -s ' '|cut -d ' ' -f3)
		datasize=${size}
		size=$(expr ${size} + ${size} / 20 )    #5% more to be sure
		freespace=$(awk '/^MemFree:/{f=$2} /^Cached:/{c=$2} END{print f+c}' /proc/meminfo)
		log_end_msg
		if [ "${freespace}" -lt "${size}" ] ; then
			echo "Not enough system RAM, ${freespace}k > ${size}k."
			echo "Attempting normal rootmount."
			mount ${roflag} ${FSTYPE:+-t ${FSTYPE} }${ROOTFLAGS} ${ROOT} ${rootmnt}
		else
			if [ "$quiet" != "y" ] ; then 
				tstart_min=$(date|tr -s ' '|cut -d ' ' -f4|cut -d : -f2)
				tstart_sec=$(date|tr -s ' '|cut -d ' ' -f4|cut -d : -f3)
				mount -t tmpfs -o size=100% none ${rootmnt}
				cd ${rootmnt}
				size=$(df -h|grep ramboot|tr -s ' '|cut -d ' ' -f3)	#reuse size human readable
				echo "System size: ${size} (${datasize}k) this may take a couple of minutes."
				log_begin_msg "Copying system files into RAM"
				echo -e -n "\b"
				cp -rfa /ramboot/* ${rootmnt} &
				pid=$!
				totalmem=$(awk '/^MemTotal:/{f=$2} END{print f}' /proc/meminfo)
				while [ ! ${pid} == "done" ] ; do
					alive=$(ps -o pid,args|grep -E ${pid}|grep -v grep)
					alive=$(echo ${alive}|cut -d ' ' -f1)
					if [ -z ${alive} ] ; then pid="done" ; fi
					printf "."
					sleep 1
				done
				log_end_msg
				echo ${ROOT} > ${rootmnt}/.bootdisk_byuuid
				tend_min=$(date|tr -s ' '|cut -d ' ' -f4|cut -d : -f2)
				tend_sec=$(date|tr -s ' '|cut -d ' ' -f4|cut -d : -f3)
				if [ ${tend_sec} -lt ${tstart_sec} ] ; then 
					tend_sec=$(expr ${tend_sec} + 60)
					tend_min=$(expr ${tend_min} - 1)
				fi
				if [ ${tend_min} -lt ${tstart_min} ] ; then 
					tend_min=$(expr ${tend_min} + 60)
				fi
				tduration_min=$(expr ${tend_min} - ${tstart_min})
				tduration_sec=$(expr ${tend_sec} - ${tstart_sec})
				echo "Copy complete, duration: $tduration_min minutes $tduration_sec seconds."
				freespace=$(awk '/^MemFree:/{f=$2} END{print f}' /proc/meminfo)
				freespace=$(expr ${freespace} + 425000)		#this accounts for the temporal settling issue
				echo "You have approximately ${freespace}k free RAM after loading the ramboot."
				if [ ${freespace} -lt "502400" ] ; then echo "Warning! you have critically low system RAM free after ramboot." ; fi
			
			else	
				cp -rfa /ramboot/* ${rootmnt}
				echo ${ROOT} > ${rootmnt}/.bootdisk_byuuid
				freespace=$(awk '/^MemFree:/{f=$2} END{print f}' /proc/meminfo)
				if [ ${freespace} -lt "102400" ] ; then echo "Warning! you have critically low system RAM free after ramboot." ; fi
			fi	
		fi
		umount /ramboot
	fi	#end custom ramboot.patch
	mountroot_status="$?"
	if [ "$LOOP" ]; then
		if [ "$mountroot_status" != 0 ]; then
			if [ ${FSTYPE} = ntfs ] || [ ${FSTYPE} = vfat ]; then
				panic "
Could not mount the partition ${ROOT}.
This could also happen if the file system is not clean because of an operating
system crash, an interrupted boot process, an improper shutdown, or unplugging
of a removable device without first unmounting or ejecting it.  To fix this,
simply reboot into Windows, let it fully start, log in, run 'chkdsk /r', then
gracefully shut down and reboot back into Windows. After this you should be
able to reboot again and resume the installation.
(filesystem = ${FSTYPE}, error code = $mountroot_status)
"
			fi
		fi
	
		mkdir -p /host
		mount -o move ${rootmnt} /host

		while [ ! -e "/host/${LOOP#/}" ]; do
			panic "ALERT!  /host/${LOOP#/} does not exist.  Dropping to a shell!"
		done

		# Get the loop filesystem type if not set
		if [ -z "${LOOPFSTYPE}" ]; then
			eval $(fstype < "/host/${LOOP#/}")
		else
			FSTYPE="${LOOPFSTYPE}"
		fi
		if [ "$FSTYPE" = "unknown" ] && [ -x /sbin/blkid ]; then
			FSTYPE=$(/sbin/blkid -s TYPE -o value "/host/${LOOP#/}")
			[ -z "$FSTYPE" ] && FSTYPE="unknown"
		fi

		if [ ${readonly} = y ]; then
			roflag=-r
		else
			roflag=-w
		fi

		# FIXME This has no error checking
		modprobe loop
		modprobe ${FSTYPE}

		# FIXME This has no error checking
		mount ${roflag} -o loop -t ${FSTYPE} ${LOOPFLAGS} "/host/${LOOP#/}" ${rootmnt}

		if [ -d ${rootmnt}/host ]; then
			mount -o move /host ${rootmnt}/host
		fi
	fi

	[ "$quiet" != "y" ] && log_begin_msg "Running /scripts/local-bottom"
	run_scripts /scripts/local-bottom
	[ "$quiet" != "y" ] && log_end_msg
}

```


Also worth note: The original duration calculations neglected to squeeze the whitespace from the output of date, which caused some months to work, and others to fail to output the duration of copy-into-ram correctly. this is fixed in the above local, but because it is cosmetic only, I didn't leap to fix it when I noticed (when april became may, it broke)

---

### Post by rockcreektech on 2013-02-20
I have tried a couple of times to get this to work on 12.04 with no success. After I've made all the changes and try to reboot, it simply won't boot up at all anymore, including to recovery mode. I suspect the initramfs script modifications may not be fully compatible with 12.04. Has anyone else had success with this? I'm VERY interested in getting this to work.

My goal is a machine that boots Ubuntu server fully to ramdisk because I want it to be completely immune to the affects of unplanned reboots (eg power failures) and I don't want any changes made to the OS to be persistent upon reboot. I've thought about doing a root-ro type scenario, but it needs to behave like a normal rw filesystem in terms of the ability to modify configuration at will. I just don't want those modifications to persist. If anyone knows of another method of accomplishing this on Precise, I'm open to other suggestions.

---

### Post by justin.perkins on 2013-02-20
I have not had a chance to test/port this procedure to 12.04. I will give it a twirl shortly. I am still using this setup successfully on 11.04 systems every single day.

---

### Post by rockcreektech on 2013-02-20
Just before it stops booting this is what I'm seeing:

> 
: not foundting root file system ... /init: /scripts/local: line 2:
/init: /scripts/local: line 5: syntax error: unexpected word (expecting "do")
[    1.957240] Kernel panic - not syncing: Attempted to kill init!
[    1.957334] Pid: 1, comm: init Not tainted 3.2.0-28-generic-pae #60-Ubuntu


That's followed by all the "Call Trace" info. So it's possible that something is not getting copied and pasted correctly from the custom "local" script you posted above. It seems unlikely that a syntax error would be a result of using a more recent kernel.

For the record "not foundting" is really what is says. That was not a typo on my part.

And here is a copy and paste back from my "local" script so you can see if anything somehow got altered in the process of copying it from here:

```

# Local filesystem mounting			-*- shell-script -*-

parse_cmdline() {
    RAM=""
    for x in $(cat /proc/cmdline); do
        case $x in
	    ramboot)
		RAM="Yes" ;;
            quiet)
                quiet=y ;;
        esac
    done
}
pre_mountroot()
{
	[ "$quiet" != "y" ] && log_begin_msg "Running /scripts/local-top"
	run_scripts /scripts/local-top
	[ "$quiet" != "y" ] && log_end_msg

	# Don't wait for a root device that doesn't have a corresponding
	# device in /dev (ie, mtd0)
	if [ "${ROOT#/dev}" = "${ROOT}" ]; then
		return
	fi

	while [ -z "${FSTYPE}" ]; do
		FSTYPE=$(wait-for-root "${ROOT}" ${ROOTDELAY:-30})

		# Load ubi with the correct MTD partition and return since
		# fstype doesn't work with a char device like ubi.
		if [ -n "$UBIMTD" ]; then
			modprobe ubi mtd=$UBIMTD
			return
		fi

		# Run failure hooks, hoping one of them can fix up the system
		# and we can restart the wait loop.  If they all fail, abort
		# and move on to the panic handler and shell.
		if [ -z "${FSTYPE}" ] && ! try_failure_hooks; then
			break
		fi
	done

	# We've given up, but we'll let the user fix matters if they can
	while [ -z "${FSTYPE}" -a ! -e "${ROOT}" ]; do
		# give hint about renamed root
		case "${ROOT}" in
		/dev/hd*)
			suffix="${ROOT#/dev/hd}"
			major="${suffix%[[:digit:]]}"
			major="${major%[[:digit:]]}"
			if [ -d "/sys/block/sd${major}" ]; then
				echo "WARNING bootdevice may be renamed. Try root=/dev/sd${suffix}"
			fi
			;;
		/dev/sd*)
			suffix="${ROOT#/dev/sd}"
			major="${suffix%[[:digit:]]}"
			major="${major%[[:digit:]]}"
			if [ -d "/sys/block/hd${major}" ]; then
				echo "WARNING bootdevice may be renamed. Try root=/dev/hd${suffix}"
			fi
			;;
		esac
		echo "Gave up waiting for root device.  Common problems:"
		echo " - Boot args (cat /proc/cmdline)"
		echo "   - Check rootdelay= (did the system wait long enough?)"
		echo "   - Check root= (did the system wait for the right device?)"
		echo " - Missing modules (cat /proc/modules; ls /dev)"
		panic "ALERT!  ${ROOT} does not exist.  Dropping to a shell!"
	done
}

mountroot()
{
	pre_mountroot
	parse_cmdline
	# Get the root filesystem type if not set
	if [ -z "${ROOTFSTYPE}" ]; then
		[ -n "${FSTYPE}" ] || FSTYPE=$(blkid -s TYPE -o value "${ROOT}")
		ROOTFSTYPE="${FSTYPE}"
	else
		FSTYPE=${ROOTFSTYPE}
	fi

	[ "$quiet" != "y" ] && log_begin_msg "Running /scripts/local-premount"
	run_scripts /scripts/local-premount
	[ "$quiet" != "y" ] && log_end_msg

	if [ "${readonly}" = "y" ] && \
	   [ -z "$LOOP" ]; then
		roflag=-r
	else
		roflag=-w
	fi

	# FIXME This has no error checking
	[ -n "${FSTYPE}" ] && modprobe ${FSTYPE}

	# FIXME This has no error checking
	# Mount root - custom ramboot.patch 
	if [ -z "${RAM}" ]; then
		mount ${roflag} ${FSTYPE:+-t ${FSTYPE} }${ROOTFLAGS} ${ROOT} ${rootmnt}
	else
		mkdir /ramboot
		mount ${roflag} -t ${FSTYPE} ${ROOTFLAGS} ${ROOT} /ramboot
		log_begin_msg "Detecting system resources"
		size=$(df|grep ramboot|tr -s ' '|cut -d ' ' -f3)
		datasize=${size}
		size=$(expr ${size} + ${size} / 20 )    #5% more to be sure
		freespace=$(awk '/^MemFree:/{f=$2} /^Cached:/{c=$2} END{print f+c}' /proc/meminfo)
		log_end_msg
		if [ "${freespace}" -lt "${size}" ] ; then
			echo "Not enough system RAM, ${freespace}k > ${size}k."
			echo "Attempting normal rootmount."
			mount ${roflag} ${FSTYPE:+-t ${FSTYPE} }${ROOTFLAGS} ${ROOT} ${rootmnt}
		else
			if [ "$quiet" != "y" ] ; then 
				tstart_min=$(date|tr -s ' '|cut -d ' ' -f4|cut -d : -f2)
				tstart_sec=$(date|tr -s ' '|cut -d ' ' -f4|cut -d : -f3)
				mount -t tmpfs -o size=100% none ${rootmnt}
				cd ${rootmnt}
				size=$(df -h|grep ramboot|tr -s ' '|cut -d ' ' -f3)	#reuse size human readable
				echo "System size: ${size} (${datasize}k) this may take a couple of minutes."
				log_begin_msg "Copying system files into RAM"
				echo -e -n "\b"
				cp -rfa /ramboot/* ${rootmnt} &
				pid=$!
				totalmem=$(awk '/^MemTotal:/{f=$2} END{print f}' /proc/meminfo)
				while [ ! ${pid} == "done" ] ; do
					alive=$(ps -o pid,args|grep -E ${pid}|grep -v grep)
					alive=$(echo ${alive}|cut -d ' ' -f1)
					if [ -z ${alive} ] ; then pid="done" ; fi
					printf "."
					sleep 1
				done
				log_end_msg
				echo ${ROOT} > ${rootmnt}/.bootdisk_byuuid
				tend_min=$(date|tr -s ' '|cut -d ' ' -f4|cut -d : -f2)
				tend_sec=$(date|tr -s ' '|cut -d ' ' -f4|cut -d : -f3)
				if [ ${tend_sec} -lt ${tstart_sec} ] ; then 
					tend_sec=$(expr ${tend_sec} + 60)
					tend_min=$(expr ${tend_min} - 1)
				fi
				if [ ${tend_min} -lt ${tstart_min} ] ; then 
					tend_min=$(expr ${tend_min} + 60)
				fi
				tduration_min=$(expr ${tend_min} - ${tstart_min})
				tduration_sec=$(expr ${tend_sec} - ${tstart_sec})
				echo "Copy complete, duration: $tduration_min minutes $tduration_sec seconds."
				freespace=$(awk '/^MemFree:/{f=$2} END{print f}' /proc/meminfo)
				freespace=$(expr ${freespace} + 425000)		#this accounts for the temporal settling issue
				echo "You have approximately ${freespace}k free RAM after loading the ramboot."
				if [ ${freespace} -lt "502400" ] ; then echo "Warning! you have critically low system RAM free after ramboot." ; fi
			
			else	
				cp -rfa /ramboot/* ${rootmnt}
				echo ${ROOT} > ${rootmnt}/.bootdisk_byuuid
				freespace=$(awk '/^MemFree:/{f=$2} END{print f}' /proc/meminfo)
				if [ ${freespace} -lt "102400" ] ; then echo "Warning! you have critically low system RAM free after ramboot." ; fi
			fi	
		fi
		umount /ramboot
	fi	#end custom ramboot.patch
	mountroot_status="$?"
	if [ "$LOOP" ]; then
		if [ "$mountroot_status" != 0 ]; then
			if [ ${FSTYPE} = ntfs ] || [ ${FSTYPE} = vfat ]; then
				panic "
Could not mount the partition ${ROOT}.
This could also happen if the file system is not clean because of an operating
system crash, an interrupted boot process, an improper shutdown, or unplugging
of a removable device without first unmounting or ejecting it.  To fix this,
simply reboot into Windows, let it fully start, log in, run 'chkdsk /r', then
gracefully shut down and reboot back into Windows. After this you should be
able to reboot again and resume the installation.
(filesystem = ${FSTYPE}, error code = $mountroot_status)
"
			fi
		fi
	
		mkdir -p /host
		mount -o move ${rootmnt} /host

		while [ ! -e "/host/${LOOP#/}" ]; do
			panic "ALERT!  /host/${LOOP#/} does not exist.  Dropping to a shell!"
		done

		# Get the loop filesystem type if not set
		if [ -z "${LOOPFSTYPE}" ]; then
			eval $(fstype < "/host/${LOOP#/}")
		else
			FSTYPE="${LOOPFSTYPE}"
		fi
		if [ "$FSTYPE" = "unknown" ] && [ -x /sbin/blkid ]; then
			FSTYPE=$(/sbin/blkid -s TYPE -o value "/host/${LOOP#/}")
			[ -z "$FSTYPE" ] && FSTYPE="unknown"
		fi

		if [ ${readonly} = y ]; then
			roflag=-r
		else
			roflag=-w
		fi

		# FIXME This has no error checking
		modprobe loop
		modprobe ${FSTYPE}

		# FIXME This has no error checking
		mount ${roflag} -o loop -t ${FSTYPE} ${LOOPFLAGS} "/host/${LOOP#/}" ${rootmnt}

		if [ -d ${rootmnt}/host ]; then
			mount -o move /host ${rootmnt}/host
		fi
	fi

	[ "$quiet" != "y" ] && log_begin_msg "Running /scripts/local-bottom"
	run_scripts /scripts/local-bottom
	[ "$quiet" != "y" ] && log_end_msg
}

```

---

