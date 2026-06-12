---
title: "How can I configure Ubuntu server to connect to the network by wireless?"
date: 2011-05-21
forum: Server Platforms
---

### Post by KIAaze on 2011-05-21
Hi,

How can I configure Ubuntu server to connect to the network by wireless?

I tried setting up wireless in /etc/network/interfaces as follows:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
#auto lo
#iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

# wireless
#auto wlan0
#iface wlan0 inet dhcp
#wpa-ssid MYSSID
#wpa-ap-scan 1
#wpa-key-mgmt WPA-PSK
#wpa-psk MYPSK
 
# reading passphrase from stdin
#network={
#	ssid="MYSSID"
#	psk=MYPSK
#}


auto lo
iface lo inet loopback

#auto wlan0
#iface wlan0 inet dhcp
#wpa-conf /etc/wpa_supplicant.conf

#The wireless interface
auto wlan0
iface wlan0 inet dhcp
wpa-ssid MYSSID
wpa-ap-scan 1
wpa-key-mgmt WPA-PSK
wpa-psk MYPSK

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

It works for Ubuntu Desktop, but doesn't seem to work for Ubuntu Server.

I'm connecting using a "Belkin N Wireless USB network adapter":
```
$ lsusb 
Bus 001 Device 004: ID 050d:815f Belkin Components F5D8053 N Wireless USB 
```

I connected by cable when I installed Ubuntu Server, but now I want to use wireless.
The USB dongle works on Ubuntu Desktop and scanning for wireless networks on the server also works:
```
$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: C0:3F:0E:D6:12:96
                    ESSID:"MYSSID"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:rsn_ie
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7C0050F204104A00011010440001021041000100103B00010310470010FB2D14C50681BE15C4E2A3580BDFAA6C1021000D4E4554474541522C20496E632E10230009574E5232303030763210240009574E523230303076321042000230311054000800060050F204000110110009574E52323030307632100800020084
                    Signal level=62/100  

```

iwconfig keeps showing some rtl_wifi:
```
$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I also tried this: [http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/](http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/)
```

ifconfig wlan0 up
iwconfig wlan0 essid NETWORK_ID key s:WIRELESS_KEY

```
But the iwconfig doesn't change at all.

network restart messages:
```

$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
cat: /var/run/wpa_supplicant.wlan0.pid: No such file or directory
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
   ...done.
lockfile creation failed: exceeded maximum number of lock attempts

```

Any ideas how I can get wireless to work?

---

