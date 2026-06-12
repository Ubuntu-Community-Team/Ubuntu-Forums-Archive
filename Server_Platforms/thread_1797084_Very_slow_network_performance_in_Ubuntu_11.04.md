---
title: "Very slow network performance in Ubuntu 11.04"
date: 2011-07-04
forum: Server Platforms
---

### Post by lafaki on 2011-07-04
Hi,

I have recently installed Ubuntu 11.04 32-bit on my NAS server.

Before 11.04 I was using 10.10 and I could achieve network transfer speeds up to 11 MB/sec on a 100 Mbps NIC.

Now in 11.04 I hardly get 1-2 MB/sec. I have checked with ethtool and the NIC seems to be properly setup for the max speed and full duplex. 

Any ideas on how to get back the 10 MB/sec network connection?
With the downgraded speed my NAS server is unfortunately useless :(

_Some background_ 
Between 10.10 and 11.04 nothing has been modified, same network switch and configuration is used.

The access speed is benchmarked against a Samba 4 network drive to which a logical NTFS volume is mounted as per below:

/dev/md0p1 /home/nas ntfs-3g auto,users,uid=1000,gid=100,utf8

The md0p1 partition is based on two software RAID1 disks of Linux Raid Autodetect type.

As I write I am also doing a system upgrade. 

Thanks!
Akis

---

### Post by u96 on 2011-09-22
I have a similar experience with Ubuntu 11.04 and I found a solution:

My Ubuntu box had a terrible network performance. Pinging another Linux host on the LAN, using its IP address, gave very infrequent replies.
Normally the received ping replies from a nearby idle host are displayed at very regular intervals. But this was not the case here. Of course, browsing the Internet was also nearly impossible.

The PC is configured as dual-boot, so I rebooted into Windows-7. Here there were no problems with the networking, so I concluded that the Ethernet interface was functioning well.

I then tried booting a live Ubuntu from the Ubuntu 11.04 CDROM. Same problem.

Finally, I went to our LAN wiring switchboard and moved my LAN connection from a 100 Mbps into a 1 Gbps switch. And now the problem has disappeared!

I can consistently switch back to the 100 Mbps switch port and the problem comes back again.

Could this be a problem related to the LAN driver?

The Ubuntu 11.04 system is updated as of today.

When connected to 100 Mbps, dmesg displays:

e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO

lsmod gives me: e1000e

And when connected to 1 Gbps, dmesg says:

e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None

The PC has this Ethernet controller:
Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 05)

I hope that this information will be helpful to someone.

Best regards.

---

### Post by chachu on 2011-09-24
Hey there, Ive been suffering with the same issue, I can hardly get anything done on my NAS now. 

Unfortunatly for me i dont have a gigabit router.

Anyone figured out how to sort this issue out????

---

### Post by ian dobson on 2011-09-24
Hi,

First try and find out if the performance problem with the network or samba. 

1) Ping the server and see what your times are like.
2) Install iperf and test the network throughput (At tcp level)
3) Look at optimizing your samba configuration. On my backend I added the following line to my smb.conf file:-

socket options = TCP_NODELAY SO_RCVBUF=262144 SO_SNDBUF=262144 rlimit_max=16384 IPTOS_LOWDELAY SO_KEEPALIVE

and am getting 30-40Mbyte sec over a gigabit lan.

Regards
Ian Dobson

---

### Post by LarryIB on 2011-09-26
Hi, my experience with Ubuntu 11.04 and e1000e driver is quite similar to ub96. Pings responses are very irregular and connections to remote hosts (in the same LAN) with ssh are almost impossible. On the contrary, browsing the Internet is acceptable but I note that DNS lookups are very slow.

With Ubuntu 10.04 LTS and the same computer/driver everything was fine, so a I think is a driver problem. Actually, when I do,

```
$ sudo rmmod e1000e
$ sudo modprobe e1000e
```

everything comes back to normal (in 11.04). After a normal reboot, the odd behavior comes back...

---

### Post by ian dobson on 2011-09-27
Hi,

Strange I have a e1000 in my backend server and haven't seen any problems. OK my network is running at gbit speed.

[    2.361145] e1000e: Intel(R) PRO/1000 Network Driver - 1.2.20-k2
[    2.361147] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    2.361161] e1000e 0000:00:19.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.361166] e1000e 0000:00:19.0: setting latency timer to 64
[    2.361254] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
[    3.735775] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) bc:ae:c5:75:35:7c
[    3.735777] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    3.735821] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[    9.250088] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
[    9.309945] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
[   12.871911] e1000e: eth8 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx


