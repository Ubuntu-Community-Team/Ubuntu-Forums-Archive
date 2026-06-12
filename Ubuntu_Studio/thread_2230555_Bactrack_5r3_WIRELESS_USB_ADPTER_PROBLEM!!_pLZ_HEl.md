---
title: "Bactrack 5r3 WIRELESS USB ADPTER PROBLEM!! pLZ HElp!! ;("
date: 2014-06-19
forum: Ubuntu Studio
---

### Post by ayan3 on 2014-06-19
root@bt:~# lsusb
Bus 002 Device 006: ID 0e0f:0008 VMware, Inc. 
Bus 002 Device 005: ID 0e0f:0007 VMware, Inc. 
Bus 002 Device 004: ID 0e0f:000a VMware, Inc. 
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

==================================================

wlan0     Link encap:Ethernet  HWaddr 00:1a:ef:41:f7:ff  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

===================================================
root@bt:~# iwconfig
lo        no wireless extensions.

wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Auto  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

====================================================

airmon-ng


Interface    Chipset        Driver

====================================================

root@bt:~# ifconfig start wlan0
wlan0: Unknown host
ifconfig: `--help' gives usage information.

====================================================

HELP! plzzzzzzzzzzzzz
HELP! plzzzzzzzzzzzzz
HELP! plzzzzzzzzzzzzz
HELP! plzzzzzzzzzzzzz
HELP! plzzzzzzzzzzzzz
HELP! plzzzzzzzzzzzzz
HELP! plzzzzzzzzzzzzz
HELP! plzzzzzzzzzzzzz

---

### Post by lisati on 2014-06-19
Please do not start multiple threads for the same problem, it dilutes the community's ability to help.

Duplicate of [http://ubuntuforums.org/showthread.php?t=2230557](http://ubuntuforums.org/showthread.php?t=2230557) closed.

---

