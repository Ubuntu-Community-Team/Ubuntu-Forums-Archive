---
title: "Wireless Connectivity Issues with Ubuntu Studio 10.04"
date: 2012-01-19
forum: Ubuntu Studio
---

### Post by Wolfmage on 2012-01-19
I just installed Ubuntu Studio 10.04 about a week ago. I have been unable to figure out the wireless set up. It doesn't look anything like the wireless configuration tool I had on Hardy.

---

### Post by deonis on 2012-01-19
We will need a little more information on your wifi card ... lspci ?

---

### Post by jejeman on 2012-01-19
You need to manualy set connection in /etc/network/interfaces 
something like this
```
cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface wlan0 inet static
address 192.168.0.64
netmask 255.255.255.0
gateway 192.168.0.1
wpa-psk 8658b40b61fc45c45c19320779798364257d5d3185c1528fd4a62c5ce8d4b995
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-scan_ssid 1
wpa-ssid broadee

auto wlan0
```Depends on your network setup, and of course the wifi card needs to be suported by the kernel.

---

### Post by Wolfmage on 2012-01-19
[B][COLOR=Purple]This is the wifi card info:
Broadcom Corporation BCM4312 802.11b/g (rev 01)
Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)[/COLOR][/B]

---

### Post by deonis on 2012-01-19
did you try to install bcmwl source?

sudo apt-get install bcmwl-kernel-source

---

### Post by Wolfmage on 2012-01-19
**I tried the sudo apt-get command as suggested & still could not connect wirelessly. I then checked (hardware drivers) I noticed the Broadband Driver was not activated. When I attempted to activate it I got an error message that directed me to var/log/jockey which at the very end gave me this:**



[COLOR=Purple][B]2012-01-19 21:39:07,631 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-19 21:39:07,815 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-19 21:39:07,950 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-19 21:39:18,163 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-19 21:39:38,332 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-01-19 21:39:38,335 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-01-19 21:39:38,424 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted[/B][/COLOR]

---

### Post by Wolfmage on 2012-01-19
[COLOR=Purple][B]Update: I just threw Knoppix Live USB in my netbook, unplugged my wired internet cable, input my wireless network info & 'poof I was surfing the internet .

This eliminates the thought that something is wrong with the wifi card, & our wireless router.

I'd like to keep the Ubuntu Studio, but only if it can access the wireless internet.[/B][/COLOR]

---

### Post by jejeman on 2012-01-20
For Broadcom you need to install driver and firmware. 
Easyiest way to do it is if you have LAN internet access is to go thru jockey-gtk, which makes instalation automated.

---

### Post by BcRich on 2012-01-21
Hi Wolfmage
I don't know if this is of any help to you [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
I use a Netgear WNA1100 wifi dongle with Ubuntu Studio 10.10 I simply installed this driver [http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/) for it to work. I wouldn't recommend installing that driver (in your case) unless you can ascertain whether it will work with your card.

---

### Post by Wolfmage on 2012-01-26
Thank you to all who replied. I have simply decided to go with a different distro for now. I installed Linux Mint 12 Gnome and wireless is working great.

---