Regards
Ian Dobson

---

### Post by manus_eiffel on 2011-10-14
> **LarryIB said:**
> Hi, my experience with Ubuntu 11.04 and e1000e driver is quite similar to ub96. Pings responses are very irregular and connections to remote hosts (in the same LAN) with ssh are almost impossible. On the contrary, browsing the Internet is acceptable but I note that DNS lookups are very slow.

With Ubuntu 10.04 LTS and the same computer/driver everything was fine, so a I think is a driver problem. Actually, when I do,

```
$ sudo rmmod e1000e
$ sudo modprobe e1000e
```

everything comes back to normal (in 11.04). After a normal reboot, the odd behavior comes back...

Thank you so much for this. I can confirm it has fixed my issue on both Ubuntu 11.04 and Ubuntu 11.10. Is there a bug report for that one?

---

### Post by LarryIB on 2011-10-27
First of all, sorry about my english. Is not my native language...

I note something quite strange about this issue. The first thing I did when the network performance was so bad is to install the latest version of the e1000e driver from here: [http://sourceforge.net/projects/e1000/](http://sourceforge.net/projects/e1000/)

After the installation I reboot the system and the odd behavior comes back... This is the output of dmesg: 

```
$ dmesg | grep e1000e
[    1.427434] **e1000e: Intel(R) PRO/1000 Network Driver - 1.2.20-k2**
[    1.427436] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    1.540013] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.540020] e1000e 0000:00:19.0: setting latency timer to 64
[    1.540143] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    1.860249] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) e0:69:95:de:08:0b
[    1.860251] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.860285] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[   17.297458] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   17.357188] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   18.960136] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   18.960141] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   28.959549] e1000e 0000:00:19.0: PCI INT A disabled
```Take a look to the driver version... After I do

```

$sudo rmmod e1000e
$sudo modprobe e1000e

```I get this dmesg output:

```
[    1.427434]** e1000e: Intel(R) PRO/1000 Network Driver - 1.2.20-k2**
[    1.427436] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    1.540013] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.540020] e1000e 0000:00:19.0: setting latency timer to 64
[    1.540143] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    1.860249] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) e0:69:95:de:08:0b
[    1.860251] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.860285] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[   17.297458] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   17.357188] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   18.960136] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   18.960141] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   28.959549] e1000e 0000:00:19.0: PCI INT A disabled
[   28.984301] **e1000e: Intel(R) PRO/1000 Network Driver - 1.6.2-NAPI**
[   28.984302] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[   28.984327] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   28.984336] e1000e 0000:00:19.0: setting latency timer to 64
[   29.070156] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   29.304405] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) e0:69:95:de:08:0b
[   29.304407] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[   29.304455] e1000e 0000:00:19.0: eth0: MAC: 11, PHY: 11, PBA No: FFFFFF-0FF
[   29.447962] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   29.507685] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   31.059457] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   31.059459] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
```The driver version (**1.6.2-NAPI**) is not the same that is loaded at boot time and now the network works very good! I don't know why Ubuntu is loading the ** 1.2.20-k2 **version at boot time and where is getting the **e1000e.ko** module for that version, because I have only one in the system and correspond to the **1.6.2-NAPI **version.

```
$ locate e1000e.ko
/lib/modules/2.6.32-34-generic/kernel/drivers/net/e1000e/e1000e.ko
$ modinfo /lib/modules/2.6.32-34-generic/kernel/drivers/net/e1000e/e1000e.ko
filename:       /lib/modules/2.6.32-34-generic/kernel/drivers/net/e1000e/e1000e.ko
version:       **1.6.2-NAPI**
license:        GPL
description:    Intel(R) PRO/1000 Network Driver
author:         Intel Corporation, <linux.nics@intel.com>
srcversion:     E4B90BE4DC230817DCFB165
alias:          pci:v00008086d00001503sv*sd*bc*sc*i*
alias:          pci:v00008086d00001502sv*sd*bc*sc*i*
alias:          pci:v00008086d000010F0sv*sd*bc*sc*i*
alias:          pci:v00008086d000010EFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010EBsv*sd*bc*sc*i*
alias:          pci:v00008086d000010EAsv*sd*bc*sc*i*
alias:          pci:v00008086d00001525sv*sd*bc*sc*i*
alias:          pci:v00008086d000010DFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010DEsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CEsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CDsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CCsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CBsv*sd*bc*sc*i*
alias:          pci:v00008086d000010F5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010E5sv*sd*bc*sc*i*
alias:          pci:v00008086d0000294Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010BDsv*sd*bc*sc*i*
alias:          pci:v00008086d000010C3sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C2sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C0sv*sd*bc*sc*i*
alias:          pci:v00008086d00001501sv*sd*bc*sc*i*
alias:          pci:v00008086d00001049sv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Asv*sd*bc*sc*i*
alias:          pci:v00008086d000010C4sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C5sv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010BBsv*sd*bc*sc*i*
alias:          pci:v00008086d00001098sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BAsv*sd*bc*sc*i*
alias:          pci:v00008086d00001096sv*sd*bc*sc*i*
alias:          pci:v00008086d0000150Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010F6sv*sd*bc*sc*i*
alias:          pci:v00008086d000010D3sv*sd*bc*sc*i*
alias:          pci:v00008086d0000109Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000108Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000108Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Dsv*sd*bc*sc*i*
alias:          pci:v00008086d000010B9sv*sd*bc*sc*i*
alias:          pci:v00008086d000010D5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010DAsv*sd*bc*sc*i*
alias:          pci:v00008086d000010D9sv*sd*bc*sc*i*
alias:          pci:v00008086d00001060sv*sd*bc*sc*i*
alias:          pci:v00008086d000010A5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BCsv*sd*bc*sc*i*
alias:          pci:v00008086d000010A4sv*sd*bc*sc*i*
alias:          pci:v00008086d0000105Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000105Esv*sd*bc*sc*i*
depends:        
vermagic:       2.6.32-34-generic SMP mod_unload modversions 
parm:           copybreak:Maximum size of packet that is copied to a new buffer on receive (uint)
parm:           TxIntDelay:Transmit Interrupt Delay (array of int)
parm:           TxAbsIntDelay:Transmit Absolute Interrupt Delay (array of int)
parm:           RxIntDelay:Receive Interrupt Delay (array of int)
parm:           RxAbsIntDelay:Receive Absolute Interrupt Delay (array of int)
parm:           InterruptThrottleRate:Interrupt Throttling Rate (array of int)
parm:           IntMode:Interrupt Mode (array of int)
parm:           SmartPowerDownEnable:Enable PHY smart power down (array of int)
parm:           KumeranLockLoss:Enable Kumeran lock loss workaround (array of int)
parm:           CrcStripping:Enable CRC Stripping, disable if your BMC needs the CRC (array of int)
parm:           EEE:Enable/disable on parts that support the feature (array of int)
parm:           Node:[ROUTING] Node to allocate memory on, default -1 (array of int)
```The workaround is to add a startup script to rmmod and modprobe the e1000e driver. Quite messy...

One more strange thing: I have the same computer (motherboard, processor, network card, everything...) and with a fresh 11.04 installation and with the **1.2.20-k2 **driver version everything works fine out of the box. So, maybe is a hardware related issue that doesn't manifest with the **1.6.2-NAPI**...

---

### Post by ian dobson on 2011-10-28
Hi,

Could it be that when you boot the network card driver is being loaded from the inital ram fs? And when you unload/reload it it loads from your compiled/installed version. In the non-working dmesg I see:-
PCI INT A disabled
And in the working (napi) version the int isn't disabled. From what I understand napi changes the way the interrupts for network cards are handled. 

To test this recreate the initramfs with:-
sudo update-initramfs -u

Regards
Ian Dobson

---

### Post by LarryIB on 2011-10-30
> Could it be that when you boot the network card driver is being loaded  from the inital ram fs? And when you unload/reload it it loads from your  compiled/installed version. In the non-working dmesg I see:-
PCI INT A disabled
And in the working (napi) version the int isn't disabled. From what I  understand napi changes the way the interrupts for network cards are  handled. 

To test this recreate the initramfs with:-
sudo update-initramfs -u

Yes! After updating the initial ram fs Ubuntu loads the "compiled" version at boot time. I learn something new today :-)

Thanks Ian!

---

### Post by ian dobson on 2011-10-30
> **LarryIB said:**
> Yes! After updating the initial ram fs Ubuntu loads the "compiled" version at boot time. I learn something new today :-)

Thanks Ian!

Glad to of service.

When linux boots, the kernel needs to load some drivers so that it can mount the root file system. As the boot loader can read/load the kernel it also has to load the inital ram disk. Normally the inital ram fs, contains enough drivers (raid sw when rootfs is on a raid array, network drivers just incase the root fs is on a ntf mount, sata/ide drivers for normal harddisks). Rebuilding the inital ram fs causes the currently installed drivers from /lib/modules/Kernel-Version are loaded into the inital ram fs.

Regards
Ian Dobson

---

