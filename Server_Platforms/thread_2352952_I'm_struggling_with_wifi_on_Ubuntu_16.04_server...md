---
title: "I'm struggling with wifi on Ubuntu 16.04 server.."
date: 2017-02-17
forum: Server Platforms
---

### Post by marco910 on 2017-02-17
Hi,
I'm struggling with wifi on Ubuntu 16.04.1 Server as wel.... :
this what I've been done till now:

```
cat /etc/network/interfaces :

source /etc/network/interfaces.d/*
auto lo
iface lo inet loopback

auto wlp5s0
iface wlp5s0 inet dhcp
wireless-essid "NetworkName"
wireless-mode managed
wpa-drivr wext
post-up wpa_supplicant -Dwext -iwlp5s0 -c /etc/wpa_supplicant.conf -B

cat /etc/wpa_supplicant.conf :

network={
  ssid="NetworkName"
  psk="PskCode"
  key_mgmt=WPA-EAP WPA-PSK
  proto=RSN WPA
  pairwise=CCMP TKIP
}

in /etc/network/if-pre-up.d/ iwconfig -> /etc/network/if-up.d/iwconfig
cat /etc/network/if-up.d/iwconfig :

#!/bin/sh
iwconfig wlp5s0 essid "NetworkName" mode managed

cat /etc/network/interfaces.d/wlp5s0 :
auto wlp5s0
iface wlp5s0 inet dhcp
wpa-ssid NetworkName
wpa-psk PskCode

```
Rebooting takes too long:
```
"A start job is running for Raise network interfaces ( / 5 min 1s)" !...... !!!

```
```
sudo ifup -v -wlp5s0
Parsing file /etc/network/interfaces.d/wlp5s0
ifup: interface wlp5s0 already configured
```
but pinging: ping 8.8.8.8 connect: Network is unreachable

Also doing:
```
sudo /etc/init.d/networking restart
[ok] Restarting networking (via systemctI): networking.service
png 8.8.8.8
connect: Network is unreachable


```
doing :
```
systemctl status networking.service
networking.service: Main process exited, code=exited, status=1/FAILURE
wlp5s0: CTRL-EVENT-DISCONNECTED 
Failed to start Raise network interfaces

```
doing:
```
journalctl -xe

ifup[4205]: Error for wireless request "Set ESSID" (8B1A)
                 SET failed on device wlp5s0 ; Operation already in progress
                 run-parts: /etc/network/if-pre-up.d/iwconfig exited with return code 250
systemd[1]:  /sbin/ifup: pre-up script failed
                  Failed to start Raise network interfaces
```

