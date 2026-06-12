---
title: "Virtual Box USB Serial Port settings"
date: 2008-04-02
forum: Virtualisation
---

### Post by hitspace on 2008-04-02
Hey i just installed virtual box but after setting up a virtual os /system i found out that neither my sound or my usb was working . i figured that it was because in the settings menu i hadnt enabled the sound  while installing windows xp. i  was wondering though that if usb support is provided and that if you are supposed to enable it by enabling the serial port options on the settings menu . i enabled the serial port but its still listed as disconnected . when i set the host pipe or host device option it asks me to specify the path . i was wondering what that path would be .  i really need the usb support for thie virtual system . 

 i also heard that it was possible to automatically get the os to recognize all usbs on the host by changing a line number from 0644 or something which i dont recall . if you could help me with that  i would be extremely grateful

your help is much appreciated

---

### Post by bmwman on 2008-04-04
Here is how I enabled my USB ports. Sound should work just by enable it in the Vbox  settings.

Setup User groups & USB support
Add yourself as a virtual box user
In a terminal type:
**sudo adduser username vboxusers**
You must replace userame with your user name!

Add USB support to you fstab file
In a terminal type:
**sudo gedit /etc/fstab**

And paste this line to the end of your fstab
**none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0**

Enable USB
In a terminal type:
**sudo gedit /etc/init.d/mountdevsubfs.sh**

You need to look for this section:
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

And delete all the # shown, it should look exactly like this.

#Magic to make /proc/bus/usb work

mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

Find your vboxusers number
In a terminal type:
**sudo gedit /etc/group**

Look for this, the number following it is your vboxusers number
**vboxusers:x:NUMBER**

Next you have to add a line to your /etc/fstab to allow usb mounting
In a terminal type:
**sudo gedit /etc/fstab**

Add this line:
**none /proc/bus/usb usbfs devgid= enter vboxusers number HERE,devmode=664 0 0**

Allow access to /proc/bus/usb/
in a teminal type:
**sudo chown -R root:vboxusers /proc/bus/usb**

Once you Log out or reboot, you can start VirtualBox (Applications>System Tools>Innotek VirtualBox)

---

### Post by toymaker0 on 2009-04-28
> **bmwman said:**
> Here is how I enabled my USB ports. Sound should work just by enable it in the Vbox  settings.

Setup User groups & USB support
Add yourself as a virtual box user
In a terminal type:
**sudo adduser username vboxusers**
You must replace userame with your user name!

Add USB support to you fstab file
In a terminal type:
**sudo gedit /etc/fstab**

And paste this line to the end of your fstab
**none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0**

Enable USB
In a terminal type:
**sudo gedit /etc/init.d/mountdevsubfs.sh**

You need to look for this section:
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

And delete all the # shown, it should look exactly like this.

#Magic to make /proc/bus/usb work

mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

Find your vboxusers number
In a terminal type:
**sudo gedit /etc/group**

Look for this, the number following it is your vboxusers number
**vboxusers:x:NUMBER**

Next you have to add a line to your /etc/fstab to allow usb mounting
In a terminal type:
**sudo gedit /etc/fstab**

Add this line:
**none /proc/bus/usb usbfs devgid= enter vboxusers number HERE,devmode=664 0 0**

Allow access to /proc/bus/usb/
in a teminal type:
**sudo chown -R root:vboxusers /proc/bus/usb**

Once you Log out or reboot, you can start VirtualBox (Applications>System Tools>Innotek VirtualBox)


hi bmwman, thanks a lot to this lttle tuto, however i cannot make it works, i stucked in the part where i suppose to enable the usb port, ( **sudo gedit /etc/init.d/mountdevsubfs.sh) **you said that i need to erase every single "#" but the gedit doesnt seem like you posted. #magic to make. this is what appears on my screen.

#! /bin/sh
### BEGIN INIT INFO
# Provides:          mountdevsubfs
# Required-Start:    mountkernfs
# Required-Stop:
# Should-Start:      udev
# Default-Start:     S
# Default-Stop:
# Short-Description: Mount special file systems under /dev.
# Description:       Mount the virtual filesystems the kernel provides
#                    that ordinarily live under the /dev filesystem.
### END INIT INFO
#
# This script gets called multiple times during boot
#

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
    
    # Mount a tmpfs on /dev/shm
    
    SHM_OPT=
    [ "${SHM_SIZE:=$TMPFS_SIZE}" ] && SHM_OPT=",size=$SHM_SIZE"
    domount tmpfs shmfs /dev/shm tmpfs -onosuid,nodev$SHM_OPT

    
     Mount /dev/pts. Master ptmx node is already created by udev.
    
        domount devpts "" /dev/pts devpts -onoexec,nosuid,gid=$TTYGRP,mode=$TTYMODE
}

case "$1" in
  "")
    echo "Warning: mountdevsubfs should be called with the 'start' argument." >&2
    do_start

i erased every # and restar and it doesn work. and i opened again and all the # appear again.

---

### Post by volaer on 2009-07-26
Same as toymaker0. I have the same codes:  sudo gedit /etc/init.d/mountdevsubfs.sh

---

