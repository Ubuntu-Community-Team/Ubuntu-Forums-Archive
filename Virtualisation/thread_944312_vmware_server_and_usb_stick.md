---
title: "vmware server and usb stick"
date: 2008-10-11
forum: Virtualisation
---

### Post by StOoZ on 2008-10-11
when I plug in my usb stick , ubuntu 8.04 recognizes it , but windows xp in vmware , doesnt , any idea how to solve it?

10x.

---

### Post by fjgaude on 2008-10-12
Uncomment lines 42-45 starting with #mkdir -p /dev/bus/usb/.usbfs like so:

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

to look like this:

```
    	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

Then place in the /etc/fstab file these lines:

```
usbfs /proc/bus/usb usbfs auto 0 0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

That should do it.

---

### Post by paris_alex on 2008-10-13
depending on whether you're using vmware workstation, player or server.. there should be a button somewhere to save 'connect' the specific usb device to the vmware guest.

It's usually, on the vmware guest OS's window. However, in VMWare Server 2.0, it is in the web administration console.

fjgaude, please don't take this the wrong way... but while the solution you posted might work.. it looks so complicated...geeky... hey....maybe i should try it! Cheers! ;-)

---

### Post by fjgaude on 2008-10-13
> **paris_alex said:**
> depending on whether you're using vmware workstation, player or server.. there should be a button somewhere to save 'connect' the specific usb device to the vmware guest.

It's usually, on the vmware guest OS's window. However, in VMWare Server 2.0, it is in the web administration console.

fjgaude, please don't take this the wrong way... but while the solution you posted might work.. it looks so complicated...geeky... hey....maybe i should try it! Cheers! ;-)

Beleive me, for some it has been the only way to get VMware and VBox to recognize USB devices.

Just in case, in the Windows VM, go to the VM tab, Removable Devices, then click the USB tab. That should show your devices, if any.

---

### Post by beyboo on 2008-11-02
[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=3862823](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=3862823)

---

