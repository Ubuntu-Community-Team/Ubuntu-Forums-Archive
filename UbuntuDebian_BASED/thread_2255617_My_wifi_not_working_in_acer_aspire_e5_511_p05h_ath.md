---
title: "My wifi not working in acer aspire e5 511 p05h atheros driver missing"
date: 2014-12-06
forum: Ubuntu/Debian BASED
---

### Post by p-eldhose on 2014-12-06
hi all, 
am trying to setup my wifi on my laptop Acer aspire e5 511-P-05H . i install debian os in it . 
m attaching my Wireless info script result ... pls help 




########## wireless info START ##########


Report from: 07 Dec 2014 02:52 IST +0530


Booted last: 07 Dec 2014 02:49 IST +0530


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Debian
Description:	Debian GNU/Linux 7.7 (wheezy)
Release:	7.7
Codename:	wheezy


##### kernel ############################


Linux 3.2.0-4-amd64 #1 SMP Debian 3.2.63-2+deb7u1 x86_64 unknown unknown GNU/Linux


Parameters: ro, initrd=/install/initrd.gz, quiet


##### desktop ###########################


sed: can't read /root/.dmrc: No such file or directory
Could not be determined.


##### lspci #############################


01:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 12)
	Subsystem: Acer Incorporated [ALI] Device [1025:0905]
	Kernel driver in use: r8169


02:00.0 Network controller [0280]: Atheros Communications Inc. AR9565 Wireless Network Adapter [168c:0036] (rev 01)
	Subsystem: Lite-On Communications Inc Device [11ad:0642]


##### lsusb #############################


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:07e6 Intel Corp. 
Bus 003 Device 003: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 003 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 005: ID 064e:9400 Suyin Corp. 
Bus 003 Device 006: ID 04ca:300b Lite-On Technology Corp. 


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: acer-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


acer_wmi               26081  0 
sparse_keymap          12760  1 acer_wmi
rfkill                 19012  4 bluetooth,acer_wmi
wmi                    13243  1 acer_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::f276:1cff:fe33:f441/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:46 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30705 (29.9 KiB)  TX bytes:19165 (18.7 KiB)
          Interrupt:104 Base address:0x8000 


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0


##### resolv.conf #######################


nameserver 192.168.0.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile


[ifupdown]
managed=false


##### NetworkManager profiles ###########


##### iw reg get ########################


nl80211 not found.


##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


##### /etc/modules ######################


loop


##### modprobe options ##################


[/etc/modprobe.d/open-vm-tools.conf]
install pcnet32 /sbin/modprobe -q --ignore-install vmxnet; /sbin/modprobe -q --ignore-install pcnet32 $CMDLINE_OPTS; /bin/true;


[/etc/modprobe.d/radeon-kms.conf]
options radeon modeset=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.1 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


########## wireless info END ############

---

### Post by chili555 on 2014-12-06
We don't know much about Debian but we know that your relatively new wireless device isn't covered in your relatively old 3.2.xx kernel. In Ubuntu, we'd install linux-backports-modules-cw-3.8 or newer; so as to install the 3.8.xx or newer wireless drivers in your 3.2.xx kernel. As to how exactly to accomplish this in Debian is unknown to me.

<rant>
I'm always a bit perplexed when users cling to a kernel version about three years behind the curve. I always wonder what features don't work in 3.16.xx; that is, Ubuntu 14.10, that magically *DO* work in 3.2.xx. Why doesn't my 1978 Ford have airbags, nav and get 35 mpg?
</rant>

---

### Post by howefield on 2014-12-06
Thread moved to the "*Other Operating Systems*" forum.

---

