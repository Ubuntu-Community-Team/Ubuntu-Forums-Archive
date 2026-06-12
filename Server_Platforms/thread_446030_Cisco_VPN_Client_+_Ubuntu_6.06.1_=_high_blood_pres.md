---
title: "Cisco VPN Client + Ubuntu 6.06.1 = high blood pressure"
date: 2007-05-16
forum: Server Platforms
---

### Post by nick1 on 2007-05-16
Greetings,

I am trying to install the Cisco VPN client on Ubuntu 6.06.1.  The installation is failing and returning the following information:

```
sudo ./vpn_install

Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright info...

Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel modeule, you must have the
kernel headers for the version of the kernel you are running.

Directory containing linux kernel source code [/lib/modules/2.6.15-28-686/build]
(I changed this to): /usr/src/linux-headers-2.6.15-28-686/

*Binaries will be installed in "/usr/local/bin".
*Modules will be installed in "/lib/modules/2.6.15-28-686/CiscoVPN".
*The VPN service will be started AUTOMATICALLY at boot time.
*Kernel source from "/usr/src/linux-headers-2.6.15-28-686/" will be used to build the module.

Is the above correct [y]

Making module
./driver_build.sh: line 50: make: command not found
Failed to make module "cisco_ipsec.ko".
```

My system information:

-Dell Latitude D820
-Ubuntu 6.06.1 LTS desktop Dapper Drake
-Kernel 2.6.15-28-686
-Cisco VPN Client version 4.8.00.0490-k9

I am aware that alternatives exist to the Cisco VPN client but before I think about using a different product, I would like to know why this installation is failing and how to properly resolve the problem.

I've read several posts that suggest installing various compilers and the like, but is this the core solution?  In an attempt to troubleshoot this problem, I installed the "make" command however the installation failed again, this time complaining about gcc not being available.

I've also read about a patch for the Cisco VPN client that is designed to work on kernels > 2.6.19 but am not sure if such a patch exists for my kernel.

Any thoughts and suggestions on resolving this problem would be greatly appreciated.

Thank you for your time,

---

### Post by m!key on 2007-05-16
Hello,

I recall something about having to install "build-essentials" so something like 

> sudo apt-get install build-essentials IMHO should get you started.

---

### Post by nick1 on 2007-05-16
Thank you for your help.  I installed the build-essential package then ran through the Cisco VPN client install again.  Now it looks like I'm getting somewhere.

However, the installation process showed some warnings which I am hoping someone can explain.

Here are the installation results:

---start---

sudo ./vpn_install

Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the license.txt file (The VPN Client license) and will comply with its terms.

Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the kernel headers for the version of the kernel you are running.

Directory containing linux kernel source code [/lib/modules/2.6.15-28-686/build]/usr/src/linux-headers-2.6.15-28-686/

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.15-28-686/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/usr/src/linux-headers-2.6.15-28-686/" will be used to build the module.

Is the above correct [y]

Making module
make -C /usr/src/linux-headers-2.6.15-28-686/ SUBDIRS=/home/kakster/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-28-686'
  CC [M]  /home/kakster/Desktop/vpnclient/linuxcniapi.o
  CC [M]  /home/kakster/Desktop/vpnclient/frag.o
  CC [M]  /home/kakster/Desktop/vpnclient/IPSecDrvOS_linux.o
  CC [M]  /home/kakster/Desktop/vpnclient/interceptor.o
