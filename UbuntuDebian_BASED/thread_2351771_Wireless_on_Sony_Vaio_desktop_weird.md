---
title: "Wireless on Sony Vaio desktop: weird"
date: 2017-02-06
forum: Ubuntu/Debian BASED
---

### Post by pns2 on 2017-02-06
Hi all,

A similar-but-different question to that asked by 4l3x2 a couple of days ago...

I have a Sony Vaio TP1 desktop. It's the [round one]("https://www.google.com/search?q=vgx+tp1&client=ubuntu&hs=POt&channel=fs&biw=1047&bih=497&tbm=isch&tbo=u&source=univ&sa=X&ved=0ahUKEwjo6dKUtvzRAhUJYpoKHRjeBPMQsAQIIA").

I am installing Lubuntu on it. Everything is fine except for connection to wifi.

Lubuntu asks for the wifi password, but then seems to reject it every time and ask for it again. I'm connecting through a plain old domestic [BT Smart Hub]("https://www.productsandservices.bt.com/products/smart-hub").

In Sony's... er... unique approach to hardware design, the Vaio doesn't come with an integral wireless antenna. Rather, it comes with an external one that plugs into the back of the unit. I'm wondering if that has anything to do with it, because I have installed Lubuntu on several Vaio laptops before (with an internal wifi antenna) without any problems.

Can anyone shed any light on this...?

Thanks in advance
Paul

---

### Post by wildmanne39 on 2017-02-06
Click on the wireless script in my signature and follow the directions for running it and posting the file it creates here using code tags.

---

### Post by pns2 on 2017-02-12
Couldn't get the script to work:

wireless-info.sh: 44: ./wireless-info.sh: Syntax error: "(" unexpected

:(

---

### Post by wildmanne39 on 2017-02-12
Just copy and paste this whole command into the terminal all at once not line by line, then enter your user password.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```
As you can see there is no .sh in the script or command.

---

### Post by wildmanne39 on 2017-02-12
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

---

### Post by pns2 on 2017-02-12
Will do. The filesystem might be FAT32, which is why I can't a+x the file either. Update coming shortly...

---

### Post by wildmanne39 on 2017-02-12
You can not install grub to a fat32, but I guess you could have installed it to sda then made your home partition fat32 possibly if that is the case then I would reinstall before going any further or back up your data and repartition that partition.
To check do:
```
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
```
that is a far off track as we can go in this thread if it is a fat32 and you need help please start a thread on that issue in the General sub-forum.
Thanks

---

### Post by pns2 on 2017-03-12
So sorry Wildmanee39. FAT32 was a red herring and Ubuntu screwed up on the computer, so I installed an old copy of ElementaryOS which I had lying around, and here's the output. Thanks so much. (wifi AP replaced with "mywirelessnetwork")

```


########## wireless info START ##########

Report from: 12 Mar 2017 17:32 EDT -0400

Booted last: 12 Mar 2017 17:28 EDT -0400

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    elementary OS
Description:    elementary OS Luna
Release:    0.2
Codename:    luna

##### kernel ############################

Linux 3.2.0-51-generic-pae #77-Ubuntu SMP Wed Jul 24 20:40:32 UTC 2013 i686 i686 i386 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Pantheon

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82562V 10/100 Network Connection [8086:104c] (rev 03)
    Subsystem: Sony Corporation Device [104d:9030]
    Kernel driver in use: e1000e

02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation Device [8086:1051]
    Kernel driver in use: iwl3945

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13fd:3940 Initio Corporation 
Bus 004 Device 002: ID 054c:024b Sony Corp. Vaio VGX Mouse
Bus 004 Device 003: ID 054c:037c Sony Corp. 
Bus 001 Device 005: ID 0204:6025 Chipsbank Microelectronics Co., Ltd CBM2080 Flash drive controller

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwl3945                73186  0 
iwl_legacy             71187  1 iwl3945
mac80211              436493  2 iwl3945,iwl_legacy
cfg80211              178877  3 iwl3945,iwl_legacy,mac80211
mxm_wmi                12893  1 nouveau
wmi                    18744  1 mxm_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f3300000-f3320000 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       715     1  0 17:28 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connecting

- Device: wlan0  [MYWIRELESSNETWORK] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC 'wlan0' [IF2]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    MYWIRELESSNETWORK:     Infra, <MAC 'MYWIRELESSNETWORK' [AN1]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 30 WPA2
    MYWIRELESSNETWORK:     Infra, <MAC 'MYWIRELESSNETWORK' [AN2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA2

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF1]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

Error executing command as another user: Request dismissed

Acquisition of admin privileges failed.

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz

##### iwlist scan #######################

Error executing command as another user: Request dismissed

Acquisition of admin privileges failed.

##### module infos ######################

[iwl3945]
filename:       /lib/modules/3.2.0-51-generic-pae/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     301B04B4010DED41B0830D0
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        iwl-legacy,cfg80211,mac80211
intree:         Y
vermagic:       3.2.0-51-generic-pae SMP mod_unload modversions 686 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

[iwl_legacy]
filename:       /lib/modules/3.2.0-51-generic-pae/kernel/drivers/net/wireless/iwlegacy/iwl-legacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     D949E7611CAAE3FC9AEDE7D
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.2.0-51-generic-pae SMP mod_unload modversions 686 
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

[mac80211]
filename:       /lib/modules/3.2.0-51-generic-pae/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     46CEFCE103007F8DF3A81B4
depends:        cfg80211
intree:         Y
vermagic:       3.2.0-51-generic-pae SMP mod_unload modversions 686 
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)

