---
title: "Qemu USB Help"
date: 2007-09-17
forum: Virtualisation
---

### Post by treeko11 on 2007-09-17
Hello everyone,

I recently installed Qemu with XP but i was wondering on how to get USB support working, for i am not sure.

---

### Post by treeko11 on 2007-09-21
bump

---

### Post by kb3hkg on 2007-10-25
I also just installed qemu in ubuntu to run xp, mostly because of a lack of vmware player this time around, I need it for usb functionality so how do I get this working?

---

### Post by Blayde on 2007-10-26
I have found this but been unable to get it to work as of yet. I'm thinking it has something to do w/ /proc/bus/usb because there's nothing there on my Gutsy install and that's where it's looking.

[http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC34](http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC34)

EDIT

I also found this

[https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/156085/+viewstatus](https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/156085/+viewstatus)

which indicates the new location. Perhaps making a symbolic link would do the trick...

EDIT

well apparently the proc filesystem can't be changed, even by root, so the only way to make this work would be compiling qemu with the patch found on launchpad. i suppose a bug/patch should be filed w/ qemu to allow changing the usb path after compile or the package maintainer should update the repositories w/ the patch

---

### Post by Blayde on 2007-10-29
If any of you want this fixed, I suggest you follow my previous link to launchpad and see what has been happening there. Basically, Ubuntu and many other distros have moved from /proc to /dev for usb access. Qemu and kvm have had over a year to make this simple change but they didn't. Patches have been submitted and we are now waiting on the MOTU team to update the repos. Once this is done, the instructions at my first link will get you going.

---

### Post by lvleph on 2007-11-27
I am confused, because I was loking at the S11mountdevsubfs.sh file and it seems to mount from dev. Am I missing something. I figured I would just fixed it myself.
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          mountdevsubfs mountvirtfs
# Required-Start:    mountkernfs
# Required-Stop:
# Default-Start:     S
# Default-Stop:
# Short-Description: Mount special file systems under /dev.
# Description:       Mount the virtual filesystems the kernel provides
#                    that ordinarily live under the /dev filesystem.
### END INIT INFO

PATH=/lib/init:/sbin:/bin
TTYGRP=5
TTYMODE=620
[ -f /etc/default/devpts ] && . /etc/default/devpts

TMPFS_SIZE=
[ -f /etc/default/tmpfs ] && . /etc/default/tmpfs

KERNEL="$(uname -s)"

. /lib/lsb/init-functions
. /lib/init/mount-functions.sh

do_start () {
	#
	# Mount a tmpfs on /dev/shm
	#
	SHM_OPT=
	[ "${SHM_SIZE:=$TMPFS_SIZE}" ] && SHM_OPT="-osize=$SHM_SIZE"
	domount tmpfs shmfs /dev/shm $SHM_OPT

	#
	# Mount /dev/pts. Create master ptmx node if needed.
	#
	domount devpts "" /dev/pts -ogid=$TTYGRP,mode=$TTYMODE

	#
	# Magic to make /proc/bus/usb work
	#
	[ -d /dev/bus/usb/.usbfs ] || mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
}

case "$1" in
  "")
	echo "Warning: mountdevsubfs should be called with the 'start' argument." >&2
	do_start
	;;
  start)
	do_start
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	# No-op
	;;
  *)
	echo "Usage: mountdevsubfs [start|stop]" >&2
	exit 3
	;;
esac
```

---

### Post by andrei.kouznetsov on 2008-11-06
Here is what I have done to make it work:
```

sudo mkdir -p /dev/bus/usb/.usbfs
cd /dev/bus/usb/.usbfs/
sudo mount -n -t usbfs -obusmode=0700,devmode=0600,listmode=0644 usbfs /dev/bus/usb/.usbfs
sudo ln -s .usbfs/devices /dev/bus/usb/devices
sudo mount --rbind /dev/bus/usb /proc/bus/usb

```

then I had to start kvm (essentially qemu) as the root:
```

sudo kvm -no-acpi -m 256 -soundhw es1370 -usb /home/and/Windows/windows.img

