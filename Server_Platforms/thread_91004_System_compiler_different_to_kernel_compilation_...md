---
title: "System compiler different to kernel compilation .."
date: 2005-11-16
forum: Server Platforms
---

### Post by dbee on 2005-11-16
> 
Your kernel was built with "gcc" version "3.4.5", while you are trying to use
"/usr/bin/gcc" version "4.0.2". This configuration is not supported and VMware
Workstation cannot work in such configuration. Please either recompile your
kernel with "/usr/bin/gcc" version "4.0.2", or restart /usr/bin/vmware-config.pl
with CC environment variable pointing to the "gcc" version "3.4.5".

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.



... hmmm ... is this just an ubuntu64 thing or is this normal ?

I'm installing vmware btw

---

### Post by dbee on 2005-11-16
So I downloaded gcc-3.4.5 off synaptic and then I 
```

export "CC=gcc-3.4.5"

```
... there was no CC environment variable there originally so I don't really know what form it would take. 

I'm running a perl script by the way and the script doesn't seem to be too forth coming as to what form it's expecting. 

I'd rather not have to recompile the kernel, from what I know of ubuntu - it seems like it would be compiled with that gcc for a reason.

---

### Post by tseliot on 2005-11-16
Try this:

```
sudo passwd root
```
(and set the root password which you will need later)

then

```
su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC
```

Now you can launch the command which failed before.

---

### Post by dbee on 2005-11-16
```

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

```
... thanks tseliot, now it can't find the header files though  :confused:

---

### Post by LordHunter317 on 2005-11-16
Install the correct kernel-headers package.

CC in the form you descried is fine.  tseliot's instructions will work, but running the command as root is rather pointless, as it doesn nothing.

---

### Post by tseliot on 2005-11-16
[QUOTE=dbee]```

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

```
... thanks tseliot, now it can't find the header files though  :confused:[/QUOTE]
Type
```
sudo apt-get install linux-headers-'uname -r'
```

---

### Post by tseliot on 2005-11-16
[QUOTE=LordHunter317]Install the correct kernel-headers package.

CC in the form you descried is fine.  tseliot's instructions will work, but running the command as root is rather pointless, as it doesn nothing.[/QUOTE]
I completely agree with you, at least in theory. Nonetheless sometimes the command doesn't work if you aren't root. I don't know why but some users I have helped to "export CC" had this problem (this step is required to compile a kernel and also to compile the nvidiamodules).

---

### Post by LordHunter317 on 2005-11-16
[QUOTE=tseliot]I completely agree with you, at least in theory. Nonetheless sometimes the command doesn't work if you aren't root.[/quote]Yes, but exporting CC as root and immediately logging out does nothing.

---

### Post by tseliot on 2005-11-16
[QUOTE=LordHunter317]Yes, but exporting CC as root and immediately logging out does nothing.[/QUOTE]

I'm not the only one to suggest that step. Some months ago I thought exactly the same thing as you.

Have a look at Arnieboy's thread [http://www.ubuntuforums.org/showthread.php?t=75284&highlight=webcam]("http://www.ubuntuforums.org/showthread.php?t=75284&highlight=webcam")

Look at the 2nd step. Perhaps you should ask him an explanation. I'm not an expert (I have used Linux for 6-7 months) but Arnieboy definitely is.

---

### Post by LordHunter317 on 2005-11-16
As am I, and the minute you run exit, that shell session is destroyed and the environment it created is too.

---

### Post by dbee on 2005-11-16
> 
Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.12-9-amd64-generic/build/include/.. SUBDIRS=$PWD SRCROO T=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-amd64-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
/tmp/vmware-config0/vmmon-only/linux/driver.c:33:25: asm/ioctl32.h: No such file  or directory
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function `register_ioctl32_han dlers':
/tmp/vmware-config0/vmmon-only/linux/driver.c:222: warning: implicit declaration  of function `register_ioctl32_conversion'
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function `unregister_ioctl32_h andlers':
/tmp/vmware-config0/vmmon-only/linux/driver.c:248: warning: implicit declaration  of function `unregister_ioctl32_conversion'
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-amd64-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


... so I compleleted the earlier tasks and now I'm getting this error. There's nothing on the vmware site that seems to help. I have a look for ioctl32.h and it gives me
```

root@ubuntu64:/home/babo/Desktop/vmware-distrib# slocate ioctl32.h
/usr/include/linux/ioctl32.h
/usr/include/asm/ioctl32.h
/usr/include/asm-i386/ioctl32.h
/usr/include/asm-x86_64/ioctl32.h

```

---

### Post by dbee on 2005-11-21
Working on the new computer again today, and I still have a problem with vmware - which I need to solve so that I can move off my P3 ...

Does anyone have any idea what I do next 
I found this solution on the net - but it's for SUSE
```

cd /usr/src/linux
make cloneconfig
make modules_prepare
/usr/bin/vmware-config.pl 

```

... I've got the linux-header files in my /usr/src directory but no corresponding makefiles on my ubuntu

---

