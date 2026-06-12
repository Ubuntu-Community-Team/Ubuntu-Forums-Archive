---
title: "[SOLVED] Compile and blacklist drivers"
date: 2007-12-02
forum: Server Platforms
---

### Post by MachineBucket on 2007-12-02
I'm running Server 6.06 and I just replaced the ancient 10/100 NIC that came with the machine with a gigabit NIC using the RTL8169s chipset. Ubuntu recognized the card and loaded modules for it fine, but the card isn't performing as I expected it to.

A 4GB file transfer to the server took about 15~16 minutes, whereas the same file sent to my gigabit NAS only took 4 minutes. I'm pretty sure the  driver is to blame. 

ethtool shows the card running at full-duplex 1000mbps but the performance says otherwise. I was wondering if someone could tell me which packages I need to compile my own drivers, and how to find which driver is loading on startup and how to blacklist it.

Thanks! :)

---

### Post by MachineBucket on 2007-12-02
I downloaded the drivers from Realtek's website and I tried to install the drivers but I was unsuccessful. 

The instructions that came with the drivers:
```
<Linux device driver for Realtek Ethernet controllers>

	This is the Linux device driver released for RealTek RTL8169S/8110S, RTL8169SB/8110SB, and RTL8110SC.

<Requirements>

	- kernel source tree (supported Linux kernel 2.6.x/2.4.20 and latter)
	- compiler/binutils for kernel compilation

<Quick install with proper kernel settings>
	Check whether the built-in driver, r8169.ko(or r8169.o for linux kernel 2.4.x), is installed. 
		# lsmod | grep r8169

	If it is installed, please remove it.
		# rmmod r8169
	note: If the built-in driver cannot removed by rmmod, please edit /etc/modprobe.conf and comment 'alias eth0 r8169'. Then, remove it again or reboot your computer.

	Unpack the tarball :
		# tar vjxf r8169-6.aaa.bb.tar.bz2

	Change to the directory:
		# cd r8169-6.aaa.bb

	If you are running the target kernel, then you should be able to do :

		# make clean modules	(as root or with sudo)
		# make install
		# depmod -a
		# insmod ./src/r8169.ko	(or r8169.o for linux kernel 2.4.x)

	You can check whether the driver is loaded by using following commands.

		# lsmod | grep r8169
		# ifconfig -a

	If there is a device name, ethX, shown on the monitor, the linux 
	driver is loaded. Then, you can use the following command to activate 
	the ethX.

		# ifconfig ethX up

		,where X=0,1,2,...
```

The error from 'sudo make clean modules':

```
make -C src/ clean
make[1]: Entering directory `/home/machinebucket/r8169-6.004.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset
make[1]: Leaving directory `/home/machinebucket/r8169-6.004.00/src'
make -C src/ modules
make[1]: Entering directory `/home/machinebucket/r8169-6.004.00/src'
make -C /lib/modules/2.6.15-29-server/build SUBDIRS=/home/machinebucket/r8169-6.004.00/src modules
make: Entering an unknown directory
make: *** /lib/modules/2.6.15-29-server/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/machinebucket/r8169-6.004.00/src'
make: *** [modules] Error 2

```

Do I need to create a /build/ directory in /lib/modules to make the compile work correctly?

EDIT: I realized that there is no need to blacklist the driver since this driver is just an updated version of what's already installed. Unless I try to install another driver with a different name.

---

### Post by MachineBucket on 2007-12-05
I didn't have all the necessary packages installed. 

This is what got it working for me.

> Just had this problem. The build folder is sometimes not linked properly to the headers for the kernel you are running.

To fix this, do the following.

sudo apt-get install build-essential

This will make sure you have most of the build tools, though ubuntu provides these already (usually). This is mostly useful for debian users who installed with the basic packages and not the programming ones. Naturally debian users will not need the sudo as debian encourages the use of the root account as opposed to sudo.

sudo apt-get install linux-headers-`uname - r`

This will installed the latest headers for your kernel. Note the backquotes around uname: this is the quote on the same key as the tilde ~.

sudo ln -s /usr/src/linux-headers-`uname - r` /lib/modules/`uname -r`/build

This will link the headers to the build folder in the proper place. This should get you compiling!

By the by, the `uname -r` just pops in the current kernel version number into the path, to make these instructions as generic as possible. Enjoy!

The next steps are to blacklist the old driver (the r8169) and make sure the r8168 is loaded on startup, the instructions for which you can find here on the forums. For debian users, the blacklisting didn't seem to work for me, but the instructions near the start of this thread do.

Thanks to jedcred for that one.

---

### Post by srf21c on 2008-06-11
Having a similar problem compiling the rtl8110SC driver on Hardy 8.04, but unfortunately the fix mentioned above did not work for me.

```
seth@atjeu-noc2:~/r8169-6.006.00$ sudo make clean modules
make -C src/ clean
make[1]: Entering directory `/home/seth/r8169-6.006.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset
make[1]: Leaving directory `/home/seth/r8169-6.006.00/src'
make -C src/ modules
make[1]: Entering directory `/home/seth/r8169-6.006.00/src'
make -C /lib/modules/2.6.24-18-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/seth/r8169-6.006.00/src'
make: *** [modules] Error 2

```

---