[cfg80211]
filename:       /lib/modules/3.2.0-51-generic-pae/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F264BD9F744E579E220FC4E
depends:        
intree:         Y
vermagic:       3.2.0-51-generic-pae SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwl3945]
antenna: 0
disable_hw_scan: 1
fw_restart: 1
swcrypto: 1

[iwl_legacy]
bt_coex_active: Y
led_mode: 0

[mac80211]
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp

##### modprobe options ##################

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/sleep.d/10_grub-common] (755 root)
case "$1" in
    thaw)
        [ -s /boot/grub/grubenv ] || rm -f /boot/grub/grubenv
        mkdir -p /boot/grub
        grub-editenv /boot/grub/grubenv unset recordfail
        ;;
esac

[/etc/pm/sleep.d/10_unattended-upgrades-hibernate] (755 root)
PATH=/sbin:/usr/sbin:/bin:/usr/bin
SHUTDOWN_HELPER=/usr/share/unattended-upgrades/unattended-upgrade-shutdown
if [ ! -x /usr/share/unattended-upgrades/unattended-upgrade-shutdown ]; then
    exit 0
fi
case "${1}" in
        hibernate)
                if [ -e $SHUTDOWN_HELPER ]; then
                 python $SHUTDOWN_HELPER
                fi
                ;;
        resume|thaw)
        # nothing
                ;;
esac

[/etc/pm/sleep.d/novatel_3g_suspend] (755 root)
BUS=2
DEVICE=2
if [ ! -x /sys/bus/usb/devices/${BUS}-${DEVICE}/power/level ]; then
    exit 0
fi
case $1 in
     suspend|suspend_hybrid|hibernate)
    echo suspend > /sys/bus/usb/devices/${BUS}-${DEVICE}/power/level
        ;;
     resume|thaw)
    # No need to do anything here, kernel unsuspends USB devices
    :
        ;;
esac

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

########## wireless info END ############


```

---

### Post by wildmanne39 on 2017-03-12
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by chili555 on 2017-03-12
This may be useful: [http://www.gizmodo.co.uk/2016/03/bt-home-hub-5-tips-tricks-settings/](http://www.gizmodo.co.uk/2016/03/bt-home-hub-5-tips-tricks-settings/)

---

### Post by mörgæs on 2017-03-13
> **pns2 said:**
> 
Linux 3.2.0-51-generic-pae #77-Ubuntu SMP Wed Jul 24 20:40:32 UTC 2013 i686 i686 i386 GNU/Linux

This is very old stuff. Regardless of the wirefree problem I suggest that you do a fresh install of L/Xubuntu 16.04.2 or a recent Elementary, if necessary with wired connection. 

After that it's time to try the advice posted here in the thread.

---

### Post by pns2 on 2017-03-19
Thanks all,

Installed Lubuntu 16.10 and then ran apt-get upgrade over a wired connection. Once the cable was taken out, the same symptoms as earlier (ie wireless would disconnect with the correct password) re-occurred. Here's the dump.

```

########## wireless info START ##########

