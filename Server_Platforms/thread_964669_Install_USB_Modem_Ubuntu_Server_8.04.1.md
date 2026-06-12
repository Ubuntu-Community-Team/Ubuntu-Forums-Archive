---
title: "Install USB Modem Ubuntu Server 8.04.1"
date: 2008-10-31
forum: Server Platforms
---

### Post by andyrogers2008 on 2008-10-31
Hi All

I need a bit of help please, I have surrently got a HP UM9800 USB Modem which I would like to add to my fax server, based on Ubuntu 8.04.1 .  I so far have gathered than I need to run the ScanModem tool which I have done, but then after this I am completly confused about the exact steps I need to take to get this modem to actually work on my server.

Iam also currently using Kernel 2.6.24-21 if that helps.

Here is the output of my ModemData.txt file, any help would really be apprecaiated:-

 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.24-21-server 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.24-21-server (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Aug 25 18:06:43 UTC 2008
 scanModem update of:  2008_10_24

 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 0483:7554 SGS Thomson Microelectronics 56k SoftModem

For candidate card in slot 01:0b.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 01:0b.0	11c1:0458	141d:9300	Communication controller: Agere Systems LT WinModem 

 Modem interrupt assignment and sharing: 
 15:        102   IO-APIC-edge      libata
 --- Bootup diagnostics for card in PCI slot 01:0b.0 ----

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 001:
	Modem chipset  detected on
SLOT="Bus 001 Device 002:"
NAME="SGS Thomson Microelectronics 56k SoftModem"
bus=001
USBmodemID=0483:7554
IDENT=slusb
Driver=slusb

 For candidate modem in:  001
    SGS Thomson Microelectronics 56k SoftModem
      Primary device ID:  0483:7554
 Support type needed or chipset:	slusb
 

----------------end Softmodem section --------------
The modem is supported by the Smartlink slusb
plus the slmodemd helper utility.  Read the
DOCs/Smartlink.txt and Modem/DOCs/YourSystem.txt for follow through guidance.


For 2.6.24-21-server compiling drivers is necessary. As of October 2007 the current packages at
[http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)  are the
ungrab-winmodem-20070505.tar.gz and slmodem-2.9.11-20080126.tar.gz

Writing DOCs/Smartlink.txt
============ end Smartlink section =====================

 Vendor 11c1 is Lucent Technologies with modem technology now under LSI Inc. 
Their Linux  code developer/maintainer is Soumyendu Sarkar. Support for a chipset and its 
 continued maintenance is only initiated at the request of a major chipset buyer,
 or comparable sponsor. Several different  modem chipset types  are produced: 
 with varying support under Linux.
 Device ID   Support        Name           Comment
 ---------   -------------  -----------    -----------------------------
 0480        serial_drivers Venus           controller chipset 1673JV7
 0440-045d   martian        Mars/Apollo     DSP (digital signal processing) chipsets
 0462        none           56K.V90/ADSL Wildwire 
 048d none           	    SV2P            soft modem 
 048(c or f) AGRSM          SV2P            soft modem
 0600        none           soft modem, very few in the field.
 0620        AGRSM          Pinball  soft modem, in some HP desktop PCs
 011c11040   AGRSM          hosted on High Definition Audio cards
 062(1-3)    none           SV92PP,Pinball  soft modem, in some HP desktop PCs

martian - At [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/)
AGRSM - At [http://linmodems.technion.ac.il/packages/ltmodem/11c11040/](http://linmodems.technion.ac.il/packages/ltmodem/11c11040/)
  Compiling resources for a driver module pair: agrmodem.ko + agrserial.ko
  Use the  agrsm-HDA-20080721-ALSA15.tar.bz2 or agrsm-HDA-20080721.tar.bz2
  Read the agrsm_howto.txt.  For 11c11040 chips, also the HOWTO-Agere-11c11040-HDA.html

-------------- end Agere Systems section -------------------


Predictive  diagnostics for card in bus 01:0b.0:
	Modem chipset  detected on
NAME="Communication controller: Agere Systems LT WinModem "
CLASS=0780
PCIDEV=11c1:0458
SUBSYS=141d:9300
IRQ=5
IDENT=Agere.DSP

 For candidate modem in:  01:0b.0
   0780 Communication controller: Agere Systems LT WinModem 
      Primary device ID:  11c1:0458
 Support type needed or chipset:	Agere.DSP
 

----------------end Softmodem section --------------

 The modem has a Lucent/Agere/LSI Mars or Apollo DSP (digital signal processing) chipset. 
Support packages for 2.6.n kernels are at:
 [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/) 
Always use the most update for kernels after 2.6.20, currently martian-full-20080625.tar.gz
For kernels 2.6.20 and less, usr martian-full-20080407.tar.gz.

 See DOCs/AgereDSP.txt for Details.


 Vendor 11c1 is Lucent Technologies with modem technology now under LSI Inc. 
Their Linux  code developer/maintainer is Soumyendu Sarkar. Support for a chipset and its 
 continued maintenance is only initiated at the request of a major chipset buyer,
 or comparable sponsor. Several different  modem chipset types  are produced: 
 with varying support under Linux.
 Device ID   Support        Name           Comment
 ---------   -------------  -----------    -----------------------------
 0480        serial_drivers Venus           controller chipset 1673JV7
 0440-045d   martian        Mars/Apollo     DSP (digital signal processing) chipsets
 0462        none           56K.V90/ADSL Wildwire 
 048d none           	    SV2P            soft modem 
 048(c or f) AGRSM          SV2P            soft modem
 0600        none           soft modem, very few in the field.
 0620        AGRSM          Pinball  soft modem, in some HP desktop PCs
 011c11040   AGRSM          hosted on High Definition Audio cards
 062(1-3)    none           SV92PP,Pinball  soft modem, in some HP desktop PCs

martian - At [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/)
AGRSM - At [http://linmodems.technion.ac.il/packages/ltmodem/11c11040/](http://linmodems.technion.ac.il/packages/ltmodem/11c11040/)
  Compiling resources for a driver module pair: agrmodem.ko + agrserial.ko
  Use the  agrsm-HDA-20080721-ALSA15.tar.bz2 or agrsm-HDA-20080721.tar.bz2
  Read the agrsm_howto.txt.  For 11c11040 chips, also the HOWTO-Agere-11c11040-HDA.html

 0x0458 -- Mars 3 Mercury data/fax/tam only.
-------------- end Agere Systems section -------------------

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.2.3
             and the compiler used in kernel assembly: 4.2.4


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.2
   linuc_headers base folder /lib/modules/2.6.24-21-server/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are needed. The also required headers of package libc6 are commonly installed by default. 
 Compiling hsfmodem drivers does require linux-libc-dev and libc6-dev packages, for kernels 2.6.24 and later versions.
 In not included on your install CD, search for them at [http://packages.ubuntu.com](http://packages.ubuntu.com)
 or comparable Repository for other Linux distros.
 When compiling ALSA drivers, the utility "patch" will also be needed.




If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed packages.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
	-rwsr-xr-- 1 root dip 269256 2007-10-04 20:57 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

# start/stop the daemon when the USB modem is connected
KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:
/etc/udev/sl-modem-daemon.rules:# start/stop the daemon when the USB modem is connected
/etc/udev/sl-modem-daemon.rules:KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/sl-modem-daemon.modutils:install slamr modprobe --ignore-install ungrab-winmodem ;  modprobe --ignore-install slamr; test -e /dev/slamr0 || (/bin/mknod -m 660 /dev/slamr0 c 242 0 2>/dev/null && chgrp dialout /dev/slamr0) 
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------


Thanks in advance.

Andy

---

