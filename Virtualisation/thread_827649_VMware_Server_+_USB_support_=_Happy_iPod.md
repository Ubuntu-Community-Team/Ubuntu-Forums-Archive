---
title: "VMware Server + USB support = Happy iPod"
date: 2008-06-13
forum: Virtualisation
---

### Post by komputes on 2008-06-13
Beside having to delete /etc/vmware and usr/lib/vmware from a failed installation of a previous version, this instalation from source was rather painless, I must admit. I had to do a little bit of research but everything works fine now. I can use iTunes to sync my iPod with little issues, well besides the fact that it is running at usb 1.0 speeds - very slow. This is how I got it done:

1) Download VMWare Server 1.0.6
```
wget -c http://download3.vmware.com/software/vmserver/VMware-server-1.0.6-91891.tar.gz
```
2) Download packages necessary for compiling VMware:
```
$ sudo aptitude install build-essential linux-kernel-devel linux-headers-generic xinetd linux-headers-`uname -r`
```
3) Register/Generate a Serial Number
[http://register.vmware.com/content/registration.html](http://register.vmware.com/content/registration.html)

(I registered 100 of them)
This one for example: 92MK1-YUZ6W-2FQEL-406HM


4) Install/Configure - Answer all questions when running vmware-install.pl

```
$ tar xf VMware-server-1.0.6-*.tar.gz
$ cd vmware-server-distrib
$ sudo ./vmware-install.pl

```## If you are asked where your linux headers include files are they should be in /usr/src/linux-headers-`uname -r`/include/
## If that directory does not exist then run: 
sudo apt-get install linux-headers-`uname -r`


5) VMware will need to access cairo libraries and gcc. Create a symbolic
link.

```
$ sudo ln -sf /usr/lib/gcc/i486-linux-gnu/4.2.3/libgcc_s.so /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
$ sudo ln -sf /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0 
```Ubuntu does not mounting USBFS to /proc/bus/usb.  The virtual machine's USB back end uses this to detect USB devices that are attached to the host. To work around this issue, mount USBFS to /proc/bus/usb. To do this while the host is running, execute the following command as root:

```
$ sudo mount -t usbfs none /proc/bus/usb

```You need to power cycle the virtual machines after the mount command to have access to available USB devices. To configure the host to mount USBFS automatically on bootup, add the  following line in the /etc/fstab file:

```
usbfs  /proc/bus/usb  usbfs  auto  0  0
```If this line is already present in /etc/fstab, it likely has the noauto option set in the options column (4th column). Change this to auto.

---

### Post by salutis on 2008-10-21
[COLOR="Red"]T[/COLOR][COLOR="Blue"]h[/COLOR][COLOR="DarkGreen"]a[/COLOR][COLOR="Indigo"]n[/COLOR][COLOR="Sienna"]k[/COLOR][COLOR="DarkSlateGray"]s[/COLOR]!

---