```

Everything works

---

### Post by markmckee601 on 2009-06-20
Another way to do it is to add this line to /etc/fstab

none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

It's the same for virtualbox.

---

### Post by gksmithlcw on 2009-09-02
> **markmckee601 said:**
> Another way to do it is to add this line to /etc/fstab

none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

It's the same for virtualbox.

So I make this change to fstab, what do I do to get my guests to properly pick up USB devices?

Thanks!

---

### Post by Goggeli on 2009-11-03
Hello!

Check out [***_this_***]("http://firmit.wordpress.com/2009/01/07/qemu-with-usb-support/")!

I managed to let my xp under Qemu detect my usb printer, still working on installing drivers, but xp found it and noticed it to be a deskjet 2100 series witch is correct.

---

### Post by gksmithlcw on 2009-11-03
> **Goggeli said:**
> Hello!

Check out [***_this_***]("http://firmit.wordpress.com/2009/01/07/qemu-with-usb-support/")!

I managed to let my xp under Qemu detect my usb printer, still working on installing drivers, but xp found it and noticed it to be a deskjet 2100 series witch is correct.

Thank you for the link. I will give it a look.

---

### Post by sdowney717 on 2009-11-04
[http://ubuntuforums.org/showthread.php?t=1300952](http://ubuntuforums.org/showthread.php?t=1300952)

try editing the apparmour settings to allow usb passthrough

---

### Post by gksmithlcw on 2009-11-04
The problem is that I'm using libvirt and virt-manager to manage my KVM machines and, though I've enabled USB through the interface (I updated to a version that supports it), it is not making it to the guest.

---

### Post by sdowney717 on 2009-11-04
i was using virt-manager also and this allowed kvm to see the usb devices
edit that file to allow passthru

then in the console window of the running machine, select the second tab, add hardware and find the usb device that is plugged and select it.

> Couple days ago I've had the same problem, spent several hours to make it work!
The thing is apparmor. You should go to /etc/apparmor.d/abstractions/libvirt-qemu and uncomment some lines there, read the comments in the file.
and check if you have hald installed. virsh (libvirt) relies on it to get host hardware list.
"virsh nodedev-list" has to list host's hardware.

> # Last Modified: Wed Jul  8 09:57:41 2009

  #include <abstractions/base>
  #include <abstractions/consoles>
  #include <abstractions/nameservice>

  # required for reading disk images
  capability dac_override,
  capability dac_read_search,
  capability chown,

  network inet stream,
  network inet6 stream,

  /dev/net/tun rw,
  /dev/kvm rw,
  /dev/ptmx rw,
  /dev/kqemu rw,

  # WARNING: uncommenting these gives the guest direct access to host hardware.
  # This is required for USB pass through but is a security risk. You have been
  # warned.
  /sys/bus/usb/devices/ r,
  /sys/devices/*/*/usb[0-9]*/** r,
  /dev/bus/usb/*/[0-9]* rw,

  # WARNING: this gives the guest direct access to host hardware and specific
  # portions of shared memory. This is required for sound using ALSA with kvm,
  # but may constitute a security risk. If your environment does not require
  # the use of sound in your VMs, feel free to comment out or prepend 'deny' to
  # the rules for files in /dev.
  /dev/shm/ r,
  /dev/shm/pulse-shm* r,
  /dev/shm/pulse-shm* rwk,
  /dev/snd/* rw,
  capability ipc_lock,
  # 'kill' is not required for sound and is a security risk. Do not enable
  # unless you absolutely need it.
  deny capability kill,

  /etc/pulse/client.conf r,
  @{HOME}/.pulse-cookie rwk,
  owner /root/.pulse-cookie rwk,
  owner /root/.pulse/ rw,
  owner /root/.pulse/* rw,
  /usr/share/alsa/** r,
  owner /tmp/pulse-*/ rw,
  owner /tmp/pulse-*/* rw,
  /var/lib/dbus/machine-id r,

  # access to firmware's etc
  /usr/share/kvm/** r,
  /usr/share/qemu/** r,
  /usr/share/bochs/** r,
  /usr/share/openbios/** r,
  /usr/share/openhackware/** r,
  /usr/share/proll/** r,
  /usr/share/vgabios/** r,

  # the various binaries
  /usr/bin/kvm rmix,
  /usr/bin/qemu rmix,
  /usr/bin/qemu-system-arm rmix,
  /usr/bin/qemu-system-cris rmix,
  /usr/bin/qemu-system-i386 rmix,
  /usr/bin/qemu-system-m68k rmix,
  /usr/bin/qemu-system-mips rmix,
  /usr/bin/qemu-system-mips64 rmix,
  /usr/bin/qemu-system-mips64el rmix,
  /usr/bin/qemu-system-mipsel rmix,
  /usr/bin/qemu-system-ppc rmix,
  /usr/bin/qemu-system-ppc64 rmix,
  /usr/bin/qemu-system-ppcemb rmix,
  /usr/bin/qemu-system-sh4 rmix,
  /usr/bin/qemu-system-sh4eb rmix,
  /usr/bin/qemu-system-sparc rmix,
  /usr/bin/qemu-system-sparc64 rmix,
  /usr/bin/qemu-system-x86_64 rmix,
  /usr/bin/qemu-alpha rmix,
  /usr/bin/qemu-arm rmix,
  /usr/bin/qemu-armeb rmix,
  /usr/bin/qemu-cris rmix,
  /usr/bin/qemu-i386 rmix,
  /usr/bin/qemu-m68k rmix,
  /usr/bin/qemu-mips rmix,
  /usr/bin/qemu-mipsel rmix,
  /usr/bin/qemu-ppc rmix,
  /usr/bin/qemu-ppc64 rmix,
  /usr/bin/qemu-ppc64abi32 rmix,
  /usr/bin/qemu-sh4 rmix,
  /usr/bin/qemu-sh4eb rmix,
  /usr/bin/qemu-sparc rmix,
  /usr/bin/qemu-sparc64 rmix,
  /usr/bin/qemu-sparc32plus rmix,
  /usr/bin/qemu-sparc64 rmix,
  /usr/bin/qemu-x86_64 rmix,

  # for save and resume
  /bin/dash rmix,
  /bin/dd rmix,
  /bin/cat rmix,

  # workaround [https://launchpad.net/bugs/457716](https://launchpad.net/bugs/457716). The svirt driver does not
  # relabel the state file ([https://bugzilla.redhat.com/show_bug.cgi?id=529363](https://bugzilla.redhat.com/show_bug.cgi?id=529363))
  # resulting in denied messages. The below works around this somewhat by
  # allowing users to save state files in their home directories. We use
  # 'owner' to make sure we don't overwrite the user's files. This will be
  # removed when the upstream bug is fixed.
  #include <abstractions/private-files-strict>
  owner @{HOME}/ r,
  owner @{HOME}/** rw,

---

### Post by sdowney717 on 2009-11-04
i had shut down issues with kvm, the machine on restart was always giving me grief. i had to continually select "use last known good configuration"
or XP would not boot. sometimes i had to select it multiple times.

the other problem is usb devices are not running at 2.0 speeds.

vmware server 2.0.2 is free and basically everything works.
you have to set up a network bridge for these vm's to network well. using NAT is awful slow.

here is my /etc/network/interfaces file for bridging

> #static on eth2, static on bridge br0
auto eth2
iface eth2 inet manual

auto br0
iface br0 inet static
        address 192.168.1.100
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        bridge_ports eth2
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off 




---

### Post by gksmithlcw on 2009-11-04
> **sdowney717 said:**
> i was using virt-manager also and this allowed kvm to see the usb devices
edit that file to allow passthru

then in the console window of the running machine, select the second tab, add hardware and find the usb device that is plugged and select it.

Thanks! I'll give it a try once I can get to my server again. I'm traveling on business, ATM, and my server's IP seems to have changed...

---

### Post by gksmithlcw on 2010-05-17
> **gksmithlcw said:**
> Thanks! I'll give it a try once I can get to my server again. I'm traveling on business, ATM, and my server's IP seems to have changed...

So... Everything is set up as suggested and I can see the USB devices in virt-manager but my Windows Server vms aren't seeing the USB devices.

I recently upgraded to Ubuntu 10.04 hoping this would help but I've had no luck.

Any ideas?

---

### Post by gksmithlcw on 2010-05-17
> **gksmithlcw said:**
> So... Everything is set up as suggested and I can see the USB devices in virt-manager but my Windows Server vms aren't seeing the USB devices.

I recently upgraded to Ubuntu 10.04 hoping this would help but I've had no luck.

Any ideas?

Update: I got the drive to show up under my Windows server vm but it is saying it is connected to a USB 1.1 host and the device is unable to start...

---