/home/kakster/Desktop/vpnclient/interceptor.c: In function ‘handle_vpnup’:
/home/kakster/Desktop/vpnclient/interceptor.c:310: warning: assignment from incompatible pointer type
/home/kakster/Desktop/vpnclient/interceptor.c:334: warning: assignment from incompatible pointer type
/home/kakster/Desktop/vpnclient/interceptor.c:335: warning: assignment from incompatible pointer type
/home/kakster/Desktop/vpnclient/interceptor.c: In function ‘do_cleanup’:
/home/kakster/Desktop/vpnclient/interceptor.c:378: warning: assignment from incompatible pointer type
  CC [M]  /home/kakster/Desktop/vpnclient/linuxkernelapi.o
  LD [M]  /home/kakster/Desktop/vpnclient/cisco_ipsec.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /home/kakster/Desktop/vpnclient/.libdriver.so.cmd for /home/kakster/Desktop/vpnclient/libdriver.so
  CC      /home/kakster/Desktop/vpnclient/cisco_ipsec.mod.o
  LD [M]  /home/kakster/Desktop/vpnclient/cisco_ipsec.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-28-686'
Create module directory "/lib/modules/2.6.15-28-686/CiscoVPN".
Copying module to directory "/lib/modules/2.6.15-28-686/CiscoVPN".
Already have group 'bin'

Creating start/stop script "/etc/init.d/vpnclient_init".
    /etc/init.d/vpnclient_init
Enabling start/stop script for run level 3,4 and 5.
Creating global config /etc/opt/cisco-vpnclient

Installing license.txt (VPN Client license) in "/opt/cisco-vpnclient/":

Installing bundled user profiles in "/etc/opt/cisco-vpnclient/Profiles/":
* New Profiles     : sample

Copying binaries to directory "/opt/cisco-vpnclient/bin".
Adding symlinks to "/usr/local/bin".
    /opt/cisco-vpnclient/bin/vpnclient
    /opt/cisco-vpnclient/bin/cisco_cert_mgr
    /opt/cisco-vpnclient/bin/ipseclog
Copying setuid binaries to directory "/opt/cisco-vpnclient/bin".
    /opt/cisco-vpnclient/bin/cvpnd
Copying libraries to directory "/opt/cisco-vpnclient/lib".
    /opt/cisco-vpnclient/lib/libvpnapi.so
Copying header files to directory "/opt/cisco-vpnclient/include".
    /opt/cisco-vpnclient/include/vpnapi.h

Setting permissions.
    /opt/cisco-vpnclient/bin/cvpnd (setuid root)
    /opt/cisco-vpnclient (group bin readable)
    /etc/opt/cisco-vpnclient (group bin readable)
    /etc/opt/cisco-vpnclient/Profiles (group bin readable)
    /etc/opt/cisco-vpnclient/Certificates (group bin readable)
* You may wish to change these permissions to restrict access to root.
* You must run "/etc/init.d/vpnclient_init start" before using the client.
* This script will be run AUTOMATICALLY every time you reboot your computer.

---end---

Should I be concerned with anything that occurred during the installation process?

Thank you for your time,

---

### Post by strixy on 2007-05-16
Warning: could not find /home/kakster/Desktop/vpnclient/.libdriver.so.cmd for /home/kakster/Desktop/vpnclient/libdriver.so

That's not good.

There is a warning about checking file permissions... specifically, are you part of the group that can run the VPN client?

I didn't even know it was available for Linux... and I use it everyday for work. Well, spank my bottom and call me Sally!  (ignore that last part ... that would be icky). I'm going to have to see it I can get that work too!

---

### Post by nick1 on 2007-05-17
>  Warning: could not find /home/kakster/Desktop/vpnclient/.libdriver.so.cmd for /home/kakster/Desktop/vpnclient/libdriver.so

That's not good.

There is a warning about checking file permissions... specifically, are you part of the group that can run the VPN client?

Thanks for the heads-up.  This is a fresh install of Ubuntu 6.06.1 and I am the only user of this computer.
How would you recommend resolving these issues, and do they present a problem when using the VPN client?  I was able to successfully connect to my company's VPN server but I want to make sure the client installed correctly and is operating securely.

If you are thinking about installing the Cisco VPN client for Linux, make sure you have the proper kernel headers installed and you'll probably need the package called build-essential.  Those were the two key components in my case.

Thank you for your time,

---

