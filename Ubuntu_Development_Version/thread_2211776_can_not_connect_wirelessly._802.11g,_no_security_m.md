---
title: "can not connect wirelessly. 802.11g, no security makes no diff"
date: 2014-03-17
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-03-17
Trying to connect to my wireless netgear router.

Bus 001 Device 003: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter

and a mn-730 pci card which uses broadcom legacy, (little led flashes)

What can I do to make it work?
I know the RT5370 worked in 13.10

---

### Post by sdowney717 on 2014-03-17
[https://help.ubuntu.com/community/WirelessTroubleshootingProcedure](https://help.ubuntu.com/community/WirelessTroubleshootingProcedure)

tried this, any ideas?
```
E: Package 'hwinfo' has no installation candidate
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:24:21:9b:19:1e
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.3 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:43 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdfe0000-fdfeffff memory:febf0000-febfffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan1
       serial: 00:0f:53:82:2a:31
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.13.0-17-generic firmware=0.29 link=no multicast=yes wireless=IEEE 802.11bgn
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    ESSID:"4LPS2"
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    ESSID:"NETGEAR"
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu Trusty Tahr (development branch)"
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:529c]
	Kernel driver in use: r8169
Bus 001 Device 003: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1163:0200 DeLorme Publishing, Inc. Earthmate GPS (LT-20, LT-40)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0461:4d03 Primax Electronics, Ltd Kensington Mouse-in-a-box
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         connected       enabled         enabled    enabled         disabled  
H/W path        Device     Class       Description
==================================================
                           system      MS-7529 (To Be Filled By O.E.M.)
/0                         bus         MS-7529
/0/0                       memory      64KiB BIOS
/0/4                       processor   Intel(R) Core(TM)2 Duo CPU     E6550  @ 2
/0/4/5                     memory      64KiB L1 cache
/0/4/6                     memory      4MiB L2 cache
/0/27                      memory      4GiB System Memory
/0/27/0                    memory      2GiB DIMM SDRAM Synchronous
/0/27/1                    memory      2GiB DIMM SDRAM Synchronous
/0/100                     bridge      82G33/G31/P35/P31 Express DRAM Controller
/0/100/1                   bridge      82G33/G31/P35/P31 Express PCI Express Roo
/0/100/1/0                 display     RV535 [Radeon X1650 PRO]
/0/100/1/0.1               display     RV535 [Radeon X1650 PRO] (Secondary)
/0/100/1b                  multimedia  NM10/ICH7 Family High Definition Audio Co
/0/100/1c                  bridge      NM10/ICH7 Family PCI Express Port 1
/0/100/1c.1                bridge      NM10/ICH7 Family PCI Express Port 2
/0/100/1c.1/0   eth0       network     RTL8111/8168/8411 PCI Express Gigabit Eth
/0/100/1d                  bus         NM10/ICH7 Family USB UHCI Controller #1
/0/100/1d.1                bus         NM10/ICH7 Family USB UHCI Controller #2
/0/100/1d.2                bus         NM10/ICH7 Family USB UHCI Controller #3
/0/100/1d.3                bus         NM10/ICH7 Family USB UHCI Controller #4
/0/100/1d.7                bus         NM10/ICH7 Family USB2 EHCI Controller
/0/100/1e                  bridge      82801 PCI Bridge
/0/100/1f                  bridge      82801GB/GR (ICH7 Family) LPC Interface Br
/0/100/1f.1                storage     82801G (ICH7 Family) IDE Controller
/0/100/1f.2                storage     NM10/ICH7 Family SATA Controller [IDE mod
/0/100/1f.3                bus         NM10/ICH7 Family SMBus Controller
/0/1            scsi0      storage     
/0/1/0.0.0      /dev/sda   disk        200GB WDC WD2000JB-00G
/0/1/0.0.0/1    /dev/sda1  volume      9536MiB EXT4 volume
/0/1/0.0.0/2    /dev/sda2  volume      176GiB Extended partition
/0/1/0.0.0/2/5  /dev/sda5  volume      4094MiB Linux swap / Solaris partition
/0/1/0.0.0/2/6  /dev/sda6  volume      172GiB Linux filesystem partition
/1              wlan1      network     Wireless interface
Linux boat-MS-7529 3.13.0-17-generic #37-Ubuntu SMP Mon Mar 10 21:44:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
[    0.000000] No AGP bridge found
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
[    0.000000] No NUMA configuration found
[    0.000000] No AGP bridge found
[    0.122615] ACPI: No dock devices found.
[    0.141455] Found 1 acpi root devices
[    0.141533] usbcore: registered new interface driver usbfs
[    0.141533] usbcore: registered new interface driver hub
[    0.141533] usbcore: registered new device driver usb
[    0.150165] Switched to clocksource hpet
[    0.158058] pnp: PnP ACPI: found 17 devices
[    0.547367] Console: switching to colour frame buffer device 80x30
[    0.616084] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.616087] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.616090] usb usb1: Product: EHCI Host Controller
[    0.616093] usb usb1: Manufacturer: Linux 3.13.0-17-generic ehci_hcd
[    0.616095] usb usb1: SerialNumber: 0000:00:1d.7
[    0.616217] hub 1-0:1.0: USB hub found
[    0.616582] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.616584] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.616587] usb usb2: Product: UHCI Host Controller
[    0.616589] usb usb2: Manufacturer: Linux 3.13.0-17-generic uhci_hcd
[    0.616591] usb usb2: SerialNumber: 0000:00:1d.0
[    0.616679] hub 2-0:1.0: USB hub found
[    0.616909] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.616912] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.616914] usb usb3: Product: UHCI Host Controller
[    0.616916] usb usb3: Manufacturer: Linux 3.13.0-17-generic uhci_hcd
[    0.616919] usb usb3: SerialNumber: 0000:00:1d.1
[    0.617006] hub 3-0:1.0: USB hub found
[    0.617242] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.617245] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.617247] usb usb4: Product: UHCI Host Controller
[    0.617250] usb usb4: Manufacturer: Linux 3.13.0-17-generic uhci_hcd
[    0.617252] usb usb4: SerialNumber: 0000:00:1d.2
[    0.617338] hub 4-0:1.0: USB hub found
[    0.617570] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.617572] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.617575] usb usb5: Product: UHCI Host Controller
[    0.617577] usb usb5: Manufacturer: Linux 3.13.0-17-generic uhci_hcd
[    0.617579] usb usb5: SerialNumber: 0000:00:1d.3
[    0.617664] hub 5-0:1.0: USB hub found
[    0.620690] Loaded X.509 cert 'Magrathea: Glacier signing key: 20a8b3c93dd3ff225705f25f2fef4bfbe5d27149'
[    0.628014] IMA: No TPM chip found, activating TPM-bypass!
[    0.628733] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.874181] r8169 0000:03:00.0 eth0: RTL8168c/8111c at 0xffffc90000678000, 00:24:21:9b:19:1e, XID 1c4000c0 IRQ 43
[    0.874184] r8169 0000:03:00.0 eth0: jumbo features [frames: 6128 bytes, tx checksumming: ko]
[    0.984043] usb 1-2: new high-speed USB device number 3 using ehci-pci
[    1.133588] usb 1-2: New USB device found, idVendor=148f, idProduct=5370
[    1.133592] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.133595] usb 1-2: Product: 802.11 n WLAN
[    1.133598] usb 1-2: Manufacturer: Ralink
[    1.133600] usb 1-2: SerialNumber: 1.0
[    1.632050] usb 3-1: new full-speed USB device number 2 using uhci_hcd
[    1.809896] usb 3-1: New USB device found, idVendor=1163, idProduct=0200
[    1.809901] usb 3-1: New USB device strings: Mfr=4, Product=42, SerialNumber=0
[    1.809904] usb 3-1: Product: DeLorme USB Earthmate      
[    1.809907] usb 3-1: Manufacturer: DeLorme Publishing
[    2.184071] usb 2-1: new low-speed USB device number 2 using uhci_hcd
[    2.368040] usb 2-1: New USB device found, idVendor=0461, idProduct=4d03
[    2.368044] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.368047] usb 2-1: Product: USB 3D Mouse
[    2.368050] usb 2-1: Manufacturer: ARROW STRONG
[    2.504084] Switched to clocksource tsc
[   13.673765] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.844020] lp: driver loaded but no devices found
[   14.036178] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   14.037425] input: HDA Intel Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   14.037501] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   14.037566] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   14.037630] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input3
[   14.038128] Console: switching to colour dummy device 80x25
[   14.042219] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   14.044860] leds_ss4200: no LED devices found
[   14.647233] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   14.696053] usbcore: registered new interface driver usbserial
[   14.696085] usbcore: registered new interface driver usbserial_generic
[   14.696113] usbserial: USB Serial support registered for generic
[   14.697795] usbcore: registered new interface driver cypress_m8
[   14.697825] usbserial: USB Serial support registered for DeLorme Earthmate USB
[   14.697853] usbserial: USB Serial support registered for HID->COM RS232 Adapter
[   14.697881] usbserial: USB Serial support registered for Nokia CA-42 V2 Adapter
[   14.699960] usb 3-1: DeLorme Earthmate USB converter now attached to ttyUSB0
[   14.726325] usbcore: registered new interface driver usbhid
[   14.726328] usbhid: USB HID core driver
[   14.744172] Console: switching to colour frame buffer device 128x48
[   14.927687] cfg80211: Calling CRDA to update world regulatory domain
[   14.942424] input: ARROW STRONG USB 3D Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input8
[   14.950417] hid-generic 0003:0461:4D03.0001: input,hidraw0: USB HID v1.00 Mouse [ARROW STRONG USB 3D Mouse] on usb-0000:00:1d.0-1/input0
[   15.291058] cfg80211: World regulatory domain updated:
[   15.291062] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.291065] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.291067] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.291069] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.291071] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.291073] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.292576] usb 1-2: reset high-speed USB device number 3 using ehci-pci
[   15.434589] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[   15.462713] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5370 detected
[   15.509458] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   15.509772] usbcore: registered new interface driver rt2800usb
[   15.568151] systemd-udevd[286]: renamed network interface wlan0 to wlan1
[   17.517180] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   20.013311] r8169 0000:03:00.0 eth0: link down
[   20.013344] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.013680] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.015473] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   20.055769] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   20.285887] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   20.286233] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   56.884168] wlan1: authenticate with 00:18:4d:58:f9:a4
[   56.917165] wlan1: send auth to 00:18:4d:58:f9:a4 (try 1/3)
[   56.918625] wlan1: authenticated
[   56.918772] rt2800usb 1-2:1.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[   56.918775] rt2800usb 1-2:1.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[   56.920120] wlan1: associate with 00:18:4d:58:f9:a4 (try 1/3)
[   57.028075] wlan1: associate with 00:18:4d:58:f9:a4 (try 2/3)
[   57.132025] wlan1: associate with 00:18:4d:58:f9:a4 (try 3/3)
[   57.236031] wlan1: association with 00:18:4d:58:f9:a4 timed out
[   58.492163] wlan1: authenticate with 00:18:4d:58:f9:a4
[   58.505156] wlan1: send auth to 00:18:4d:58:f9:a4 (try 1/3)
[   58.506614] wlan1: authenticated
[   58.506731] rt2800usb 1-2:1.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[   58.506735] rt2800usb 1-2:1.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[   58.508040] wlan1: associate with 00:18:4d:58:f9:a4 (try 1/3)
[   58.616028] wlan1: associate with 00:18:4d:58:f9:a4 (try 2/3)
[   58.720026] wlan1: associate with 00:18:4d:58:f9:a4 (try 3/3)
[   58.824033] wlan1: association with 00:18:4d:58:f9:a4 timed out
[   60.480746] wlan1: authenticate with 00:18:4d:58:f9:a4
[   60.497037] wlan1: send auth to 00:18:4d:58:f9:a4 (try 1/3)
[   60.498490] wlan1: authenticated
[   60.498601] rt2800usb 1-2:1.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[   60.498605] rt2800usb 1-2:1.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[   60.500047] wlan1: associate with 00:18:4d:58:f9:a4 (try 1/3)
[   60.604025] wlan1: associate with 00:18:4d:58:f9:a4 (try 2/3)
[   60.708028] wlan1: associate with 00:18:4d:58:f9:a4 (try 3/3)
[   60.812025] wlan1: association with 00:18:4d:58:f9:a4 timed out
[   62.952117] wlan1: authenticate with 00:18:4d:58:f9:a4
[   62.965034] wlan1: send auth to 00:18:4d:58:f9:a4 (try 1/3)
[   62.966489] wlan1: authenticated
[   62.966598] rt2800usb 1-2:1.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[   62.966602] rt2800usb 1-2:1.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[   62.968047] wlan1: associate with 00:18:4d:58:f9:a4 (try 1/3)
[   63.072026] wlan1: associate with 00:18:4d:58:f9:a4 (try 2/3)
[   63.176023] wlan1: associate with 00:18:4d:58:f9:a4 (try 3/3)
[   63.280032] wlan1: association with 00:18:4d:58:f9:a4 timed out
[   75.548159] wlan1: authenticate with 00:18:4d:58:f9:a4
[   75.561036] wlan1: send auth to 00:18:4d:58:f9:a4 (try 1/3)
[   75.562494] wlan1: authenticated
[   75.562605] rt2800usb 1-2:1.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[   75.562609] rt2800usb 1-2:1.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[   75.564093] wlan1: associate with 00:18:4d:58:f9:a4 (try 1/3)
[   75.668025] wlan1: associate with 00:18:4d:58:f9:a4 (try 2/3)
[   75.772022] wlan1: associate with 00:18:4d:58:f9:a4 (try 3/3)
[   75.876034] wlan1: association with 00:18:4d:58:f9:a4 timed out
[  102.184883] r8169 0000:03:00.0 eth0: link up
[  102.184893] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
	Release Date: 11/24/2008
		Serial services are supported (int 14h)
	Manufacturer: MICRO-STAR INTERNATIONAL CO.,LTD
	Product Name: MS-7529
	Serial Number: 106952006
	Manufacturer: MICRO-STAR INTERNATIONAL CO.,LTD
	Product Name: MS-7529
	Serial Number: To be filled by O.E.M.
	Manufacturer: MICRO-STAR INTERNATIONAL CO.,LTD
	Serial Number: snc302eeh
	Manufacturer: Intel            
	Serial Number: To Be Filled By O.E.M.
	Port Type: Serial Port 16550A Compatible
	Manufacturer: Manufacturer0
	Serial Number: SerNum0
	Manufacturer: Manufacturer1
	Serial Number: SerNum1
wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

lo        no wireless extensions.

install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
sudo: hwinfo: command not found
root       867  0.0  0.1 334388  6336 ?        Ssl  18:12   0:00 NetworkManager
root      1031  0.0  0.0  30608  2448 ?        Ss   18:12   0:00 /sbin/wpa_supplicant -B -P /run/sendsigs.omit.d/wpasupplicant.pid -u -s -O /var/run/wpa_supplicant
root      2067  0.0  0.0  10232  3700 ?        S    18:14   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /run/sendsigs.omit.d/network-manager.dhclient-eth0.pid -lf /var/lib/NetworkManager/dhclient-dcfad161-a9ca-4b48-8e4c-f195e793f68b-eth0.lease -cf /var/lib/NetworkManager/dhclient-eth0.conf eth0
nobody    2076  0.0  0.0  31028  1532 ?        S    18:14   0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/NetworkManager/dnsmasq.pid --listen-address=127.0.1.1 --conf-file=/var/run/NetworkManager/dnsmasq.conf --cache-size=0 --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
boat      2672  0.0  0.0   9448   892 pts/0    S+   18:29   0:00 egrep --color=auto wpa|icd|etwork
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
total 56008
   12 drwxr-xr-x  3 root root     4096 Mar 16 16:14 .
    2 drwxr-xr-x 23 root root     4096 Mar 16 15:52 ..
 5437 -rw-r--r--  1 root root  1007681 Feb 18 16:37 abi-3.11.0-18-generic
12378 -rw-r--r--  1 root root  1161352 Mar 10 18:42 abi-3.13.0-17-generic
 6688 -rw-r--r--  1 root root   163258 Feb 18 16:37 config-3.11.0-18-generic
12380 -rw-r--r--  1 root root   165249 Mar 10 18:42 config-3.13.0-17-generic
   21 drwxr-xr-x  5 root root     4096 Mar 16 16:11 grub
  338 -rw-r--r--  1 root root 17438426 Mar 16 15:17 initrd.img-3.11.0-18-generic
17089 -rw-r--r--  1 root root 18773928 Mar 16 16:14 initrd.img-3.13.0-17-generic
 4948 -rw-r--r--  1 root root   176500 Mar 12 08:31 memtest86+.bin
 4947 -rw-r--r--  1 root root   178176 Mar 12 08:31 memtest86+.elf
 4949 -rw-r--r--  1 root root   178680 Mar 12 08:31 memtest86+_multiboot.bin
 6689 -rw-------  1 root root  3296162 Feb 18 16:37 System.map-3.11.0-18-generic
12381 -rw-------  1 root root  3369592 Mar 10 18:42 System.map-3.13.0-17-generic
 5436 -rw-------  1 root root  5634192 Feb 18 16:37 vmlinuz-3.11.0-18-generic
12379 -rw-------  1 root root  5767264 Mar 10 18:42 vmlinuz-3.13.0-17-generic
Support status summary of 'boat-MS-7529':

You have 1952 packages (87.9%) supported until December 2014 (9m)

You have 10 packages (0.5%) that can not/no-longer be downloaded
You have 259 packages (11.7%) that are unsupported

Run with --show-unsupported, --show-supported or --show-all to see more details
Module                  Size  Used by
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             395423  10 bnep,rfcomm
binfmt_misc            17468  1 
arc4                   12608  2 
rt2800usb              27034  0 
rt2x00usb              20742  1 rt2800usb
rt2800lib              89076  1 rt2800usb
rt2x00lib              55307  3 rt2x00usb,rt2800lib,rt2800usb
hid_generic            12548  0 
mac80211              626584  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              490477  2 mac80211,rt2x00lib
crc_ccitt              12707  1 rt2800lib
gpio_ich               13476  0 
ppdev                  17671  0 
usbhid                 52616  0 
cypress_m8             20458  0 
usbserial              45014  1 cypress_m8
hid                   106148  2 hid_generic,usbhid
coretemp               13435  0 
kvm_intel             143060  0 
kvm                   451519  1 kvm_intel
radeon               1514262  3 
lpc_ich                21080  0 
ttm                    85115  1 radeon
serio_raw              13462  0 
drm_kms_helper         52758  1 radeon
snd_hda_codec_realtek    61356  1 
drm                   302631  5 ttm,drm_kms_helper,radeon
snd_hda_intel          52355  3 
snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
i2c_algo_bit           13413  1 radeon
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
parport_pc             32701  1 
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mac_hid                13205  0 
soundcore              12680  1 snd
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
r8169                  67581  0 
mii                    13934  1 r8169
floppy                 69370  0 
boat@boat-MS-7529:~$ 

```

---

### Post by sdowney717 on 2014-03-17
```
[   75.564093] wlan1: associate with 00:18:4d:58:f9:a4 (try 1/3)
[   75.668025] wlan1: associate with 00:18:4d:58:f9:a4 (try 2/3)
[   75.772022] wlan1: associate with 00:18:4d:58:f9:a4 (try 3/3)
[   75.876034] wlan1: association with 00:18:4d:58:f9:a4 timed out
```

I assume this is saying it did not connect to the router?
I also rebooted router.

---

### Post by sdowney717 on 2014-03-17
Since I started with the mn-730 
I followed this guide.
[http://www.howopensource.com/2012/10/install-broadcom-b43-legacy-wireless-driver-in-ubuntu-12-10-12-04/](http://www.howopensource.com/2012/10/install-broadcom-b43-legacy-wireless-driver-in-ubuntu-12-10-12-04/)
It is legacy broadcom.

Any effect on because of that,  making the usb thingy fail?

---

### Post by sdowney717 on 2014-03-17
[http://superuser.com/questions/692229/install-driver-for-rt5370-on-ubuntu](http://superuser.com/questions/692229/install-driver-for-rt5370-on-ubuntu)

tried this
>  sudo apt-get install linux-firmware-nonfree
  sudo rmmod rt5572sta
  sudo modprobe rt2800usb

reboot still no good.

---

### Post by sdowney717 on 2014-03-17
trying wifi radar, it crashes.

[http://www.linux.com/learn/tutorials/374514-control-wireless-on-the-linux-desktop-with-these-tools](http://www.linux.com/learn/tutorials/374514-control-wireless-on-the-linux-desktop-with-these-tools)

---

### Post by sdowney717 on 2014-03-17
Just tried the USB wifi device in another ubuntu trusty PC and it can not connect.

Next step, should I bother setting up a different wireless router to see if that is an issue?
Or just abandon the effort till new updates fix it?

---

### Post by sdowney717 on 2014-03-17
Ok, I just booted off the live usb with the usb wifi plugged in.

Disconnected the wired lan

Connected to wireless router and it is working, in the live usb.

So why is that?
Nothing wrong with the router then.
Must be the OS.

Anything can be done to see what is up with this?

---

### Post by xc3RnbFO8P on 2014-03-18
Check this, I had this problem missing the DK (Denmark) in crda :

---

### Post by sdowney717 on 2014-03-18
After updates today, 

> Bus 001 Device 003: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter

can connect to a verizon wireless router.:P
But cant connect to my netgear router in the same room even with security off, go figure.:(

I have 4 wireless routers, I only have been using one of the netgears. I know it works because my daughter visits and she connects. And this PC can connect to it using the RALink.
Wireless has always been flakey tech IMO

Which is why I ran cat5e all over the house.

---