Report from: 19 Mar 2017 21:35 GMT +0000

Booted last: 19 Mar 2017 00:00 GMT +0000

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.8.0-41-generic #44~16.04.1-Ubuntu SMP Fri Mar 3 17:11:03 UTC 2017 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82562V 10/100 Network Connection [8086:104c] (rev 03)
    Subsystem: Sony Corporation 82562V 10/100 Network Connection [104d:9030]
    Kernel driver in use: e1000e

02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:1051]
    Kernel driver in use: iwl3945

##### lsusb #############################

Bus 001 Device 002: ID 13fd:3940 Initio Corporation 
Bus 001 Device 005: ID 0204:6025 Chipsbank Microelectronics Co., Ltd CBM2080 / CBM2090 Flash drive controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 054c:037c Sony Corp. 
Bus 004 Device 002: ID 054c:024b Sony Corp. Vaio VGX Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwl3945                65536  0
iwlegacy               90112  1 iwl3945
mac80211              679936  2 iwlegacy,iwl3945
cfg80211              512000  3 mac80211,iwlegacy,iwl3945
mxm_wmi                16384  1 nouveau
wmi                    16384  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s25   Link encap:Ethernet  HWaddr <MAC 'enp0s25' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f3300000-f3320000 

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

enp0s25   no wireless extensions.

lo        no wireless extensions.

wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       730     1  0 21:31 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        PRO/Wireless 3945ABG [Golan] Network Connection
GENERAL.DRIVER:                         iwl3945
GENERAL.DRIVER-VERSION:                 4.8.0-41-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   42a9fcf6-f8f1-4b9c-b564-529d0878832e | MYWIRELESSNETWORK

GENERAL.DEVICE:                         enp0s25
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82562V 10/100 Network Connection
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.3-2
GENERAL.HWADDR:                         <MAC 'enp0s25' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/enp0s25
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID         BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
MYWIRELESSNETWORK  <MAC 'MYWIRELESSNETWORK' [AC4]>  Infra  36    5180 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2      no        
--           <MAC '' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  24      &#9602;___  --        no        
MYWIRELESSNETWORK  <MAC 'MYWIRELESSNETWORK' [AC3]>  Infra  11    2462 MHz  54 Mbit/s  17      &#9602;___  WPA2      no        
--           <MAC '--' [AN4]>  Infra  11    2462 MHz  54 Mbit/s  15      &#9602;___  --        no        
--           <MAC '' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  15      &#9602;___  --        no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/MYWIRELESSNETWORK]] (600 root)
[connection] id=MYWIRELESSNETWORK | type=wifi | permissions=user:vaiomedia:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=MYWIRELESSNETWORK
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp0s25   no frequency information.

lo        no frequency information.

wlp2s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz

##### iwlist scan #######################

enp0s25   Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz (Channel 36)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC '' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000012bff209264
                    Extra: Last beacon: 28364ms ago
          Cell 02 - Address: <MAC '' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000012c00aa5140
                    Extra: Last beacon: 2540ms ago
          Cell 03 - Address: <MAC 'MYWIRELESSNETWORK' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"MYWIRELESSNETWORK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012c00a73185
                    Extra: Last beacon: 2696ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'MYWIRELESSNETWORK' [AC4]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"MYWIRELESSNETWORK"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000012c00bea03c
                    Extra: Last beacon: 2284ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwl3945]
filename:       /lib/modules/4.8.0-41-generic/kernel/drivers/net/wireless/intel/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     426C5AE2C37FAEE73CFCC4E
depends:        iwlegacy,mac80211,cfg80211
intree:         Y
vermagic:       4.8.0-41-generic SMP mod_unload modversions 686 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

[iwlegacy]
filename:       /lib/modules/4.8.0-41-generic/kernel/drivers/net/wireless/intel/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     27B0CC79D616458D3CC644B
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.8.0-41-generic SMP mod_unload modversions 686 
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

[mac80211]
filename:       /lib/modules/4.8.0-41-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     9AF49B72127065FCF655D6A
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-41-generic SMP mod_unload modversions 686 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.8.0-41-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     46F63B461AA5E38D042F531
depends:        
intree:         Y
vermagic:       4.8.0-41-generic SMP mod_unload modversions 686 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwl3945]
antenna: 0
disable_hw_scan: 1
fw_restart: 1
swcrypto: 1

