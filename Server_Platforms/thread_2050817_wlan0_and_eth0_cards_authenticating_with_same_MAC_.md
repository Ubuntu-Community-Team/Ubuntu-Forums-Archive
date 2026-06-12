---
title: "wlan0 and eth0 cards authenticating with same MAC on router - Using WPA_SUPPLICANT"
date: 2012-08-31
forum: Server Platforms
---

### Post by vinaobraga on 2012-08-31
Hello Guys.

I'm trying to configure my wireless connection on my server but something weird is happening.
I have two cards on my server, one wired and another one wireless.
After set up all the setting of wpa_supplicant and execute the commands to connect, the wlan0 network get IP and connected on my AP.
But, when I log into my AP and ask to list all attached devices, I see the wlan0 card connected with the same MAC Address from the wired card. And if I unplug the network cabe from eth0, both connections goes down.

I will sent the steps that I followed with my configuration files to see if you can help me, please.

root@server:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:54:21:27:1f
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:54ff:fe21:271f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:517 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:106880 (106.8 KB)  TX bytes:80933 (80.9 KB)
          Interrupt:19 Base address:0x2c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1524 (1.5 KB)  TX bytes:1524 (1.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:06:4f:70:f8:c8
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::206:4fff:fe70:f8c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:19857 (19.8 KB)  TX bytes:21919 (21.9 KB)

root@server:~#

Follow the steps:

ifconfig wlan0 up
ifconfig
wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -B
ifconfig
ps aux | grep [w]pa
iwconfig wlan0
dhclient wlan0

root@server:~# cat /etc/wpa_supplicant/wpa_supplicant.conf
ctrl_interface=/var/run/wpa_supplicant
network={
        ssid="AP-NOVO"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        #psk="REMOVED"
        psk=REMOVED
}
root@server:~#

root@server:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

#wireless
auto wlan0
iface wlan0 inet dhcp


Follow the output of the attached devices from router:

3	192.168.1.9	SERVER	00:08:54:21:27:1F
4	192.168.1.10	SERVER	00:08:54:21:27:1F

if you can see, the MAC is the same of the eth0.

What is wrong? I want to use only the wireless card..is it possible, right?

I'm running ubutu 12.04.

Thanks in advanced by any help.

---

### Post by kennethconn on 2012-08-31
What router are you using? Firmware?

---

### Post by vinaobraga on 2012-09-01
Hi Kenneth.

follow the router data:

It's a NetGear

Hardware Version	WGR614V9
Firmware Version	V1.2.30_41.0.44

---

