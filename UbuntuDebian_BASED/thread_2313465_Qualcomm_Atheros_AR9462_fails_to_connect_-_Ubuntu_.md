---
title: "Qualcomm Atheros AR9462 fails to connect - Ubuntu 14.04"
date: 2016-02-12
forum: Ubuntu/Debian BASED
---

### Post by sundjata on 2016-02-12
This may not be the right forum to post this question, but I can't find answers anywhere else on the Internet after extensive searching and I'm at my wit's end. I'm running elementary OS 0.3 Freya (64-bit, built on ubuntu 14.04) on an Acer C720 16GB Chromebook. I recently cp'd my entire /usr folder to a symlinked /usr on a 1tb external drive and borked all my permissions in the process. I repaired them by using rsync to reconstruct permissions from my backup folder, and now everything seems to work except my wifi, which fails to connect to visible WPA2 networks. Below is the output of running the wireless-info script:
```

########## wireless info START ##########

Report from: 12 Feb 2016 20:34 GMT +0000

Booted last: 12 Feb 2016 04:11 GMT +0000

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:	elementary OS
Description:	elementary OS Freya
Release:	0.3
Codename:	freya

##### kernel ############################

Linux 3.17.4-ickle #3 SMP Sat Nov 22 16:25:35 MST 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, tpm_tis.interrupts=0, vt.handoff=7

##### desktop ###########################

Pantheon

##### lspci #############################

01:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e058]
	Kernel driver in use: ath9k

##### lsusb #############################

Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 015: ID 054c:05ba Sony Corp. 
Bus 002 Device 011: ID 0489:e056 Foxconn / Hon Hai 
Bus 002 Device 003: ID 1bcf:2c67 Sunplus Innovation Technology Inc. 
Bus 002 Device 002: ID 0480:a200 Toshiba America Info. Systems, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

ath9k                 150702  0 
ath9k_common           25638  1 ath9k
ath9k_hw              454833  2 ath9k_common,ath9k
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              669964  1 ath9k
ath3k                  13331  0 
bluetooth             456055  23 bnep,ath3k,btusb,rfcomm
cfg80211              503543  4 ath,ath9k_common,ath9k,mac80211

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2456 (2.4 KB)  TX bytes:4515 (4.5 KB)

##### iwconfig ##########################

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

	NetworkManager

Running:

root      1388     1  0 04:11 ?        00:00:02 NetworkManager

##### NetworkManager info ###############

** (process:8403): WARNING **: Could not create object for /org/freedesktop/NetworkManager/Settings/75: uid 1001 has no permission to perform this operation

** (process:8403): WARNING **: handle_property_changed: failed to update property 'available-connections' of object type NMDeviceBt.

** (process:8403): WARNING **: error: cannot retrieve connection: uid 1001 has no permission to perform this operation

NetworkManager Tool

State: disconnected

- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no

  Capabilities:

- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no

  Capabilities:

- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no

  Capabilities:

- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no

  Capabilities:

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    AANKOMAH.NET:    Infra, <MAC 'AANKOMAH.NET' [AN1]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Hub Accra LTE]] (600 root)
[connection] id=Hub Accra LTE | type=802-11-wireless
[802-11-wireless] ssid=Hub Accra LTE | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Africa/Accra (based on set time zone)

country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
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
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

##### iwlist scan #######################

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Gateway' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"Gateway"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001c59507e1
                    Extra: Last beacon: 20ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.17.4-ickle/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     40EDC25D9BA894EB68105B1
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.17.4-ickle SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        8E:DE:3C:96:0C:F9:6D:D1:7B:AB:51:5C:93:4B:25:01:1D:52:55:47
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/3.17.4-ickle/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     64198F81A3D3DC3B5C957E6
depends:        cfg80211,ath9k_hw,ath
intree:         Y
vermagic:       3.17.4-ickle SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        8E:DE:3C:96:0C:F9:6D:D1:7B:AB:51:5C:93:4B:25:01:1D:52:55:47
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.17.4-ickle/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     96CAB8CC990EE7D448E7E9F
depends:        ath
intree:         Y
vermagic:       3.17.4-ickle SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        8E:DE:3C:96:0C:F9:6D:D1:7B:AB:51:5C:93:4B:25:01:1D:52:55:47
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.17.4-ickle/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     0AB7275A823E46D904ED4C7
depends:        cfg80211
intree:         Y
vermagic:       3.17.4-ickle SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        8E:DE:3C:96:0C:F9:6D:D1:7B:AB:51:5C:93:4B:25:01:1D:52:55:47
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.17.4-ickle/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B1AB7B2B112D48EA26CED76
depends:        cfg80211
intree:         Y
vermagic:       3.17.4-ickle SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        8E:DE:3C:96:0C:F9:6D:D1:7B:AB:51:5C:93:4B:25:01:1D:52:55:47
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[ath3k]
filename:       /lib/modules/3.17.4-ickle/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     9CB3FB381F873BAD63648E5
depends:        bluetooth
intree:         Y
vermagic:       3.17.4-ickle SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        8E:DE:3C:96:0C:F9:6D:D1:7B:AB:51:5C:93:4B:25:01:1D:52:55:47
sig_hashalgo:   sha512

[cfg80211]
filename:       /lib/modules/3.17.4-ickle/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A189C096E57D9F63A205933
depends:        
intree:         Y
vermagic:       3.17.4-ickle SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        8E:DE:3C:96:0C:F9:6D:D1:7B:AB:51:5C:93:4B:25:01:1D:52:55:47
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0
use_chanctx: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/snd-hda-intel.conf]
options snd-hda-intel model=,alc283-dac-wcaps

[/etc/modprobe.d/xboxdrv.conf]
blacklist xpad

##### rc.local ##########################

chgrp plugdev /sys/class/backlight/intel_backlight/brightness
chmod g+w /sys/class/backlight/intel_backlight/brightness

exit 0

##### pm-utils ##########################

[/etc/pm/sleep.d/00_screen] (755 root)
getXuser() {
        export user=`pinky -fw | awk '{ if ($2 == ":'$displaynum'" || $(NF) == ":'$displaynum'" ) { print $1; exit; } }'`
}
for x in /tmp/.X11-unix/*; do
    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
    getXuser;
    case "$1" in
	thaw|resume)
	    getXuser;
	    sudo -u $user env DISPLAY=":$displaynum" /usr/bin/xrandr --auto
            ;;
	*)
            ;;
    esac
done
exit 0

[/etc/pm/sleep.d/99wifi] (755 root)
case "${1}" in
        hibernate)
		/sbin/rmmod ath9k
                ;;
	resume|thaw)
                /sbin/modprobe ath9k
		;;
esac
exit 0

[/etc/pm/sleep.d/99zcyapa] (755 root)
getXuser() {
        user=`pinky -fw | awk '{ if ($2 == ":'$displaynum'" || $(NF) == ":'$displaynum'" ) { print $1; exit; } }'`
        if [ x"$user" = x"" ]; then
                startx=`pgrep -n startx`
                if [ x"$startx" != x"" ]; then
                        user=`ps -o user --no-headers $startx`
                fi
        fi
        if [ x"$user" != x"" ]; then
                userhome=`getent passwd $user | cut -d: -f6`
                export XSESSIONRC=$userhome/.xsessionrc
        else
                export XSESSIONRC=""
        fi
}
case "${1}" in
    hibernate)
	/sbin/rmmod cyapa
        ;;
    resume|thaw)
        COUNTER=0
        while [  $COUNTER -lt 10 ]; do
            date >>/tmp/99_cyapa
            /sbin/modprobe cyapa
	    sleep 1
	    dmesg | grep cyapa | tail -1 | grep "\(error\|fail\)" >/dev/null
	    RES=$?
	    if [ ${RES} -ne 1 ] ; then
		/sbin/rmmod cyapa
		sleep 1
	    else
		#done
		COUNTER=11
	    fi
	    
            COUNTER=`expr $COUNTER + 1`
        done
        ;;
     *)
        ;;
esac
exit 0

[/etc/pm/sleep.d/xboxdrv] (755 root)
case $1 in
     suspend|suspend_hybrid|hibernate)
	stop -q xboxdrv || :
        ;;
     resume|thaw)
	start -q xboxdrv || :
        ;;
esac

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x168c:0x0034 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[12270.631939] wlan0: authenticate with <MAC 'Gateway' [AC1]>
[12270.646535] wlan0: send auth to <MAC 'Gateway' [AC1]> (try 1/3)
[12270.674706] wlan0: authenticated
[12270.674920] ath9k 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[12270.674926] ath9k 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[12270.675534] wlan0: associate with <MAC 'Gateway' [AC1]> (try 1/3)
[12270.677956] wlan0: RX AssocResp from <MAC 'Gateway' [AC1]> (capab=0x411 status=0 aid=5)
[12270.678044] wlan0: associated
[12283.928545] wlan0: deauthenticating from <MAC 'Gateway' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############
 
```

---

### Post by howefield on 2016-02-12
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by sundjata on 2016-02-12
Thanks howefield. Will make note of the appropriate forum for future posts.

---

