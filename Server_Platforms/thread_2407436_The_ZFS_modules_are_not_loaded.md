---
title: "The ZFS modules are not loaded"
date: 2018-12-04
forum: Server Platforms
---

### Post by ehamdja on 2018-12-04
[FONT=arial]Please help, was trying to install and create zfs pool but received this error:

[/FONT][COLOR=#000000][FONT=&quot][FONT=arial]The ZFS modules are not loaded.                                                                                                [/FONT][/FONT][/COLOR]
[FONT=arial][COLOR=#000000]Try running '/sbin/modprobe zfs' as root to load them.

When trying to run /sbin/modprobe zfs, received this msg:

modprobe: FATAL: Module zfs not found in directory /lib/modules/3.10.106-153

anybody can help? Thank you in advance.[/COLOR][/FONT]

---

### Post by darkod on 2018-12-04
Which ubuntu server version are you running? Zfs was included not so long ago so it wouldnt exist in old versions.

---

### Post by ehamdja on 2018-12-05
I'm running ubuntu 16.04.5 LTS

---

### Post by darkod on 2018-12-05
Can you post the outputs of the following commands:
```
apt-cache policy zfsutils-linux
apt-cache policy zfs-initramfs
uname -a
apt-cache policy linux-generic-hwe-16.04
```

---

### Post by ehamdja on 2018-12-06
```

[COLOR=#000000][FONT=&amp]zfsutils-linux:                                                                                                                [/FONT][/COLOR]  
Installed: 0.6.5.6-0ubuntu26                                                                                                 
Candidate: 0.6.5.6-0ubuntu26                                                                                                 
Version table:                                                                                                               
 *** 0.6.5.6-0ubuntu26 500                                                                                                     
        500 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main armhf Packages                                            
        100 /var/lib/dpkg/status                                                                                               
     0.6.5.6-0ubuntu8 500                                                                                                      
[COLOR=#000000][FONT=&amp]        500 [/FONT][/COLOR][http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)[COLOR=#000000][FONT=&amp] xenial/universe armhf Packages[/FONT][/COLOR]
```

```

[COLOR=#000000][FONT=&amp]  zfs-initramfs:                                                                                                                 [/FONT][/COLOR]  
 Installed: (none)                                                                                                            
  Candidate: 0.6.5.6-0ubuntu26                                                                                                 
  Version table:                                                                                                               
     0.6.5.6-0ubuntu26 500                                                                                                     
        500 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/universe armhf Packages                                        
     0.6.5.6-0ubuntu8 500                                                                                                      
[COLOR=#000000][FONT=&amp]        500 [/FONT][/COLOR][http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)[COLOR=#000000][FONT=&amp] xenial/universe armhf Packages[/FONT][/COLOR]
```

```
[COLOR=#000000][FONT=&amp]Linux erickh-odroidXU4 3.10.106-153 #1 SMP PREEMPT Mon Jun 4 01:19:38 UTC 2018 armv7l armv7l armv7l GNU/Linux[/FONT][/COLOR]
```

```

[COLOR=#000000][FONT=&amp]  linux-generic-hwe-16.04:                                                                                                       [/FONT][/COLOR]  
  Installed: (none)                                                                                                            
  Candidate: 4.15.0.42.63                                                                                                      
  Version table:                                                                                                               
     4.15.0.42.63 500                                                                                                          
        500 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main armhf Packages                                            
[COLOR=#000000][FONT=&amp]        500 [/FONT][/COLOR][http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)[COLOR=#000000][FONT=&amp] xenial-security/main armhf Packages[/FONT][/COLOR]
```

---

### Post by darkod on 2018-12-06
I didn't realize you are running on ARM.

I think you need to have that package zfs-initramfs so that modules are automatically created for new kernels. I think this is why you don't have modules to autoload. You never installed that package. It should be installed together with zfs.

Also I would install the linux-generic-hwe-16.04 which can provide newer kernels (if available). You should do it with the following command (there is small difference compared to standard apt-get install):
```
sudo apt-get install --install-recommends linux-generic-hwe-16.04
```

More info: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by ehamdja on 2018-12-06
as you recommended I was able to install [COLOR=#000000][FONT=&amp]zfs-initramfs[/FONT][/COLOR] but when I tried to do [COLOR=#000000][FONT=&amp]sudo apt-get install --install-recommends linux-generic-hwe-16.04
[/FONT][/COLOR]I got this
```
[COLOR=#000000][FONT=&amp]Get:1 [/FONT][/COLOR][http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)[COLOR=#000000][FONT=&amp] xenial/main armhf devio armhf 1.2-1build2 [16.4 kB]
[/FONT][/COLOR]Get:2 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main armhf flash-kernel armhf 3.0~rc.4ubuntu62.2 [18.1 kB]
Get:3 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main armhf linux-firmware all 1.157.21 [49.8 MB]
Get:4 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main armhf linux-modules-4.15.0-42-generic armhf 4.15.0-42.45~16.04.1
 [43.4 MB]                                                                                                                     
Get:5 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main armhf linux-image-4.15.0-42-generic armhf 4.15.0-42.45~16.04.1 [
8176 kB]                                                                                                                       
Get:6 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main armhf linux-image-generic-hwe-16.04 armhf 4.15.0.42.63 [2420 B]
Get:7 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main armhf linux-headers-4.15.0-42 all 4.15.0-42.45~16.04.1 [11.0 MB]
Get:8 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main armhf linux-headers-4.15.0-42-generic armhf 4.15.0-42.45~16.04.1
 [827 kB]                                                                                                                      
Get:9 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main armhf linux-headers-generic-hwe-16.04 armhf 4.15.0.42.63 [2414 B
]                                                                                                                              
Get:10 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main armhf linux-generic-hwe-16.04 armhf 4.15.0.42.63 [1802 B]
Fetched 113 MB in 40s (2790 kB/s)
Selecting previously unselected package devio.                                                                                 
(Reading database ... 93211 files and directories currently installed.)                                                        
Preparing to unpack .../devio_1.2-1build2_armhf.deb ...                                                                        
Unpacking devio (1.2-1build2) ...                                                                                              
Selecting previously unselected package flash-kernel.                                                                          
Preparing to unpack .../flash-kernel_3.0~rc.4ubuntu62.2_armhf.deb ...                                                          
Unpacking flash-kernel (3.0~rc.4ubuntu62.2) ...                                                                                
Selecting previously unselected package linux-firmware.                                                                        
Preparing to unpack .../linux-firmware_1.157.21_all.deb ...                                                                    
Unpacking linux-firmware (1.157.21) ...                                                                                        
Selecting previously unselected package linux-modules-4.15.0-42-generic.                                                       
Preparing to unpack .../linux-modules-4.15.0-42-generic_4.15.0-42.45~16.04.1_armhf.deb ...                                     
Unpacking linux-modules-4.15.0-42-generic (4.15.0-42.45~16.04.1) ...                                                           
Selecting previously unselected package linux-image-4.15.0-42-generic.                                                         
Preparing to unpack .../linux-image-4.15.0-42-generic_4.15.0-42.45~16.04.1_armhf.deb ...                                       
Unpacking linux-image-4.15.0-42-generic (4.15.0-42.45~16.04.1) ...                                                             
Selecting previously unselected package linux-image-generic-hwe-16.04.                                                         
Preparing to unpack .../linux-image-generic-hwe-16.04_4.15.0.42.63_armhf.deb ...                                               
Unpacking linux-image-generic-hwe-16.04 (4.15.0.42.63) ...                                                                     
Selecting previously unselected package linux-headers-4.15.0-42.                                                               
Preparing to unpack .../linux-headers-4.15.0-42_4.15.0-42.45~16.04.1_all.deb ...                                               
Unpacking linux-headers-4.15.0-42 (4.15.0-42.45~16.04.1) ...                                                                   
Selecting previously unselected package linux-headers-4.15.0-42-generic.                                                       
Preparing to unpack .../linux-headers-4.15.0-42-generic_4.15.0-42.45~16.04.1_armhf.deb ...                                     
Unpacking linux-headers-4.15.0-42-generic (4.15.0-42.45~16.04.1) ...                                                           
Selecting previously unselected package linux-headers-generic-hwe-16.04.                                                       
Preparing to unpack .../linux-headers-generic-hwe-16.04_4.15.0.42.63_armhf.deb ...                                             
Unpacking linux-headers-generic-hwe-16.04 (4.15.0.42.63) ...                                                                   
Selecting previously unselected package linux-generic-hwe-16.04.                                                               
Preparing to unpack .../linux-generic-hwe-16.04_4.15.0.42.63_armhf.deb ...                                                     
Unpacking linux-generic-hwe-16.04 (4.15.0.42.63) ...                                                                           
Setting up devio (1.2-1build2) ...                                                                                             
Setting up flash-kernel (3.0~rc.4ubuntu62.2) ...                                                                               
Setting up linux-firmware (1.157.21) ...                                                                                       
update-initramfs: Generating /boot/initrd.img-3.10.106-153                                                                     
Ignoring old or unknown version 3.10.106-153 (latest is 4.15.0-42-generic)                                                     
update-initramfs: Generating /boot/initrd.img-3.10.96+                                                                         
WARNING: missing /lib/modules/3.10.96+                                                                                         
Ensure all necessary drivers are built into the linux image!                                                                   
depmod: ERROR: could not open directory /lib/modules/3.10.96+: No such file or directory                                       
depmod: FATAL: could not search modules: No such file or directory                                                             
depmod: WARNING: could not open /var/tmp/mkinitramfs_GIwPGx/lib/modules/3.10.96+/modules.order: No such file or directory      
depmod: WARNING: could not open /var/tmp/mkinitramfs_GIwPGx/lib/modules/3.10.96+/modules.builtin: No such file or directory    
Ignoring old or unknown version 3.10.96+ (latest is 4.15.0-42-generic)                                                         
Setting up linux-modules-4.15.0-42-generic (4.15.0-42.45~16.04.1) ...                                                          
depmod: FATAL: could not load /boot/System.map-4.15.0-42-generic: No such file or directory                                    
Setting up linux-image-4.15.0-42-generic (4.15.0-42.45~16.04.1) ...                                                            
I: /boot/vmlinuz.old is now a symlink to vmlinuz-3.10.106-153                                                                  
I: /boot/initrd.img.old is now a symlink to initrd.img-3.10.106-153                                                            
I: /boot/vmlinuz is now a symlink to vmlinuz-4.15.0-42-generic                                                                 
I: /boot/initrd.img is now a symlink to initrd.img-4.15.0-42-generic                                                           
Setting up linux-image-generic-hwe-16.04 (4.15.0.42.63) ...                                                                    
Setting up linux-headers-4.15.0-42 (4.15.0-42.45~16.04.1) ...                                                                  
Setting up linux-headers-4.15.0-42-generic (4.15.0-42.45~16.04.1) ...                                                          
/etc/kernel/header_postinst.d/dkms:                                                                                            
configure: error: unknown                                                                                                      
Error! Bad return status for module build on kernel: 4.15.0-42-generic (armv7l)                                                
Consult /var/lib/dkms/spl/0.6.5.6/build/make.log for more information.                                                         
configure: error:                                                                                                              
        *** Please make sure the kmod spl devel <kernel> package for your                                                      
        *** distribution is installed then try again.  If that fails you                                                       
        *** can specify the location of the spl objects with the                                                               
        *** '--with-spl-obj=PATH' option.                                                                                      
Error! Bad return status for module build on kernel: 4.15.0-42-generic (armv7l)                                                
Consult /var/lib/dkms/zfs/0.6.5.6/build/make.log for more information.                                                         
Setting up linux-headers-generic-hwe-16.04 (4.15.0.42.63) ...                                                                  
Setting up linux-generic-hwe-16.04 (4.15.0.42.63) ...                                                                          
Processing triggers for linux-image-4.15.0-42-generic (4.15.0-42.45~16.04.1) ...                                               
/etc/kernel/postinst.d/dkms:                                                                                                   
configure: error: unknown                                                                                                      
Error! Bad return status for module build on kernel: 4.15.0-42-generic (armv7l)                                                
Consult /var/lib/dkms/spl/0.6.5.6/build/make.log for more information.                                                         
configure: error:                                                                                                              
        *** Please make sure the kmod spl devel <kernel> package for your                                                      
        *** distribution is installed then try again.  If that fails you                                                       
        *** can specify the location of the spl objects with the                                                               
        *** '--with-spl-obj=PATH' option.                                                                                      
Error! Bad return status for module build on kernel: 4.15.0-42-generic (armv7l)                                                
Consult /var/lib/dkms/zfs/0.6.5.6/build/make.log for more information.                                                         
/etc/kernel/postinst.d/initramfs-tools:                                                                                        
update-initramfs: Generating /boot/initrd.img-4.15.0-42-generic                                                                
flash-kernel: deferring update (trigger activated)                                                                             
/etc/kernel/postinst.d/uInitrd:                                                                                                
Image Name:   uInitrd                                                                                                          
Created:      Thu Dec  6 10:24:28 2018                                                                                         
Image Type:   ARM Linux RAMDisk Image (uncompressed)                                                                           
Data Size:    46796432 Bytes = 45699.64 kB = 44.63 MB                                                                          
Load Address: 00000000                                                                                                         
Entry Point:  00000000                                                                                                         
/etc/kernel/postinst.d/zz-flash-kernel:                                                                                        
flash-kernel: deferring update (trigger activated)                                                                             
Processing triggers for flash-kernel (3.0~rc.4ubuntu62.2) ...                                                                  
Unsupported platform.                                                                                                          
dpkg: error processing package flash-kernel (--configure):                                                                     
 subprocess installed post-installation script returned error exit status 1                                                    
Errors were encountered while processing:                                                                                      
 flash-kernel                                                                                                                  
E: Sub-process /usr/bin/dpkg returned an error code (1)                                                                        
erickh@erickh-odroidXU4:~$ sudo zpool create OdroidPool mirror /dev/sdb /dev/sdc                                               
The ZFS modules are not loaded.                                                                                                
Try running '/sbin/modprobe zfs' as root to load them.                                                                         
erickh@erickh-odroidXU4:~$ sudo /sbin/modprobe zfs                                                                             
[COLOR=#000000][FONT=&amp]modprobe: FATAL: Module zfs not found in directory /lib/modules/3.10.106-153[/FONT][/COLOR]
```

---

### Post by darkod on 2018-12-06
Did you check that log file that is telling you to consult?

It also depends whether you are installing kernels manually of they are supported through the standard repositories. It also says "Unsupported platform" in there.

---

### Post by ehamdja on 2018-12-09
I was trying to check about log file that is telling to consult but I restart the server and now can't even load. I don't know what happened when trying to install the generic kernel. What can I do at this point?

---

### Post by darkod on 2018-12-09
In the grub menu use the advanced ubuntu options and try loading older kernel. You can even try with the first one you have in the list. That one might have the zfs modules.
You were missing the important zfs initramfs package so when ever you installed new kernel the modules were not created.
If you can load older kernel that doesnt have the modules you should also try creating them by updating the initramfs.
nd if the 4.15 kernel is creating issues for you, you can always uninstall it.

---

### Post by ehamdja on 2018-12-10
my issue now is that since it is a bare minimum ubuntu server, I don't think I have grub menu or options where I can choose which kernel to upload. I tried to access the hard drive and I only see [COLOR=#333333][FONT=&quot]boot.ini, ulnitrd and zlmage.[/FONT][/COLOR] Any more pointer?

---

### Post by ehamdja on 2018-12-14
[COLOR=#333333][FONT=&quot]Solved it by extracting the kernel/initrd/modules from a working 18.04 image and copy it over my system[/FONT][/COLOR]

---

