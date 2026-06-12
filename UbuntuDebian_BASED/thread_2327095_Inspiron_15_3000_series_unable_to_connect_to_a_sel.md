---
title: "Inspiron 15 3000 series unable to connect to a self made RPi-Jessie router"
date: 2016-06-07
forum: Ubuntu/Debian BASED
---

### Post by AntoineCompagnie on 2016-06-07
Hi there! I just finished to create my own router with a RPi thanks to [http://raspberrypihq.com/how-to-turn-a-raspberry-pi-into-a-wifi-router/](http://raspberrypihq.com/how-to-turn-a-raspberry-pi-into-a-wifi-router/)

Yet, If I'm able to connect to the access point, I'm not able to connect to the Internet.

I followed the instructions on [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) and here are the results of the the wireless info script:

```
:~ $ sudo cat /home/pi/wireless-info.txt

########## wireless info START ##########

Report from: 07 Jun 2016 21:44 CEST +0200

Booted last: 01 Jan 1970 01:00 CET +0100

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

Distributor ID:    Raspbian
Description:    Raspbian GNU/Linux 8.0 (jessie)
Release:    8.0
Codename:    jessie

##### kernel ############################

Linux 4.4.9-v7+ #884 SMP Fri May 6 17:28:59 BST 2016 armv7l unknown unknown GNU/Linux

dma.dmachans=0x7f35, bcm2708_fb.fbwidth=656, bcm2708_fb.fbheight=416, bcm2709.boardrev=0xa01041, bcm2709.serial=0x23c7c566, smsc95xx.macaddr=<MAC 'eth0' [IF1]>, bcm2708_fb.fbswap=1, bcm2709.uart_clock=3000000, bcm2709.disk_led_gpio=47, bcm2709.disk_led_active_low=0, vc_mem.mem_base=0x3dc00000, vc_mem.mem_size=0x3f000000, dwc_otg.lpm_enable=0, console=ttyAMA0,115200, console=tty1, rootfstype=ext4, elevator=deadline, fsck.repair=yes, rootwait

##### desktop ###########################

sed: can't read /home/pi/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

./wireless-info: line 179: lspci: command not found

##### lsusb #############################

Bus 001 Device 006: ID 046d:c312 Logitech, Inc. DeLuxe 250 Keyboard
Bus 001 Device 005: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 004: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter
Bus 001 Device 003: ID 0424:ec00 Standard Microsystems Corp. SMSC9512/9514 Fast Ethernet Adapter
Bus 001 Device 002: ID 0424:9514 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

./wireless-info: line 192: rfkill: command not found

##### lsmod #############################

cfg80211              427855  0 
rfkill                 16037  3 cfg80211,bluetooth

##### interfaces ########################

source-directory /etc/network/interfaces.d

auto lo

iface lo inet loopback
iface eth0 inet dhcp

allow-hotplug wlan0

iface wlan0 inet static
    address 192.168.10.1
    netmask 255.255.255.0

up iptables-restore < /etc/iptables.ipv4.nat

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.0.33  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::c0f2:6df7:e27f:78c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76586 errors:0 dropped:4 overruns:0 frame:0
          TX packets:41865 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:110458999 (105.3 MiB)  TX bytes:3619806 (3.4 MiB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.10.1  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::cc03:14b4:9a3a:c2b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:694 errors:0 dropped:3 overruns:0 frame:0
          TX packets:470 errors:0 dropped:30 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:90884 (88.7 KiB)  TX bytes:78201 (76.3 KiB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Dumbledore"  Nickname:"<WIFI@REALTEK>"
          Mode:Master  Frequency:2.412 GHz  Access Point: <MAC 'wlan0' [IF2]>   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=2/100  Signal level=2/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.254   0.0.0.0         UG    202    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     303    0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     202    0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 wlan0

##### resolv.conf #######################

nameserver 192.168.0.254

##### network managers ##################

Installed:

    None found.

Running:

    None found.

##### NetworkManager info ###############

NetworkManager is not installed (package "network-manager").

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory

##### NetworkManager.conf ###############

grep: /etc/NetworkManager/NetworkManager.conf: No such file or directory

##### NetworkManager profiles ###########

No NetworkManager profiles found.

##### iw reg get ########################

Region: Europe/Brussels (based on set time zone)

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

lo        no frequency information.

eth0      no frequency information.

wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.457 GHz (Channel 10)
      5   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Copain' [AC1]>
                    ESSID:"Copain"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Quality=48/100  Signal level=48/100  
          Cell 02 - Address: <MAC 'FreeWifi' [AC2]>
                    ESSID:"FreeWifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:144 Mb/s
                    Quality=48/100  Signal level=69/100  
          Cell 03 - Address: <MAC 'FreeWifi_secure' [AC3]>
                    ESSID:"FreeWifi_secure"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac010c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    Quality=48/100  Signal level=61/100  
          Cell 04 - Address: <MAC 'SoloNet-C3:88' [AC4]>
                    ESSID:"SoloNet-C3:88"
                    Protocol:IEEE 802.11bgn
                    Mode:Ad-Hoc
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:off
                    Bit Rates:72 Mb/s
                    Quality=48/100  Signal level=46/100  
          Cell 05 - Address: <MAC '' [AC5]>
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=20/100  Signal level=10/100  
          Cell 06 - Address: <MAC 'patate' [AC6]>
                    ESSID:"patate"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=97/100  Signal level=10/100  

##### module infos ######################

libkmod: ERROR ../libkmod/libkmod.c:557 kmod_search_moddep: could not open moddep file '/lib/modules/4.4.9-v7+/modules.dep.bin'
modinfo: ERROR: Module alias cfg80211 not found.
[cfg80211]

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

i2c-dev

##### modprobe options ##################

[/etc/modprobe.d/ipv6.conf]
alias net-pf-10 off

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

##### rc.local ##########################

_IP=$(hostname -I) || true
if [ "$_IP" ]; then
  printf "My IP address is %s\n" "$_IP"
fi

sudo ifplugd eth0 --kill
sudo ifup lan0

exit 0

##### pm-utils ##########################

[/etc/pm/sleep.d/74ifplugd] (755 root)
[ -f /etc/default/ifplugd ] || exit 0
. /etc/default/ifplugd
[ "$SUSPEND_ACTION" ] || [ "$SUSPEND_ACTION" != "none" ] || exit 0
if [ "$SUSPEND_ACTION" = "suspend" ] ; then
  RESUME_ACTION="resume"
elif [ "$SUSPEND_ACTION" = "stop" ] ; then
  RESUME_ACTION="start"
else
  exit 0
fi
[ -f "${PM_FUNCTIONS}" ] && . "${PM_FUNCTIONS}"
IFPLUGD_STATE="ifplugd_ifs"
elem_of() {
    local E=$1
    shift
    echo $@ | grep -Eq "(\\<all\\>)|(\\<${E}\\>)" 
}
save_state() {
    savestate ${IFPLUGD_STATE} 2>/dev/null
}
load_state() {
    restorestate ${IFPLUGD_STATE} 2>/dev/null
}
filter_hotplug_ifs() {
    while read L; do
        for IF in $L; do
            # interface is managed statically
            elem_of "${IF}" "${INTERFACES}" && continue
            # interface is not managed by udev
            elem_of "${IF}" "${HOTPLUG_INTERFACES}" || continue
            # ignore lo
            [ "x${IF}" = "xlo" ] && continue
            echo -n "${IF} "
        done 
    done
    echo ""
}
get_running_ifs() {
    ps --no-headers -o args -C ifplugd | \
    sed -e 's/.*-[[:alpha:]]*i[[:space:]]*\([^[:space:]]\+\).*/\1/' | \
    filter_hotplug_ifs
}
get_hotplug_ifs() {
    local IFACES=""
    for IF in /sys/class/net/*; do
        echo "${IF##*/} "
    done | filter_hotplug_ifs
}
stop_udev_ifs() {
    local ACTION=$1
    local IFACES
    local IF
    IFACES=`get_running_ifs`
    # save list of interfaces we stop, so we can restart them
    echo "${IFACES}" | save_state || true
    for IF in ${IFACES}; do
        if [ "x${ACTION}" = "xsuspend" ]; then
            ifplugd -i ${IF} -S
        else
            ifplugd -i ${IF} -k
        fi
        # ifplugd started by udev doesn't take down the IF
        /etc/ifplugd/ifplugd.action ${IF} down
    done
}
start_udev_ifs() {
    local ACTION=$1
    local IFACES
    local IF
    # try to load list of interfaces
    # if it can't be loaded, we just start all hotplug interfaces
    IFACES=`load_state || get_hotplug_ifs`
    for IF in ${IFACES}; do
        if [ "x${ACTION}" = "xresume" ] && ifplugd -i ${IF} -c; then
            ifplugd -i ${IF} -R
        else
            # start ifplugd just as udev would
            INTERFACE=${IF} ACTION=add /lib/udev/ifplugd.agent
        fi
    done
}
case "$1" in
        hibernate|suspend|suspend_hybrid)
                /etc/init.d/ifplugd ${SUSPEND_ACTION}
                stop_udev_ifs ${SUSPEND_ACTION}
                ;;
        thaw|resume)
                if [ "x$2" != "xstandby" ]; then
                    start_udev_ifs ${RESUME_ACTION}
                    /etc/init.d/ifplugd ${RESUME_ACTION}
                fi
                ;;
        *) exit 1
                ;;
esac
exit 0

##### udev rules ########################

##### dmesg #############################

[    8.586659] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    9.926089] smsc95xx 1-1.1:1.0 eth0: hardware isn't capable of remote wakeup
[    9.926633] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.205215] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   11.714357] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   11.716151] smsc95xx 1-1.1:1.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1

########## wireless info END ############
```

---

### Post by jeremy31 on 2016-06-07
Does the Inspiron 15 3000 have Ubuntu installed on it?

---

### Post by AntoineCompagnie on 2016-06-08
Yes! ```
:~$ cat /proc/version
Linux version 3.19.0-59-generic (buildd@lgw01-39) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #66~14.04.1-Ubuntu SMP Fri May 13 17:27:10 UTC 2016
```

---

### Post by howefield on 2016-06-08
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