[iwlegacy]
bt_coex_active: Y
led_mode: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   22.287837] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   22.287839] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   22.287913] iwl3945 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   22.343722] iwl3945 0000:02:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   22.343726] iwl3945 0000:02:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   22.352211] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   22.355178] iwl3945 0000:02:00.0 wlp2s0: renamed from wlan0
[   26.026316] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   26.090967] iwl3945 0000:02:00.0: loaded firmware version 15.32.2.9
[   26.174333] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   26.184490] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready (repeated 2 times)
[   26.808679] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   55.144749] wlp2s0: authenticate with <MAC 'MYWIRELESSNETWORK' [AC4]>
[   55.149210] wlp2s0: send auth to <MAC 'MYWIRELESSNETWORK' [AC4]> (try 1/3)
[   55.352066] wlp2s0: send auth to <MAC 'MYWIRELESSNETWORK' [AC4]> (try 2/3)
[   55.560035] wlp2s0: send auth to <MAC 'MYWIRELESSNETWORK' [AC4]> (try 3/3)
[   55.764063] wlp2s0: authentication with <MAC 'MYWIRELESSNETWORK' [AC4]> timed out
[   55.944553] wlp2s0: authenticate with <MAC 'MYWIRELESSNETWORK' [AC3]>
[   55.947704] wlp2s0: send auth to <MAC 'MYWIRELESSNETWORK' [AC3]> (try 1/3)
[   56.148065] wlp2s0: send auth to <MAC 'MYWIRELESSNETWORK' [AC3]> (try 2/3)
[   56.352060] wlp2s0: send auth to <MAC 'MYWIRELESSNETWORK' [AC3]> (try 3/3)
[   56.556104] wlp2s0: authentication with <MAC 'MYWIRELESSNETWORK' [AC3]> timed out
[   60.012954] wlp2s0: authenticate with <MAC 'MYWIRELESSNETWORK' [AC4]>
[   60.017313] wlp2s0: send auth to <MAC 'MYWIRELESSNETWORK' [AC4]> (try 1/3)
[   60.220065] wlp2s0: send auth to <MAC 'MYWIRELESSNETWORK' [AC4]> (try 2/3)
[   60.424090] wlp2s0: send auth to <MAC 'MYWIRELESSNETWORK' [AC4]> (try 3/3)
[   60.628089] wlp2s0: authentication with <MAC 'MYWIRELESSNETWORK' [AC4]> timed out
[   77.003563] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   78.368797] wlp2s0: authenticate with <MAC 'MYWIRELESSNETWORK' [AC3]>
[   78.372285] wlp2s0: send auth to <MAC 'MYWIRELESSNETWORK' [AC3]> (try 1/3)
[   78.576068] wlp2s0: send auth to <MAC 'MYWIRELESSNETWORK' [AC3]> (try 2/3)
[   78.784057] wlp2s0: send auth to <MAC 'MYWIRELESSNETWORK' [AC3]> (try 3/3)
[   78.988079] wlp2s0: authentication with <MAC 'MYWIRELESSNETWORK' [AC3]> timed out
[   92.332714] wlp2s0: authenticate with <MAC 'MYWIRELESSNETWORK' [AC4]>
[   92.335889] wlp2s0: send auth to <MAC 'MYWIRELESSNETWORK' [AC4]> (try 1/3)
[   92.540061] wlp2s0: send auth to <MAC 'MYWIRELESSNETWORK' [AC4]> (try 2/3)
[   92.744088] wlp2s0: send auth to <MAC 'MYWIRELESSNETWORK' [AC4]> (try 3/3)
[   92.948063] wlp2s0: authentication with <MAC 'MYWIRELESSNETWORK' [AC4]> timed out
[  102.009932] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  105.357137] wlp2s0: authenticate with <MAC 'MYWIRELESSNETWORK' [AC4]>
[  105.360403] wlp2s0: send auth to <MAC 'MYWIRELESSNETWORK' [AC4]> (try 1/3)
[  105.564059] wlp2s0: send auth to <MAC 'MYWIRELESSNETWORK' [AC4]> (try 2/3)
[  105.768091] wlp2s0: send auth to <MAC 'MYWIRELESSNETWORK' [AC4]> (try 3/3)
[  105.972096] wlp2s0: authentication with <MAC 'MYWIRELESSNETWORK' [AC4]> timed out
[  116.061016] wlp2s0: authenticate with <MAC 'MYWIRELESSNETWORK' [AC3]>
[  116.069618] wlp2s0: send auth to <MAC 'MYWIRELESSNETWORK' [AC3]> (try 1/3)
[  116.272085] wlp2s0: send auth to <MAC 'MYWIRELESSNETWORK' [AC3]> (try 2/3)
[  116.476063] wlp2s0: send auth to <MAC 'MYWIRELESSNETWORK' [AC3]> (try 3/3)
[  116.680059] wlp2s0: authentication with <MAC 'MYWIRELESSNETWORK' [AC3]> timed out
[  127.023781] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  130.044829] wlp2s0: authenticate with <MAC 'MYWIRELESSNETWORK' [AC4]>
[  130.050288] wlp2s0: send auth to <MAC 'MYWIRELESSNETWORK' [AC4]> (try 1/3)
[  130.252059] wlp2s0: send auth to <MAC 'MYWIRELESSNETWORK' [AC4]> (try 2/3)
[  130.456061] wlp2s0: send auth to <MAC 'MYWIRELESSNETWORK' [AC4]> (try 3/3)
[  130.660066] wlp2s0: authentication with <MAC 'MYWIRELESSNETWORK' [AC4]> timed out
[  152.010893] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready

