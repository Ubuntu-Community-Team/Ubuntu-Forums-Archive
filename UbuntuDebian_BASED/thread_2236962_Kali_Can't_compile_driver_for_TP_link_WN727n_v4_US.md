---
title: "Kali: Can't compile driver for TP link WN727n v4 USB wireless adapter"
date: 2014-07-29
forum: Ubuntu/Debian BASED
---

### Post by Hanna_Aggarwal on 2014-07-29
[SIZE=4]Hello Varun

I may be posting in the wrong section, however i think this issue is in the same regards.................................................................................I have followed your "Wireless Script" and generated the following log.

FYI: I have a broadcom card which i habe disabled even before installing linux, I have TP link WN727n v 4 usb card for which i need help, it uses MT7601 drivers, i have tried compliling but failed....Please help



Following is the info from you script[/SIZE]

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

dhcppc5 3.14-kali1-686-pae i686,  Debian GNU/Linux Kali Linux 1.0.8, n/a

CPU    : Intel(R) Core(TM) i3-3110M CPU @ 2.40GHz
Memory : 3913 MB
Uptime : 00:07:32 up  1:21,  3 users,  load average: 0.30, 0.26, 0.34


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Lenovo Device [17aa:3975]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. Card reader
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0bc2:2312 Seagate RSS LLC 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b2e1 Chicony Electronics Co., Ltd 
Bus 001 Device 008: ID 148f:7601 Ralink Technology, Corp. 
Bus 001 Device 005: ID 04f3:0235 Elan Microelectronics Corp. 
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                  Soft blocked  Hard blocked
0: ideapad_bluetooth: Bluetooth      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rt2800usb              21813  0 
rt2x00usb              17426  1 rt2800usb
rt2800lib              72679  1 rt2800usb
rt2x00lib              41387  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              427800  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              369089  2 mac80211,rt2x00lib
crc_ccitt              12331  1 rt2800lib
mxm_wmi                12467  1 nouveau
wmi                    17147  2 mxm_wmi,nouveau
usbcore               142158  9 uvcvideo,rts5139,rt2x00usb,usb_storage,rt2800usb,ehci_hcd,ehci_pci,usbhid,xhci_hcd


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rt2800usb     (1): nohwcrypt=N
usbcore       (9): authorized_default=-1 | autosuspend=2 | blinkenlights=N | initial_descriptor_timeout=5000 | nousb=N | old_scheme_first=N | usbfs_memory_mb=16 | usbfs_snoop=N | use_both_schemes=Y
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
================o=======o========o===========o=========o===========o==============o===========
 Interface & ID | Type  | Driver | State     | Default | Speed     | Support      | HW Addr   
================o=======o========o===========o=========o===========o==============o===========
 eth0           | Wired | r8169  | unmanaged | no      | 100 Mb/s  |              | <MAC eth0>
----------------+-------+--------+-----------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet dhcp

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 4.2.2.2
nameserver 8.8.8.8


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.15.0.1      0.0.0.0         UG    0      0        0 eth0
172.15.0.0      0.0.0.0         255.255.255.0   U     0      0        0 eth0

--- 172.15.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.716/1.380/2.045/0.665 ms

--- 4.2.2.2 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 146.566/146.603/146.641/0.384 ms

--- 8.8.8.8 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 5.535/6.269/7.003/0.734 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (N/A, 20)
    (2457 - 2482 @ 40), (N/A, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (N/A, 20), PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 80), (N/A, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 80), (N/A, 20), PASSIVE-SCAN, NO-IBSS
    (57240 - 63720 @ 2160), (N/A, 0)


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-libnfc.conf]
blacklist nfc
blacklist pn533


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rt2800usb]
filename:       /lib/modules/3.14-kali1-686-pae/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
firmware:       rt2870.bin
version:        2.3.0
srcversion:     8D709655B6AD993F0D5ACC4
depends:        rt2x00lib,rt2800lib,rt2x00usb,usbcore
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/3.14-kali1-686-pae/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
version:        2.3.0
srcversion:     44768071492503F8EFE1EED
depends:        usbcore,rt2x00lib,mac80211

[rt2800lib]
filename:       /lib/modules/3.14-kali1-686-pae/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
version:        2.3.0
srcversion:     045B7E84F3DBB154C7AEC06
depends:        rt2x00lib,mac80211,crc-ccitt

[rt2x00lib]
filename:       /lib/modules/3.14-kali1-686-pae/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
version:        2.3.0
srcversion:     6791C3895D6D2F5D832F327
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.14-kali1-686-pae/kernel/net/mac80211/mac80211.ko
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.14-kali1-686-pae/kernel/net/wireless/cfg80211.ko
depends:        rfkill
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[crc_ccitt]
filename:       /lib/modules/3.14-kali1-686-pae/kernel/lib/crc-ccitt.ko
depends:        

[mxm_wmi]
filename:       /lib/modules/3.14-kali1-686-pae/kernel/drivers/platform/x86/mxm-wmi.ko
depends:        wmi

