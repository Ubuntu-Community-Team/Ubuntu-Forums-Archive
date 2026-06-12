---
title: "Upgrading kernel, but still booting into old (removed) kernel"
date: 2016-10-21
forum: Server Platforms
---

### Post by smllms on 2016-10-21
In response to Dirty COW I upgraded my remote server's linux image, but the the server is rebooting into the old (removed) image. I'm mystified as to how this can be.

I'd like to boot into 3.13.0-100. How to go about updating to the correct image? 

Thanks!

Output of uname:
```
root@svr01:~# uname -mrs
Linux 3.13.0-43-generic x86_64
```

Output of dpkg with images installed/marked for removal:
```
root@svr01:~# dpkg --list | grep linux
ii  libselinux1:amd64                    2.2.2-1ubuntu0.1                  amd64        SELinux runtime shared libraries
ii  linux-firmware                       1.127.22                          all          Firmware for Linux kernel drivers
ii  linux-generic                        3.13.0.100.108                    amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-100             3.13.0-100.147                    all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-100-generic     3.13.0-100.147                    amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                3.13.0.100.108                    amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-100-generic       3.13.0-100.147                    amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-32-generic        3.13.0-32.57                      amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-36-generic        3.13.0-36.63                      amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-37-generic        3.13.0-37.64                      amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-43-generic        3.13.0-43.72                      amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-100-generic 3.13.0-100.147                    amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic  3.13.0-32.57                      amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-36-generic  3.13.0-36.63                      amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-37-generic  3.13.0-37.64                      amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-43-generic  3.13.0-43.72                      amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                  3.13.0.100.108                    amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                 3.13.0-100.147                    amd64        Linux Kernel Headers for development
ii  util-linux                           2.20.1-5.1ubuntu20.7              amd64
```

---

### Post by darkod on 2016-10-21
It should update grub with the new kernel automatically on kernel installation but maybe it somehow failed. Try running:
```
sudo update-grub
```

It will list all kernels detected and added into grub, check if -100 is there.

---

### Post by smllms on 2016-10-21
Thanks but I still booting into kernel 3.13.0-43 :(
Anything else I could try?

Output from grub-update:
```
root@svr01:~# update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-100-generic
Found initrd image: /boot/initrd.img-3.13.0-100-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
```

Output of ls /boot/
```
drwxr-xr-x  3 root root     4096 Oct 21 02:24 .
drwxr-xr-x 22 root root     4096 Oct 21 16:24 ..
-rw-r--r--  1 root root  1166518 Oct 18 11:04 abi-3.13.0-100-generic
-rw-r--r--  1 root root   165931 Oct 18 11:04 config-3.13.0-100-generic
drwxr-xr-x  5 root root     4096 Oct 21 16:24 grub
-rw-r--r--  1 root root 19368068 Oct 21 01:36 initrd.img-3.13.0-100-generic
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3395101 Oct 18 11:04 System.map-3.13.0-100-generic
-rw-------  1 root root  5836896 Oct 18 11:04 vmlinuz-3.13.0-100-generic
```

Output of /etc/default/grub
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1
```

---

### Post by darkod on 2016-10-22
Strange...

According to this you only have kernel -100. How can it be booting -43, I've never seen anything similar before.

How about purging -100 and reinstalling it?
```
sudo apt-get purge linux-image-3.13.0-100-generic
sudo apt-get install linux-image-3.13.0-100-generic
```

---

