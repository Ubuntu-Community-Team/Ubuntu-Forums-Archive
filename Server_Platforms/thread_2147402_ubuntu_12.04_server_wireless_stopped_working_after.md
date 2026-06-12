---
title: "ubuntu 12.04 server: wireless stopped working after adding VNC"
date: 2013-05-21
forum: Server Platforms
---

### Post by alwayssummer on 2013-05-21
I had everything working fine for my PS3MS box, but I decided to add VNC desktop because I can't find decent documentation how to configure PS3MS without the GUI. Well, after the upgrade wireless doesn't work, which makes my media server pretty useless.

I was working on the guide for wpa_supplicant: [http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

But when it attempts to connect I just get a lot of 'Failed to initiate AP Scan: Operation not supported' errors. I'm in way over my head on this one, where do I begin untangling this mess?

EDIT:

Here's my logs from trying to start the interface.

```
ris@woja:/etc$ sudo wpa_supplicant -Dwext -ieth0 -c/etc/wpa_supplicant.conf
ioctl[SIOCSIWMODE]: Operation not supported
ioctl[SIOCGIWRANGE]: Operation not supported
ioctl[SIOCGIWMODE]: Operation not supported
ioctl[SIOCSIWAP]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODE]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODE]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODE]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODE]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODE]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODE]: Operation not supported
ioctl[SIOCSIWSCAN]: Operation not supported
Failed to initiate AP scan.
ioctl[SIOCSIWSCAN]: Operation not supported
Failed to initiate AP scan.
```

Sample wpa_supplicant.conf:
```
network={
    ssid="MyNetwork"
    #psk="Long p@ssword, with spaces\!"
    psk=89878ca9b4b54d39f3889cf690fbe34054e75dc056fe0e42e4e3d30bb0eab786
}
```
Note, there's no '\' in my password, I'm adding it in order to escape the '!' at the end of the password.

Sample interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto wlan0
iface wlan0 inet dhcp
        wireless-essid MyNetwork
        pre-up wpa_supplicant - Bw -Dwext -ieth0 -c/etc/wpa_supplicant.conf
        post-down killall -q wpa_supplicant
```

---

### Post by alwayssummer on 2013-05-24
No ideas?

---

### Post by steeldriver on 2013-05-24
You appear to be calling wpa_supplicant on eth0 - shouldn't that be wlan0? it is probably failing because the eth0 interface doesn't support wireless operations. You also appear to be mixing WPA and WEP interface fields - afaik [FONT=courier new]wireless-essid[/FONT] is for WEP only, for WPA you want [FONT=courier new]wpa-ssid[/FONT]. (Also [FONT=courier new]89878ca9b4b54d39f3889cf690fbe34054e75dc056fe0e42e4e3d30bb0eab786[/FONT] looks more like a WEP key than a WPA passphrase.)

I'm not sure why you are using wpa_supplicant directly via a pre-up anyway - it should be sufficient to do something like (obviously change the dns-nameservers field to something appropriate for your network):

```

auto wlan0
iface wlan0 inet dhcp
    wpa-ssid MyNetwork
    wpa-psk "Long p@ssword, with spaces\!"
dns-nameservers 192.168.1.1

```


I guess another possibility is that the addition of the VNC server pulled in network-manager as part of a desktop dependency and that is conflicting with your existing network config - you can check that with

```
service network-manager status
```

```
apt-cache policy network-manager
```

---

