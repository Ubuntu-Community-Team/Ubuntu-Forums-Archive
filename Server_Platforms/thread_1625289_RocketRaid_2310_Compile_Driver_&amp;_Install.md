---
title: "RocketRaid 2310 Compile Driver &amp; Install"
date: 2010-11-18
forum: Server Platforms
---

### Post by SBFree on 2010-11-18
I would like to use a HighPoint RocketRaid 2310 Controller with Ubuntu 10.04 LTS to control 2 Raid 1 Arrays. There is not a precompiled driver available for 10.04. Is there a description of how to compile the driver from source code and install it or can someone describe this process?
Thanks,
Scott

---

### Post by CharlesA on 2010-11-18
Download the open source driver from here: [http://www.highpoint-tech.com/USA_new/series_rr2300.htm](http://www.highpoint-tech.com/USA_new/series_rr2300.htm)

Make sure you have linux-headers installed for yer kernel and then compile the driver with ***make install***

Here's my lazy script:

```
#!/bin/bash

URL=http://www.support-highpoint-tech.com/Main/rr231x_00/Linux/opensrc/
DRIVER=rr231x_0x-linux-src-v2.5-091022-1618.tar.gz

apt-get install build-essential linux-headers-$(uname -r)
wget $URL$DRIVER && tar -xf $DRIVER && cd rr231x_0x-linux-src-v2.5/product/rr2310pm/linux && make install

```

Run it with sudo.

---

### Post by SBFree on 2010-11-19
That's it? You must be an Ubuntu God. Thank you so much. I'm off to restore back to a clean install and try it out.
Regards, Scott

---

### Post by CharlesA on 2010-11-19
I have a similar card (26xx) and I have to compile the driver from source. :)

Don't forget to mark the thread as solved from the thread tools menu.

---