I ran the following script: [https://github.com/UbuntuForums/wireless-info](https://github.com/UbuntuForums/wireless-info) in order to gather the infos necessary for troubleshooting a wireless connection.Please find attached the resulting txt file
Looking forward to your kind help
Marco

---

### Post by howefield on 2017-02-17
Post moved to own thread and to the "*Server Platforms*" forum.

---

### Post by bearlake on 2017-02-17
Hi,

This is all I had to do to get my wireless to work on Ubuntu Server 16.04

install wpasupplicant

added the following info to /etc/network/interfaces

auto lo wlp20s0
iface wlp20s0 inet dhcp
wpa-ssid (name)
wpa-psk (password)

---

### Post by chili555 on 2017-02-17
> **marco910 said:**
> Hi,
I'm struggling with wifi on Ubuntu 16.04.1 Server as wel.... :
this what I've been done till now:

<snip>

Any suggestions?
Looking forward to your kind help
MarcoFirst, please confirm that your interface is indeed wlp5s0:```
iwconfig
```Next, please amend the /etc/network/interfaces file to:```
auto lo
iface lo inet loopback

auto wlp5s0
iface wlp5s0 inet dhcp
wpa-ssid NetworkName
wpa-psk <your_key_in_plain_text>
```We will change to a static IP a bit later. It is cumbersome to locate a server with an ever-changing IP address.

Now, restart the interface:```
sudo ifdown wlp5s0 && sudo ifup -v wlp5s0
```The -v for verbose should produce some clues as to what is going wrong, if any.

---

### Post by marco910 on 2017-02-17
Hi bearlake,
I've already added into /etc/network/interfaces these linese:

auto wlp5s0
iface wlp5s0 inet dhcp
wpa-ssid NetworkName
wpa-psk LongPskNumericalCode
and as I wrote above I still have "Failed to start Raise network interfaces" problems

---

### Post by bearlake on 2017-02-17
I needed to install wpasupplicant.

---

### Post by marco910 on 2017-02-18
"wpasupplicant already the newest version "... but still "Faised to start raise network interfaces"... any ideas about what to check?

---

### Post by howefield on 2017-02-18
Threads merged.

---

### Post by marco910 on 2017-02-18
Thank you howefield. They refer to exactly the same problem.

---

### Post by Habitual on 2017-02-18
Is this a Virtual host or a physical one?

---

### Post by marco910 on 2017-02-19
It is a physical host.
I ran the following script: [https://github.com/UbuntuForums/wireless-info](https://github.com/UbuntuForums/wireless-info) in order to gather the infos necessary for troubleshooting a wireless connection.Please find attached the resulting txt file
Looking forward to your hints.
Marco

---

### Post by marco910 on 2017-02-20
> **chili555 said:**
> First, please confirm that your interface is indeed wlp5s0:```
iwconfig
```Next, please amend the /etc/network/interfaces file to:```
auto lo
iface lo inet loopback

auto wlp5s0
iface wlp5s0 inet dhcp
wpa-ssid NetworkName
wpa-psk <your_key_in_plain_text>
```We will change to a static IP a bit later. It is cumbersome to locate a server with an ever-changing IP address.

Now, restart the interface:```
sudo ifdown wlp5s0 && sudo ifup -v wlp5s0
```The -v for verbose should produce some clues as to what is going wrong, if any.

Hi,
this is the output of :
sudo ifdown wlp5s0 && sudo ifup -v wlp5s0
ifdown: interface wlp5s0 not configured
Parsing file /etc/network/interfaces.d/wlp5s0
Configuring interface wlp5s0=wlp5s0 (inet)
/bin/run-parts --exit-on-error --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/ifenslave
+ [ inet = meta ]
+ IF_BOND_SLAVES=
+ [  ]
+ [  ]
+ [ -z  ]
+ exit
run-parts: executing /etc/network/if-pr-up.d/iwconfig
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlp5s0 ; Operation already in progress.
run-parts: /etc/network/if-pre-up.d/iwconfig exited with return code 250
Failed to bring up wlp4s0

---

### Post by marco910 on 2017-02-20
Hi,
iwconfig
lo               no wireless extensions
wlp5s0        IEEE 802.11bgn ESSID:"Vodafone-11111111"
                  Bit Rate=1 Mb/s Tx-Power=13 dBm
                  Retry short limit:7  RTS thr:off Fragmen thr:off
                  Power Management:off
                  Link Quality=47/70  Signal level = -63 dBm
                  Rx invalid nwid:0  Rx invalid crypt:0 Rx invalid frag:0
                  Tx excessive retries:0 Invalid misc:8 Missed beacon:0

sudo cat /etc/network /interfaces

source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback

auto enp3s0
iface enp3s0 inet static
address 192.168.1.3
pre-up /sbin/ethtool -s enp3s0 speed 1000 duplex full

allow-hotplug wlp5s0
iface wlp5s0 inet dhcp
wpa-ssid "Vodafone-11111111"
wpa-psk "Psk_in_plain_text"

sudo ifdown wlp5s0 && sudo ifup -v wlp5s0
ifdown: interface wlp5s0 not configured
Parsing file /etc/network/interfaces.d/wlp5s0
Configuring interface wlp5s0=wlp5s0 (inet)
/bin/run-parts --exit-on-error --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/ifenslave
+ [  inet = meta  ]
+ IF_BOND_SLAVES=
+ [  ]
+ [  ]
+ [ -z  ]
+ exit
run-parts: executing /etc/network/if-pre-up.d/iwconfi
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlp5s0 ; Operation already in progress.
run-parts: /etc/network/if-pre-up.d/iwconfig exited with return code 250
Failed to bring up wulp5s0

---

### Post by marco910 on 2017-02-20
[COLOR=#222222]Please let me know what ever I have to check in order to understand why WIFI doesn't work[FONT=arial]
[/FONT][/COLOR]

---

### Post by chili555 on 2017-02-20
This looks like you are connected:> wlp5s0 IEEE 802.11bgn ESSID:"Vodafone-11111111"
Bit Rate=1 Mb/s Tx-Power=13 dBm
Retry short limit:7 RTS thrff Fragmen thrff
Power Managementff
Link Quality=47/70 Signal level = -63 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:8 Missed beacon:0
But this looks like you are not:> Failed to bring up w[COLOR="#FF0000"]u[/COLOR]lp5s0Is there a typo here? In your file or just when you copied the results??

Your /etc/network/interfaces is badly malformed for enp3s0. First, it asks both ethernet *and *wireless to start automatically; auto enp3s0. Second, it declares a static IP address but no netmask, gateway nor dns-nameservers. For now, until we sort out the wireless, I suggest that you comment out the ethernet, thus:```
source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback

#auto enp3s0
#iface enp3s0 inet static
#address 192.168.1.3
#pre-up /sbin/ethtool -s enp3s0 speed 1000 duplex full

allow-hotplug wlp5s0
iface wlp5s0 inet dhcp
wpa-ssid "Vodafone-11111111"
wpa-psk "Psk_in_plain_text"
```Detach the ethernet cable, reboot and show us:```
iwconfig
dmesg | grep wlp
sudo ifdown wlp5s0 && sudo ifup -v wlp5s0
```

---

### Post by marco910 on 2017-02-22
Hi,
with this interface file now and with this wpa_supplicant.conf files, both ethernet and wifi connections work fine:

marco@PC:~$ sudo cat /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

auto enp3s0
iface enp3s0 inet dhcp
pre-up /sbin/ethtool -s enp3s0 speed 1000 duplex full

allow-hotplug wlp5s0
iface wlp5s0 inet dhcp
wpa-ssid "Vodafone-11111111"
wpa-psk "Psk_in_plain_text"

marco@PC:~$ sudo cat /etc/wpa_supplicant.conf
network={
        ssid="Vodafone-11111111"
        psk=very_long_numeric_code # obtained through wpa_passphrase "Vodafone-11111111" Psk_in_plain_text
        key_mgmt=WPA-EAP WPA-PSK
        proto=RSN WPA
        pairwise=CCMP TKIP
}

THANK YOU VERY MUCH for your kind help.
Marco

---

