---
title: "cant access usb devices in vmware server"
date: 2008-10-15
forum: Virtualisation
---

### Post by unseenbeing on 2008-10-15
i have been trying to get my zune to work in vmware but i cant get my usb to work. how do i go about fixing this.

also no sound

---

### Post by darco on 2008-10-16
You have to make sure its enabled in the Settings....you may need to use the ADD button to find your devices....check the box and you should be good to go

darco

---

### Post by unseenbeing on 2008-10-16
i have added the usb but it still cant see my zune

---

### Post by unseenbeing on 2008-10-25
bump

i still need help

---

### Post by fjgaude on 2008-10-26
Uncomment lines 42-45 starting with #mkdir -p /dev/bus/usb/.usbfs

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Like so:

```
    	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

Then place in the fstab file this line:

```
usbfs /proc/bus/usb usbfs auto 0 0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

That will likely fix your issues.

---

### Post by beyboo on 2008-11-02
I had the same problem and found an easy solution here

[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=3862823](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=3862823)

---