########## wireless info END ############

```

---

### Post by chili555 on 2017-03-19
> In Sony's... er... unique approach to hardware design, the Vaio doesn't come with an integral wireless antenna. Rather, it comes with an external one that plugs into the back of the unit. I'm wondering if that has anything to do with it, because I have installed Lubuntu on several Vaio laptops before (with an internal wifi antenna) without any problems.
I think that is exactly the problem because we see this:> Cell 04 - Address: <MAC 'MYWIRELESSNETWORK' [AC4]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    [COLOR="#FF0000"]Quality=29/70[/COLOR]  [COLOR="#FF0000"]Signal level=-81 dBm  [/COLOR]
                    Encryption key:on
                    ESSID:"MYWIRELESSNETWORK"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000012c00bea03c
                    Extra: Last beacon: 2284ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSKI am about 32 feet (~9.75 meters) from my router and it's in a closet. My scan reads:```
Cell 01 - Address: xx:2B:B0:DC:45:xx
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                   [COLOR="#FF0000"] Quality=59/70  [/COLOR][COLOR="#FF0000"]Signal level=-51 dBm  [/COLOR]
                    Encryption key:on
                    ESSID:"GBR5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
<snip>

```I suggest that you check the antenna. Perhaps it is either broken or not properly connected.

---

### Post by pns2 on 2017-04-02
It's really puzzling me, as when the unit ran under Windows, the connectivity was not poor.

Would a USB antenna help...? (I'll need to fine one with Linux drivers...)

---

### Post by chili555 on 2017-04-02
> when the unit ran under Windows, the connectivity was not poor.Recently? Yesterday or today? Or was it not poor before the connector worked loose?> Would a USB antenna help...? (I'll need to fine one with Linux drivers...)Probably, but you'd need to blacklist the driver for the internal device.

Several of us here use this; it works out of the box: [https://www.amazon.com/TP-Link-N150-Wireless-Adapter-TL-WN722N/dp/B002SZEOLG/](https://www.amazon.com/TP-Link-N150-Wireless-Adapter-TL-WN722N/dp/B002SZEOLG/)

---

### Post by pns2 on 2017-04-04
The connector hasn't worked loose... it has always... worked! :-) - and when the unit ran Windows, the connectivity was fine for at least 2 years. No change to the antenna was made between the unit running Windows and running Ubuntu.
Anyway, thanks for the tip with the TPLink antenna. Amazon reports that it has been replaced by the TL-WN822N, so I'll buy that and give it a go.

---

### Post by chili555 on 2017-04-04
>  Amazon reports that it has been replaced by the TL-WN822N, so I'll buy that and give it a go.That uses a different chipset that isn't natively supported in Ubuntu. I'd look around for the 722 if you can.

---

### Post by pns2 on 2017-04-18
Many thanks to everyone for your help in this thread. I bought the 722 from Amazon. The machine recognised it instantly as promised, so I'm back up and running again with wifi. Thanks all.

---