### Post by SBFree on 2010-11-19
I feel Like I got close. I changed the URL and then got the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.32-25-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-24-generic linux-headers-2.6.32-24
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
--2010-11-19 19:09:29--  [http://www.support-highpoint-tech.com/Main/rr231x_00/Linux/opensrc/rr231x_0x-linux-src-v2.5-091022-1618.tar.gz](http://www.support-highpoint-tech.com/Main/rr231x_00/Linux/opensrc/rr231x_0x-linux-src-v2.5-091022-1618.tar.gz)
Resolving [www.support-highpoint-tech.com](www.support-highpoint-tech.com)... 97.74.215.122
Connecting to [www.support-highpoint-tech.com|97.74.215.122|:80](www.support-highpoint-tech.com|97.74.215.122|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 493669 (482K) [application/x-gzip]
Saving to: `rr231x_0x-linux-src-v2.5-091022-1618.tar.gz'

100%[=============================================================>] 493,669      490K/s   in 1.0s    

2010-11-19 19:09:30 (490 KB/s) - `rr231x_0x-linux-src-v2.5-091022-1618.tar.gz' saved [493669/493669]

tar: option requires an argument -- f
Try `tar --help' or `tar --usage' for more information.

Thanks for being patient. If it gives you any insight I had to go write my "Hello World" bash script to get to this point.

Scott

---

### Post by CharlesA on 2010-11-19
Try running this in the current directory:

```
tar -xf rr231x_0x-linux-src-v2.5-091022-1618.tar.gz
```

---

### Post by SBFree on 2010-11-19
That ran. Can I substitute it for part of the part of the line that starts 'wget'?

---

### Post by CharlesA on 2010-11-19
It's already extracted the tar, so you'd only have to do this:

```
cd rr231x_0x-linux-src-v2.5/product/rr2310pm/linux
sudo make install
```

---

### Post by SBFree on 2010-11-19
That ran too!

It looks like 'cd rr231x_0x-linux-src-v2.5/product/rr2310pm/linux'
was already in the wget line.

Why did it not work there and is there a way to correct the script for my directories?

Are the drivers installed now? Will they load at each start up if they are? Thanks again for all this help.
Scot

---

### Post by CharlesA on 2010-11-19
It should have worked, I tested it before I posted it.

*shrugs*

The drivers will load every time you boot. If you upgrade the kernel, you'll need to reinstall the drivers.

---

### Post by SBFree on 2011-08-20
How are drivers reinstalled after a kernel update? I have been experiencing some difficulty getting directories to update and would like to see if reinstalling the drivers solves this problem.
Thanks,
Scott

---

### Post by CharlesA on 2011-08-20
You have to rebuild them after a kernel update.

I've been just installing from source then using modprobe to load the module.

---

### Post by SBFree on 2011-08-24
Thank you for the reply.
I ran the following script that I had to install the driver and things seemed to be right again. I can see this is going to be a recurring task when the Kernel is updated. [COLOR="Red"]I was hoping you might point me to how to use 'modprobe' in this setting[/COLOR].

It looks like I should use the modprobe as follows:
```

$ sudo modprobe installraid

```

I had added comments to the script you gave me trying to understand what it was doing. The script I used was:
```
!/bin/bash
### Run this script as root
### ./installraid.sh
###
### Set variable URL
URL=http://www.support-highpoint-tech.com/Main/rr231x_00/Linux/opensrc/

### Set Driver variable
DRIVER=rr231x_0x-linux-src-v2.5-091022-1618.tar.gz

### Install build-essentials & linux-headers
### By default, Ubuntu does not come with the tools required. You need to install the package 
### build-essential for making
### the package and checkinstall for putting it into your package
### manager. These can be found on the install CD or in the
### repositories, searching in
### Synaptic Package Manager
### run as sudo if not in script
apt-get install build-essential linux-headers-$(uname -r)

### get the driver off the web
### puts the driver.tar.gz in the <username> folder
wget $URL$DRIVER &&

### Extract the Driver from the archive
### extracts the driver to folder rr231x_0x-linux-src-v2.5/product/rr2310pm/linux
### in <username> folder
tar -xf $DRIVER &&

### change to a specific folder
cd rr231x_0x-linux-src-v2.5/product/rr2310pm/linux &&

### run make
### make executes commands in the makefile to update one or more target names,
### where name is typically a program. If no -f option is present,
### make will look for the makefiles GNUmakefile, makefile, and Makefile, in that order
### run this as sudo if not in script
make install

```

[COLOR="red"]I wonder if the end should be 'make installraid' rather than 'make install' as the name of my file is installraid.sh ?[/COLOR]

Thanks for your efforts,
Scott

---

### Post by CharlesA on 2011-08-25
I think it should be "make install"

To use modprobe you need to know the module name - mine is rr26xx for my raid card (different model)

---

### Post by SBFree on 2012-10-23
Well I was keeping up with Kernel updates ok but it's not working after having upgraded to 12.04. I get an error that the driver is for kernel 2.4/2.6 and that I have 2.2.:
**** Only kernel 2.4/2.6 is supported but you use 2.2. *

Running the script also tells me that:
*!/bin/bash: not found*

It looks like the only driver available is no longer going to work. Is any one using a RocketRaid 2310 with 12.04?
Thanks in advance for any comments,
Scott

---

### Post by CharlesA on 2012-10-23
I'm not using 2310 on 12.04, but I am using 2640 on 12.04.

You might be able to mess with the source and get it to work with the 3.2.x kernel.

See here: [https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid)

---

### Post by SBFree on 2012-10-23
I feel like I got close with new source code from HPT but ended with an error that I am having difficulty attributing to my script or the code. My script is attached

The end of the out put is:
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/scott/rr231x_0x-linux-src-v2.5/product/rr2310pm/linux/.build/.him_rr2310pm.o.cmd for /home/scott/rr231x_0x-linux-src-v2.5/product/rr2310pm/linux/.build/him_rr2310pm.o
  CC      /home/scott/rr231x_0x-linux-src-v2.5/product/rr2310pm/linux/.build/rr2310_00.mod.o
  LD [M]  /home/scott/rr231x_0x-linux-src-v2.5/product/rr2310pm/linux/.build/rr2310_00.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'
Can not get kernel version from rr2310_00..
make: *** [install] Error 1

Thanks in advance.
Scott

---

### Post by CharlesA on 2012-10-23
That is a problem with running make, try running it manually and see if it will compile.

---

