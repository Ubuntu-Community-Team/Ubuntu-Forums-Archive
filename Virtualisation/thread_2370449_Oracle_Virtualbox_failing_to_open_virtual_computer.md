---
title: "Oracle Virtualbox failing to open virtual computers"
date: 2017-09-03
forum: Virtualisation
---

### Post by carega on 2017-09-03
Hello,

I've been trying to get Virtualbox to creat a virtualmachine and failed miserably every time. I have Virtualbox 5.1.26 installed (latest version) using their repositories. Whenever I try to start a virtual machine I get the following message:

>  Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

[COLOR=#0000ff]'/sbin/vboxconfig'[/COLOR]

as root.

where: suplibOsInit what: 3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On linux, open returned ENOENT. 



I also get this message:

> 
Fallo al abrir una sesión para la máquina virtual Mindows.

The virtual machine 'Mindows' has terminated unexpectedly during startup with exit code 1 (0x1).

Código Resultado: NS_ERROR_FAILURE (0x80004005)
Componente: MachineWrap
Interfaz: IMachine {b2547866-a0a1-4391-8b86-6952d82efaa0}


So I was very obedient and tried doing what was asked and got this:

```

$ sudo /sbin/vboxconfig
vboxdrv.sh: Stopping VirtualBox services.
vboxdrv.sh: Building VirtualBox kernel modules.
This system is not currently set up to build kernel modules (system extensions).
Running the following commands should set the system up correctly:

  apt-get install linux-headers-3.13.0-119-generic
(The last command may fail if your system is not fully updated.)
  apt-get install linux-headers-generic
vboxdrv.sh: failed: Look at /var/log/vbox-install.log to find out what went wrong.
This system is not currently set up to build kernel modules (system extensions).
Running the following commands should set the system up correctly:

  apt-get install linux-headers-3.13.0-119-generic
(The last command may fail if your system is not fully updated.)
  apt-get install linux-headers-generic

There were problems setting up VirtualBox.  To re-start the set-up process, run
  /sbin/vboxconfig
as root.

```

I ran the commands suggest and got the following messages:

```

Package linux-headers-3.13.0-119-generic is not available, but is referred to by another package. 
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package «linux-headers-3.13.0-119-generic» has no installation candidate

```

Regarding the linx-headers-generic it says it's already on its most recent version (4.4.0.93.98).

Could anyone help me with this? I've looked in many places on the internet but haven't found a solution yet.

---

### Post by carega on 2017-09-03
On /var/log/vbox-install.log I get the following output:

[https://paste.ubuntu.com/25459616/](https://paste.ubuntu.com/25459616/)

I have Ubuntu 16.04 by the way.

---

### Post by deadflowr on 2017-09-03
*Thread moved to **Virtualisation**.*

---

### Post by &amp;KyT$0P# on 2017-09-03
Please post the output from the following commands -
```
uname -a
dpkg-query -W | grep -P -i '^linux'
ls -la /boot
```

---

### Post by carega on 2017-09-03
Hello,

Here's the output requested:

```
carega@macross:~$ uname -a
Linux macross 3.13.0-119-generic #166-Ubuntu SMP Wed May 3 12:19:45 UTC 2017 i686 i686 i686 GNU/Linux
carega@macross:~$ dpkg-query -W | grep -P -i '^linux'
linux-base    4.0ubuntu1
linux-firmware    1.157.11
linux-goldfish-headers-3.4.0-4    3.4.0-4.27
linux-headers-3.4.0-4-goldfish    3.4.0-4.27
linux-headers-4.4.0-79    4.4.0-79.100
linux-headers-4.4.0-79-generic    4.4.0-79.100
linux-headers-4.4.0-93    4.4.0-93.116
linux-headers-4.4.0-93-generic    4.4.0-93.116
linux-headers-generic    4.4.0.93.98
linux-image-3.13.0-100-generic    3.13.0-100.147
linux-image-3.13.0-101-generic    3.13.0-101.148
linux-image-3.13.0-103-generic    3.13.0-103.150
linux-image-3.13.0-105-generic    3.13.0-105.152
linux-image-3.13.0-106-generic    3.13.0-106.153
linux-image-3.13.0-107-generic    3.13.0-107.154
linux-image-3.13.0-108-generic    3.13.0-108.155
linux-image-3.13.0-109-generic    3.13.0-109.156
linux-image-3.13.0-110-generic    3.13.0-110.157
linux-image-3.13.0-112-generic    3.13.0-112.159
linux-image-3.13.0-113-generic    3.13.0-113.160
linux-image-3.13.0-115-generic    3.13.0-115.162
linux-image-3.13.0-116-generic    3.13.0-116.163
linux-image-3.13.0-117-generic    3.13.0-117.164
linux-image-3.13.0-119-generic    3.13.0-119.166
linux-image-3.13.0-48-generic    3.13.0-48.80
linux-image-3.13.0-49-generic    3.13.0-49.83
linux-image-3.13.0-51-generic    3.13.0-51.84
linux-image-3.13.0-52-generic    3.13.0-52.86
linux-image-3.13.0-53-generic    3.13.0-53.89
linux-image-3.13.0-54-generic    3.13.0-54.91
linux-image-3.13.0-55-generic    3.13.0-55.94
linux-image-3.13.0-57-generic    3.13.0-57.95
linux-image-3.13.0-58-generic    3.13.0-58.97
linux-image-3.13.0-59-generic    3.13.0-59.98
linux-image-3.13.0-61-generic    3.13.0-61.100
linux-image-3.13.0-62-generic    3.13.0-62.102
linux-image-3.13.0-63-generic    3.13.0-63.103
linux-image-3.13.0-65-generic    3.13.0-65.106
linux-image-3.13.0-66-generic    3.13.0-66.108
linux-image-3.13.0-68-generic    3.13.0-68.111
linux-image-3.13.0-71-generic    3.13.0-71.114
linux-image-3.13.0-73-generic    3.13.0-73.116
linux-image-3.13.0-74-generic    3.13.0-74.118
linux-image-3.13.0-76-generic    3.13.0-76.120
linux-image-3.13.0-77-generic    3.13.0-77.121
linux-image-3.13.0-79-generic    3.13.0-79.123
linux-image-3.13.0-83-generic    3.13.0-83.127
linux-image-3.13.0-85-generic    3.13.0-85.129
linux-image-3.13.0-86-generic    3.13.0-86.131
linux-image-3.13.0-87-generic    3.13.0-87.133
linux-image-3.13.0-88-generic    3.13.0-88.135
linux-image-3.13.0-91-generic    3.13.0-91.138
linux-image-3.13.0-92-generic    3.13.0-92.139
linux-image-3.13.0-93-generic    3.13.0-93.140
linux-image-3.13.0-95-generic    3.13.0-95.142
linux-image-3.13.0-96-generic    3.13.0-96.143
linux-image-3.13.0-98-generic    3.13.0-98.145
linux-image-3.2.0-23-generic-pae    3.2.0-23.36
linux-image-3.2.0-32-generic-pae    3.2.0-32.51
linux-image-3.2.0-33-generic-pae    3.2.0-33.52
linux-image-3.2.0-34-generic-pae    3.2.0-34.53
linux-image-3.2.0-35-generic-pae    3.2.0-35.55
linux-image-3.2.0-36-generic-pae    3.2.0-36.57
linux-image-3.2.0-37-generic-pae    3.2.0-37.58
linux-image-3.2.0-38-generic-pae    3.2.0-38.61
linux-image-3.2.0-39-generic-pae    3.2.0-39.62
linux-image-3.2.0-40-generic-pae    3.2.0-40.64
linux-image-3.2.0-41-generic-pae    3.2.0-41.66
linux-image-3.2.0-43-generic-pae    3.2.0-43.68
linux-image-3.2.0-44-generic-pae    3.2.0-44.69
linux-image-3.2.0-45-generic-pae    3.2.0-45.70
linux-image-3.2.0-48-generic-pae    3.2.0-48.74
linux-image-3.2.0-49-generic-pae    3.2.0-49.75
linux-image-3.2.0-52-generic-pae    3.2.0-52.78
linux-image-3.2.0-53-generic-pae    3.2.0-53.81
linux-image-3.2.0-54-generic-pae    3.2.0-54.82
linux-image-3.2.0-55-generic-pae    3.2.0-55.85
linux-image-3.2.0-56-generic-pae    3.2.0-56.86
linux-image-3.2.0-57-generic-pae    3.2.0-57.87
linux-image-3.2.0-58-generic-pae    3.2.0-58.88
linux-image-3.2.0-59-generic-pae    3.2.0-59.90
linux-image-3.2.0-60-generic-pae    3.2.0-60.91
linux-image-3.2.0-61-generic-pae    3.2.0-61.93
linux-image-3.2.0-63-generic-pae    3.2.0-63.95
linux-image-3.2.0-64-generic-pae    3.2.0-64.97
linux-image-3.2.0-65-generic-pae    3.2.0-65.99
linux-image-3.2.0-67-generic-pae    3.2.0-67.101
linux-image-3.2.0-68-generic-pae    3.2.0-68.102
linux-image-3.2.0-69-generic-pae    3.2.0-69.103
linux-image-3.2.0-70-generic-pae    3.2.0-70.105
linux-image-3.2.0-72-generic-pae    3.2.0-72.107
linux-image-3.2.0-74-generic-pae    3.2.0-74.109
linux-image-3.2.0-75-generic-pae    3.2.0-75.110
linux-image-3.2.0-76-generic-pae    3.2.0-76.111
linux-image-3.2.0-77-generic-pae    3.2.0-77.114
linux-image-3.2.0-79-generic-pae    3.2.0-79.115
linux-image-4.4.0-79-generic    4.4.0-79.100
linux-image-extra-3.13.0-100-generic    3.13.0-100.147
linux-image-extra-3.13.0-101-generic    3.13.0-101.148
linux-image-extra-3.13.0-103-generic    3.13.0-103.150
linux-image-extra-3.13.0-105-generic    3.13.0-105.152
linux-image-extra-3.13.0-106-generic    3.13.0-106.153
linux-image-extra-3.13.0-107-generic    3.13.0-107.154
linux-image-extra-3.13.0-108-generic    3.13.0-108.155
linux-image-extra-3.13.0-109-generic    3.13.0-109.156
linux-image-extra-3.13.0-110-generic    3.13.0-110.157
linux-image-extra-3.13.0-112-generic    3.13.0-112.159
linux-image-extra-3.13.0-113-generic    3.13.0-113.160
linux-image-extra-3.13.0-115-generic    3.13.0-115.162
linux-image-extra-3.13.0-116-generic    3.13.0-116.163
linux-image-extra-3.13.0-117-generic    3.13.0-117.164
linux-image-extra-3.13.0-119-generic    3.13.0-119.166
linux-image-extra-3.13.0-48-generic    3.13.0-48.80
linux-image-extra-3.13.0-49-generic    3.13.0-49.83
linux-image-extra-3.13.0-51-generic    3.13.0-51.84
linux-image-extra-3.13.0-52-generic    3.13.0-52.86
linux-image-extra-3.13.0-53-generic    3.13.0-53.89
linux-image-extra-3.13.0-54-generic    3.13.0-54.91
linux-image-extra-3.13.0-55-generic    3.13.0-55.94
linux-image-extra-3.13.0-57-generic    3.13.0-57.95
linux-image-extra-3.13.0-58-generic    3.13.0-58.97
linux-image-extra-3.13.0-59-generic    3.13.0-59.98
linux-image-extra-3.13.0-61-generic    3.13.0-61.100
linux-image-extra-3.13.0-62-generic    3.13.0-62.102
linux-image-extra-3.13.0-63-generic    3.13.0-63.103
linux-image-extra-3.13.0-65-generic    3.13.0-65.106
linux-image-extra-3.13.0-66-generic    3.13.0-66.108
linux-image-extra-3.13.0-68-generic    3.13.0-68.111
linux-image-extra-3.13.0-71-generic    3.13.0-71.114
linux-image-extra-3.13.0-73-generic    3.13.0-73.116
linux-image-extra-3.13.0-74-generic    3.13.0-74.118
linux-image-extra-3.13.0-76-generic    3.13.0-76.120
linux-image-extra-3.13.0-77-generic    3.13.0-77.121
linux-image-extra-3.13.0-79-generic    3.13.0-79.123
linux-image-extra-3.13.0-83-generic    3.13.0-83.127
linux-image-extra-3.13.0-85-generic    3.13.0-85.129
linux-image-extra-3.13.0-86-generic    3.13.0-86.131
linux-image-extra-3.13.0-87-generic    3.13.0-87.133
linux-image-extra-3.13.0-88-generic    3.13.0-88.135
linux-image-extra-3.13.0-91-generic    3.13.0-91.138
linux-image-extra-3.13.0-92-generic    3.13.0-92.139
linux-image-extra-3.13.0-93-generic    3.13.0-93.140
linux-image-extra-3.13.0-95-generic    3.13.0-95.142
linux-image-extra-3.13.0-96-generic    3.13.0-96.143
linux-image-extra-3.13.0-98-generic    3.13.0-98.145
linux-image-extra-4.4.0-79-generic    4.4.0-79.100
linux-libc-dev:i386    4.4.0-93.116
linux-sound-base    1.0.25+dfsg-0ubuntu5
carega@macross:~$ ls -la /boot
total 70964
drwxr-xr-x  3 root root    20480 ago  2 12:54 .
drwxr-xr-x 23 root root     4096 jun 16 12:05 ..
-rw-r--r--  1 root root  1171026 may  3 11:14 abi-3.13.0-119-generic
-rw-r--r--  1 root root   805847 mar 12  2015 abi-3.2.0-79-generic-pae
-rw-r--r--  1 root root   170101 may  3 11:14 config-3.13.0-119-generic
-rw-r--r--  1 root root   147737 mar 12  2015 config-3.2.0-79-generic-pae
drwxr-xr-x  5 root root    12288 jul 31 17:38 grub
-rw-r--r--  1 root root 30892711 ago  2 12:54 initrd.img-3.13.0-119-generic
-rw-r--r--  1 root root 22921041 jun 16 11:07 initrd.img-3.2.0-79-generic-pae
-rw-r--r--  1 root root   182704 ene 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 ene 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 ene 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  2706722 may  3 11:14 System.map-3.13.0-119-generic
-rw-------  1 root root  2325436 mar 12  2015 System.map-3.2.0-79-generic-pae
-rw-------  1 root root  5868368 may  3 11:14 vmlinuz-3.13.0-119-generic
-rw-------  1 root root  5042720 mar 12  2015 vmlinuz-3.2.0-79-generic-pae

```

---

### Post by &amp;KyT$0P# on 2017-09-03
You're running Ubuntu 16.04, yet you are running a kernel version for Ubuntu 14.04, you have a **ton** of Ubuntu 12.04 and 14.04 kernels installed, and yet somehow the only kernels available to boot from are one for 12.04 and one for 14.04?

You have a much bigger problem than VirtualBox not working.

If this happened to me, I'd probably back everything up and do a clean reinstall.  I've no idea how to go about fixing that, sorry.

---

### Post by deadflowr on 2017-09-03
I have a feeling most of those from the dpkg-query output are rc'd, otherwise known as removed.
```
dpkg -l | grep linux | awk '/^rc/{print $1,$2}'
```
should show you if that's what is what.

---

### Post by carega on 2017-09-03
Here's the output requested:

```

carega@macross:~$ dpkg -l | grep linux | awk '/^rc/{print $1,$2}'
rc linux-image-3.13.0-100-generic
rc linux-image-3.13.0-101-generic
rc linux-image-3.13.0-103-generic
rc linux-image-3.13.0-105-generic
rc linux-image-3.13.0-106-generic
rc linux-image-3.13.0-107-generic
rc linux-image-3.13.0-108-generic
rc linux-image-3.13.0-109-generic
rc linux-image-3.13.0-110-generic
rc linux-image-3.13.0-112-generic
rc linux-image-3.13.0-113-generic
rc linux-image-3.13.0-115-generic
rc linux-image-3.13.0-116-generic
rc linux-image-3.13.0-117-generic
rc linux-image-3.13.0-48-generic
rc linux-image-3.13.0-49-generic
rc linux-image-3.13.0-51-generic
rc linux-image-3.13.0-52-generic
rc linux-image-3.13.0-53-generic
rc linux-image-3.13.0-54-generic
rc linux-image-3.13.0-55-generic
rc linux-image-3.13.0-57-generic
rc linux-image-3.13.0-58-generic
rc linux-image-3.13.0-59-generic
rc linux-image-3.13.0-61-generic
rc linux-image-3.13.0-62-generic
rc linux-image-3.13.0-63-generic
rc linux-image-3.13.0-65-generic
rc linux-image-3.13.0-66-generic
rc linux-image-3.13.0-68-generic
rc linux-image-3.13.0-71-generic
rc linux-image-3.13.0-73-generic
rc linux-image-3.13.0-74-generic
rc linux-image-3.13.0-76-generic
rc linux-image-3.13.0-77-generic
rc linux-image-3.13.0-79-generic
rc linux-image-3.13.0-83-generic
rc linux-image-3.13.0-85-generic
rc linux-image-3.13.0-86-generic
rc linux-image-3.13.0-87-generic
rc linux-image-3.13.0-88-generic
rc linux-image-3.13.0-91-generic
rc linux-image-3.13.0-92-generic
rc linux-image-3.13.0-93-generic
rc linux-image-3.13.0-95-generic
rc linux-image-3.13.0-96-generic
rc linux-image-3.13.0-98-generic
rc linux-image-3.2.0-23-generic-pae
rc linux-image-3.2.0-32-generic-pae
rc linux-image-3.2.0-33-generic-pae
rc linux-image-3.2.0-34-generic-pae
rc linux-image-3.2.0-35-generic-pae
rc linux-image-3.2.0-36-generic-pae
rc linux-image-3.2.0-37-generic-pae
rc linux-image-3.2.0-38-generic-pae
rc linux-image-3.2.0-39-generic-pae
rc linux-image-3.2.0-40-generic-pae
rc linux-image-3.2.0-41-generic-pae
rc linux-image-3.2.0-43-generic-pae
rc linux-image-3.2.0-44-generic-pae
rc linux-image-3.2.0-45-generic-pae
rc linux-image-3.2.0-48-generic-pae
rc linux-image-3.2.0-49-generic-pae
rc linux-image-3.2.0-52-generic-pae
rc linux-image-3.2.0-53-generic-pae
rc linux-image-3.2.0-54-generic-pae
rc linux-image-3.2.0-55-generic-pae
rc linux-image-3.2.0-56-generic-pae
rc linux-image-3.2.0-57-generic-pae
rc linux-image-3.2.0-58-generic-pae
rc linux-image-3.2.0-59-generic-pae
rc linux-image-3.2.0-60-generic-pae
rc linux-image-3.2.0-61-generic-pae
rc linux-image-3.2.0-63-generic-pae
rc linux-image-3.2.0-64-generic-pae
rc linux-image-3.2.0-65-generic-pae
rc linux-image-3.2.0-67-generic-pae
rc linux-image-3.2.0-68-generic-pae
rc linux-image-3.2.0-69-generic-pae
rc linux-image-3.2.0-70-generic-pae
rc linux-image-3.2.0-72-generic-pae
rc linux-image-3.2.0-74-generic-pae
rc linux-image-3.2.0-75-generic-pae
rc linux-image-3.2.0-76-generic-pae
rc linux-image-3.2.0-77-generic-pae
rc linux-image-4.4.0-79-generic
rc linux-image-extra-3.13.0-100-generic
rc linux-image-extra-3.13.0-101-generic
rc linux-image-extra-3.13.0-103-generic
rc linux-image-extra-3.13.0-105-generic
rc linux-image-extra-3.13.0-106-generic
rc linux-image-extra-3.13.0-107-generic
rc linux-image-extra-3.13.0-108-generic
rc linux-image-extra-3.13.0-109-generic
rc linux-image-extra-3.13.0-110-generic
rc linux-image-extra-3.13.0-112-generic
rc linux-image-extra-3.13.0-113-generic
rc linux-image-extra-3.13.0-115-generic
rc linux-image-extra-3.13.0-116-generic
rc linux-image-extra-3.13.0-117-generic
rc linux-image-extra-3.13.0-48-generic
rc linux-image-extra-3.13.0-49-generic
rc linux-image-extra-3.13.0-51-generic
rc linux-image-extra-3.13.0-52-generic
rc linux-image-extra-3.13.0-53-generic
rc linux-image-extra-3.13.0-54-generic
rc linux-image-extra-3.13.0-55-generic
rc linux-image-extra-3.13.0-57-generic
rc linux-image-extra-3.13.0-58-generic
rc linux-image-extra-3.13.0-59-generic
rc linux-image-extra-3.13.0-61-generic
rc linux-image-extra-3.13.0-62-generic
rc linux-image-extra-3.13.0-63-generic
rc linux-image-extra-3.13.0-65-generic
rc linux-image-extra-3.13.0-66-generic
rc linux-image-extra-3.13.0-68-generic
rc linux-image-extra-3.13.0-71-generic
rc linux-image-extra-3.13.0-73-generic
rc linux-image-extra-3.13.0-74-generic
rc linux-image-extra-3.13.0-76-generic
rc linux-image-extra-3.13.0-77-generic
rc linux-image-extra-3.13.0-79-generic
rc linux-image-extra-3.13.0-83-generic
rc linux-image-extra-3.13.0-85-generic
rc linux-image-extra-3.13.0-86-generic
rc linux-image-extra-3.13.0-87-generic
rc linux-image-extra-3.13.0-88-generic
rc linux-image-extra-3.13.0-91-generic
rc linux-image-extra-3.13.0-92-generic
rc linux-image-extra-3.13.0-93-generic
rc linux-image-extra-3.13.0-95-generic
rc linux-image-extra-3.13.0-96-generic
rc linux-image-extra-3.13.0-98-generic
rc linux-image-extra-4.4.0-79-generic

```

I'd like to note that when I first got this computer I installed Ubuntu 12.04 (I bought it back in 2012), then upgraded to 14.04 and 16.04 recently.

---

### Post by deadflowr on 2017-09-03
Yep, I thought so.

Also, I see you've tried, at one point, to install the 4.4 kernel series, but the image packages have since been removed.
You may still have the 4.4 headers package. They are listed in the first halogen2 requested output, but are not in the rc'd output I requested.

All that adds to some confusion, since the linux-image/headers-generic packages list them (in the halogen2 requested output) as for the 4.4 kernel series, is this Ubuntu 16.04?
If so, that makes sense that trying to install the 3.13.0-119 header package would fail.
It does not exist in 16.04.

I would try reinstalling the 4.4 image package and then reboot into that kernel.
You might try
```
sudo apt-get update
sudo apt-get install --reinstall linux-image-generic linux-headers-generic 
```
hopefully that should bring in both the proper image  and headers packages.
If not, run
```
sudo apt full-upgrade
```
this will update the whole system kernels and all.
You will need to reboot into the new kernel.

I hope this isn't confusing, I've had to re-edit this post a few times as I go back and forth through the earlier posts.
So I got lost here and there...

---

### Post by carega on 2017-09-04
So I think now we're getting close, thank you for that!. I could turn on the VM but it says "Error loading operating system"

Furthermore I got this message about a virtualbox-dkms 5.0.40-dfsg-0ubuntu1.16.04.1 package failing to install (although I didn't install anything). 

It says the package is "virtualbox-dkms (not installed)" and on Title it states "the virtualbox-dkms 5.... virtualbox kernel module failed to build"

Could this be the fault of the virtual machine itself or something else?

Oh and when I rebooted the computer (the real computer, not the VM mind you) it showed the following message "vboxclient - Kernel not running".

---

### Post by deadflowr on 2017-09-04
Hmm, it seems to think you have the Ubuntu repository version of virtualbox.
What does
```
dpkg -l | grep virtualbox | awk '{print $1,$2,$3}'
```
show you?

> Could this be the fault of the virtual machine itself or something else?
No, this all on the host side.
The vms should be safe, tucked away and ready to run whenever the host system figures itself out.

---

### Post by carega on 2017-09-07
Sorry for the delay, didn't notice there was a second page with your reply. Here's the output you requested:

```

carega@macross:~$ dpkg -l | grep virtualbox | awk '{print $1,$2,$3}'
ii unity-scope-virtualbox 0.1+13.10.20130723-0ubuntu1
ii virtualbox-5.1 5.1.26-117224~Ubuntu~xenial
rc virtualbox-guest-x11 5.0.40-dfsg-0ubuntu1.16.04.1

```

---

### Post by deadflowr on 2017-09-10
I wonder if a virtualbox-5.1 reinstall would be in order:
```
sudo apt-get install --reinstall virtualbox-5.1
```

The design of virtualbox places the vms inside the user's home folder, by default, and are untouched by apt.
So removing virtualbox or reinstalling virtualbox will not harm the vms.

I also wonder if the odd dkms and vboxclient messages seen were a result of having the guest-x11 package installed at some point.
(it's gone now, but I do not know when it was there)

---

### Post by carega on 2017-09-10
The same is happening. I'm attaching a screenshot of the VM so you can see the message.

---

### Post by carega on 2017-09-18
Bump

---

### Post by lammert-nijhof on 2017-09-19
If I ever saw a system; that really really needed a fresh install it is  yours. If you download Virtualbox 5.1.26 for Ubuntu 16.04, it will assume, that it has to integrate into Linux 4.4 or higher. That download of Virtualbox 5.1.26 would be incompatible with any Linux 3.x version, you seem to boot from and use as Linux kernel. 

The best solution would be to  re-install the host system and WIPE the system partition or the whole disk in the process after making  a back-up from all things you want to keep. First install all OS updates and afterwards you could  install Virtualbox 5.1.28 (newer) in a fresh and lean copy of Ubuntu. If during  the install it complains about missing dependencies, make sure that  those packages are installed too. Use Gdebi or the terminal for the  installation of Virtualbox. In future run from time to time e.g. "Ubuntu  Cleaner" to remove old stuff including old kernels from the system.

If re-installing and re-tuning your system and applications would take many many days, an alternative with say 33% chance of lasting success could be:

[LIST]
[*]Make a back-up and run (assuming that sda is your OS disk): 
[/LIST]
 > 
sudo grub-install /dev/sda   ;
sudo update-grub

 
[LIST]
[*]Look if Linux version 4.4 is part of the grub boot menu and BOOT from THAT 4.4 Linux kernel. 
[*]If you cannot boot from Linux 4.4 or anything else goes wrong in the process, re-install from scratch as proposed in the first paragraph. 
[*]Check the file /etc/apt/sources.list for any entries related to OTHER Ubuntu releases then "Xenial" and remove them (sudo gedit /etc/apt/sources.list) or re-install from scratch as proposed in the first paragraph. If "Xenial" is missing from the list, re-install from scratch. 
[*]Run the "Software Updater" to get the latest updates 
[*]Install "Ubuntu Cleaner" see OMG Ubuntu about where to find it or google for it. 
[*]Run "Ubuntu Cleaner" and remove all old junk 
[*]Download and install Virtualbox 5.1.28 and install all missing dependencies too. Use Gdebi or the terminal for the  installation of Virtualbox. 
[*]Download and install the Extension Pack 5.1.28 
[/LIST]

---

### Post by deadflowr on 2017-09-19
The issue of *Error loading operating system* is one of two possible causes.
The first is likely improper disk controller settings:
[https://www.virtualbox.org/manual/ch05.html]("https://www.virtualbox.org/manual/ch05.html")
[https://forums.virtualbox.org/viewtopic.php?f=7&t=56195]("https://forums.virtualbox.org/viewtopic.php?f=7&t=56195")
windows is more susceptible to this since any change in the disk controller settings can break the boot loader.

The second might be a busted boot sector.
Or at least that's the common cause of the Error loading operating system.
Might look over this:
[https://help.ubuntu.com/community/BootSectorFix]("https://help.ubuntu.com/community/BootSectorFix")
Though I'm not sure about it happening inside a vm.

---

### Post by lammert-nijhof on 2017-09-19
@deadflowr: Sorry. Carega is booting from a v3.13 Linux kernel and has Virtualbox 5.1.26 downloaded and installed for Ubuntu 16.04 and Linux v4.4. See one of his error messages and what he thinks is installed.
> This system is not currently set up to build kernel modules (system extensions).
Running the following commands should set the system up correctly:

  apt-get install linux-headers-3.13.0-119-generic
 and see his remark:
> I'd like to note that when I first got this computer I installed Ubuntu  12.04 (I bought it back in 2012), then upgraded to 14.04 and 16.04  recently.                 
His version of Virtualbox is simply incompatible with his version of Linux and since Virtualbox is tightly integrated into the OS, loading a VM must result in errors. He has still a ton of Linux versions installed. The best advice we can give him is to re-install Ubuntu 16.04 from scratch, I hope you agree after this explanation.

---

### Post by carega on 2017-09-25
Guys, thanks for your responses and your concern on solving my issue. I think I'm gonna go with a fresh reinstall of Ubuntu and see how it goes from there. I'll post again once I do it but I'm kind of busy and don't have the time for that right now.

---

### Post by carega on 2017-10-05
Hello again.

So I took [**[COLOR=#000000]lammert-nijhof[/COLOR]**]("https://ubuntuforums.org/member.php?u=1949495")'s advice and decided to format the whole computer because I felt I would probably get into *other* problems in the future due to the things he mentioned. However, upon the new install I tried to run the virtual machine with Windows 2000 in it and got the following mistake... (image attached).

Could this be the fault of the VM? Is there a way I can find out?

[ATTACH=CONFIG]276999[/ATTACH]

---

