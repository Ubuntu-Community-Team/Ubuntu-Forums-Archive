---
title: "KVM/qemu Help!"
date: 2010-03-18
forum: Server Platforms
---

### Post by Face_Man on 2010-03-18
Hello all,

I am running Ubuntu 9.10 server and have enabled virtualization using KVM. I was able to install Win7 bit 32 as a guest, however, I am having some problems. 

1- Viewing the guest operating system :

if I try to view the guest OS from the Host using this command
```

	sudo qemu -vga std ~/Images/Win7.img -m 2048 -boot c  

```
I get this :
```

	(*) DirectFB/Core: Single Application Core. (2009-06-02 06:26) 
	(*) Direct/Memcpy: Using Generic 64bit memcpy()
	(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
	    --> No such file or directory
	(!) DirectFB/FBDev: Error opening framebuffer device!
	(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
	(!) DirectFB/Core: Could not initialize 'system_core' core!
	    --> Initialization error!
	Could not initialize SDL – exiting

```
after some research I found out that I can access the Host from workstation (Ubuntu 9.10 Desktop) using 
```
	
        ssh -X user@host

```
however, the mouse movement is too slow. Therefore, is there is a better way to view the guest OS or I am  missing something.


2- Add a USB Bluetooth Device to the Guest OS
using this command :
```

	sudo qemu -vga std ~/Images/Win7.img -m 2048 -usbdevice bt -bt hci,null  -boot c -usb -usbdevice tablet 

```
However, when login to the Guest OS, the device is there but it say on Device Status :
```

	Windows has stopped this device because it has reported problem. (Code 43)

```


Any help would be much appreciated.

---

### Post by Face_Man on 2010-03-19
Anyone!

---

