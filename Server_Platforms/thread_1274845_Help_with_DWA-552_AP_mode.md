---
title: "Help with DWA-552 AP mode"
date: 2009-09-25
forum: Server Platforms
---

### Post by Darksmac on 2009-09-25
Please help me i am trying to set my linux box as a router need to get wireless card into ap mode

heres all the info i have

**ifconfig wlan0

wlan0     Link encap:Ethernet  HWaddr 00:22:b0:bd:98:7f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**iwconfig wlan0

wlan0     IEEE 802.11bgn  ESSID:""SmappleServe""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**sudo lspci|grep Atheros

01:06.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)

**sudo lsmod|grep "ath"

ath9k                 310584  0 
mac80211              251528  1 ath9k
led_class              13064  1 ath9k


Ive already tried --

**sudo gedit /etc/modprobe.d/madwifi
     *addlines* options ath_pci autocreate=ap

**sudo ifconfig wlan0 up



any help please would be very helpful

---

### Post by Darksmac on 2009-09-26
any one ?!

---