[wmi]
filename:       /lib/modules/3.14-kali1-686-pae/kernel/drivers/platform/x86/wmi.ko
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[usbcore]
filename:       /lib/modules/3.14-kali1-686-pae/kernel/drivers/usb/core/usbcore.ko
depends:        usb-common
parm:           usbfs_snoop:true to log all usbfs traffic (bool)
parm:           usbfs_memory_mb:maximum MB allowed for usbfs buffers (0 = no limit) (uint)
parm:           authorized_default:Default USB device authorization: 0 is not authorized, 1 is authorized, -1 is authorized except for wireless USB (default, old behaviour (int)
parm:           blinkenlights:true to cycle leds on hubs (bool)
parm:           initial_descriptor_timeout:initial 64-byte descriptor request timeout in milliseconds (default 5000 - 5.0 seconds) (int)
parm:           old_scheme_first:start with the old device initialization scheme (bool)
parm:           use_both_schemes:try the other device initialization scheme if the first one fails (bool)
parm:           autosuspend:default autosuspend delay (int)
parm:           nousb:bool


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
loop

[/etc/modprobe.d]
radeon-kms.conf   : options radeon modeset=1
rt2800usb.conf    : install rt2800usb modprobe --ignore-install rt2800usb ; /bin/echo "148f 5370" > /sys/bus/usb/drivers/rt2800usb/new_id


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.14-kali1-686-pae root=UUID=ebd3ba28-2095-402e-ac35-1a14fab3367f ro initrd=/install/initrd.gz quiet


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.007242] Initializing cgroup subsys net_cls
[    1.454057] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.454391] audit: initializing netlink subsys (disabled)
[    1.920068] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.166651] platform microcode: firmware: direct-loading firmware intel-ucode/06-3a-09
[    3.167918] platform microcode: firmware: direct-loading firmware intel-ucode/06-3a-09
[    3.168674] platform microcode: firmware: direct-loading firmware intel-ucode/06-3a-09
[    3.169445] platform microcode: firmware: direct-loading firmware intel-ucode/06-3a-09
[    6.643961] wmi: Mapper loaded
[   19.750077] r8169 0000:03:00.0: firmware: direct-loading firmware rtl_nic/rtl8105e-1.fw

    ======== Done ========
```

Below is the result of the command to make the compilation/installation of said drivers

```

root@dhcppc5:~/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913# sudo make
make -C tools
make[1]: Entering directory `/root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools'
/root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools/bin2h
cp -f os/linux/Makefile.6 /root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/Makefile
make -C /lib/modules/3.14-kali1-686-pae/build SUBDIRS=/root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.14-kali1-686-pae'
  CC [M]  /root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.o
/root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOsUsDelay’:
/root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:179:8: warning: unused variable ‘i’ [-Wunused-variable]
/root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘__RtmpOSFSInfoChange’:
/root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:1121:20: error: incompatible types when assigning to type ‘int’ from type ‘kuid_t’
/root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:1122:20: error: incompatible types when assigning to type ‘int’ from type ‘kgid_t’
/root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpDrvAllRFPrint’:
/root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2052:4: warning: passing argument 2 of ‘file_w->f_op->write’ from incompatible pointer type [enabled by default]
/root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2052:4: note: expected ‘const char *’ but argument is of type ‘UINT32 *’
/root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2037:22: warning: unused variable ‘macValue’ [-Wunused-variable]
/root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2037:9: warning: unused variable ‘macAddr’ [-Wunused-variable]
/root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSIRQRelease’:
/root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2173:21: warning: unused variable ‘net_dev’ [-Wunused-variable]
make[4]: *** [/root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.o] Error 1
make[3]: *** [_module_/root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux] Error 2
make[2]: *** [sub-make] Error 2
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.14-kali1-686-pae'
make: *** [LINUX] Error 2
```

---

### Post by varunendra on 2014-07-30
Found a patch suggested here : [http://askubuntu.com/a/477708](http://askubuntu.com/a/477708) - the official source of the modified driver and the patch are not mentioned in the post.

However, I just compared the entire directory with the official driver downloaded from Ralink's site : [http://www.mediatek.com/en/downloads/mt7601u-usb](http://www.mediatek.com/en/downloads/mt7601u-usb)
..and apparently three files have some small changes, which to me seem to be related to LED behaviour.

The critical change, the patch that seems to be intended to fix the compiling error, is just two words in "include/os/rt_linux.h" file. So let's start with the minimal change and see if it works.

Please open the "include/os/rt_linux.h" file from the directory extracted from the downloaded driver package, and look for these lines (they are currently line numbers 282, 283) -
```
	int				fsuid;
	int				fsgid;
```
Change them to -
```
	kuid_t				fsuid;
	kgid_t				fsgid;
```
Save > close and retry to compile it with -
```
make clean
make
```
Does it compile successfully now? If yes, go ahead and do -
```
sudo make install
sudo modprobe -v mt7601Usta
```
..and post back if it works.

However, if it still fails to compile, or doesn't work after installation, report back the error/problem and we may try something else.

---

### Post by golia2tive on 2014-08-18
hi varunendra,

here are "make" output:
```
root@kali:~/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913# make
make -C tools
make[1]: Entering directory `/root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools'
/root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools/bin2h
cp -f os/linux/Makefile.6 /root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/Makefile
make -C /lib/modules/3.14-kali1-686-pae/build SUBDIRS=/root/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux modules
make[1]: Entering directory `/lib/modules/3.14-kali1-686-pae/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/3.14-kali1-686-pae/build'
make: *** [LINUX] Error 2

```

the command 5th from down side up "make -C /lib/...." from my first try told: "make -C /lib/modules/3.14-kali1-686-pae/build:  No such file or directory". so I went to the folder and manually created a folder named "build". Then I do:
```

make clean
make

```
and the CODE tag above is the output
plz help me

---

### Post by golia2tive on 2014-08-18
well, the instructions worked with backtrack 5r3 (no error happened)
"iwconfig" output after install:
```

ra0 Ralink STA

```
but I dont know how to manage and use the card. wifite.py still cannot detect any wifi card :guitar:

---

