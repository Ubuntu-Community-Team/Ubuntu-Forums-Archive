---
title: "Disable/enable USB storage device @ run time"
date: 2008-08-01
forum: Security
---

### Post by Mr.Jkate on 2008-08-01
I need to disable/enable USB storage device @ run time on ubuntu 7.1
Any Idea ?

---

### Post by cdenley on 2008-08-01
> **Mr.Jkate said:**
> I need to disable/enable USB storage device @ run time on ubuntu 7.1
Any Idea ?

I haven't tried it, but I think this would work.
```

sudo bash -c "echo blacklist usb-storage>/etc/modprobe.d/disable-usbstor"

```

---

### Post by unutbu on 2008-08-01
One way would be to compile a kernel with no USB storage support, and then add a GRUB boot stanza for the new kernel. The advantage of doing it this way is that compiling kernels is a well documented process, and so is editing GRUB menu.lst, so all the pieces to the solution are generally available. The disadvantage is you'll be installing maybe ~100MB of files just to disable USB storage. You might be able to cut down on the bloat with a lot of symlinks, but I'm not confident I could describe the process and be right at the same time.

There may be a better way -- something along the lines of what cdenley suggested -- by editing some configuration file. The particular command cdenley suggested will (I think) work if you run the command *before* rebooting when you want USB disabled. But when you want to re-enable USB storage, you'd have to remove the /etc/modprobe.d/disable-usbstor file.

If there is a better way along these lines, I do not know it.

A third possibility is the following hack: You can hook up a GRUB boot stanza to a different runlevel.
The advantage here is you can control the behavior by select a boot option in the GRUB menu, but unlike when compiling a new kernel, there will not be tons of files installed. The disadvantage of this hack is that it attacks the problem too late in the boot process -- the usb-storage kernel module will have already been loaded into the kernel, so the hack simply runs a script to unmount your USB partitions and then remove the usb-storage module. 

Well, for what it's worth, here is the hack:


[list=1]
[*] Hook up a GRUB boot stanza to runlevel 3 
(Your default boot is runlevel 2, we can leave that alone for when you want USB storage enabled. We now modify the runlevel 3 boot process to disable USB storage.)

[list=a]
[*] Tell your linux box what to do if it encounters the word "runlevel3" in its boot command:
```
gksu gedit /etc/event.d/rc-default
```
Change this:
```
	if grep -q -w -- "-s\|single\|S" /proc/cmdline; then
	    telinit S
	elif [ -r /etc/inittab ]; then
```

to
```
	if grep -q -w -- "-s\|single\|S" /proc/cmdline; then
	    telinit S
 	[B]elif grep -q -w -- "runlevel3" /proc/cmdline; then
	    telinit 3[/B]
	elif [ -r /etc/inittab ]; then
```

Save and Quit gedit.

[*] Put "runlevel3" in a new GRUB boot stanza:

```
gksu gedit /boot/grub/menu.lst
```

About 2/3 of the way down the file you will find something like this

```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed ro 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```
Make a duplicate copy of your boot stanza, and then modify the duplicate by changing the title to something like "No USB", and adding "runlevel3" to the end of the kernel line:

```
title		**No USB**
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed ro **runlevel3**
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```
Okay, now when you boot, you can press ESC to get to the GRUB menu, and you'll see both your regular boot line, and a "No USB" boot line. Now to make runlevel 3 do something different than runlevel 2:
[/list]

[*] Create a /etc/init.d/disable-usbstorage script
[list=a]
[*]```

gksu gedit /etc/init.d/disable-usbstorage
```

```
#! /bin/sh
PATH=/sbin:/bin:/usr/sbin:/usr/bin
. /lib/lsb/init-functions

case "$1" in
    start)
	umount /dev/sdbX
	modprobe -r usb-storage
        ;;
    stop)
	modprobe usb-storage
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

```
Change /dev/sdbX to the real device name of your USB storage device.

[*] Link the script to /etc/rc3.d, so it will be run in runlevel 3.
```
sudo ln -s /etc/init.d/disable-usbstorage /etc/rc3.d/S99disable-usbstorage
```
[/list]
[/list]

---

