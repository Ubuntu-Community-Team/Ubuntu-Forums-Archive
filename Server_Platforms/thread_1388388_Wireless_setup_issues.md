---
title: "Wireless setup issues"
date: 2010-01-23
forum: Server Platforms
---

### Post by cs3gallery on 2010-01-23
For some strange reason I have tried to get this sucker to work but it just doesnt want too. So I am here to ask you pros what you think the issue may be. I have had 9.04 running on this server before and had it all up and working and everything fine... I then decided to mess around and install a different operating system on it to test some things out.. now when I went back to linux by re installing it... it does the weirdest thing... After I configure everything in the /etc/network/interfaces I type in iwconfig to see if I am connected... sure enough it shows I am properly connected to my wifi that is WPA Using TKIP and the wext driver. However it shows there is no information being transferred.. and sure enough when I try and apt it wont let me do anything... Let me get both my iwlist and interfaces to show you how I have it setup.. I dunno... maybe I am doing something wrong.

First step I did was sudo vim /etc/network/interfaces to create this.

```
auto lo
iface lo inet loopback

auto ra0
iface ra0 inet static
address <my ip>
gateway <my gateway addy>	
dns-nameservers <I have 2 if them.. does it matter which I use?>
netmask 255.255.255.248 <this is the same as my subnet right?>
wpa-driver wext
wpa-ssid <level3>
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <my_hex_key>
```

Now I go back and type in sudo /etc/init.d/networking restart

afterwards I type in iwconfig and get this information.

```
lo     no wireless extensions

eth0   no wireless extensions

ra0    RT2860 Wireless ESSID:"level3"
       Mode:Auto Frequency=2.412 GHz
       Link Quality=100/100 Signal level:87 dBm Noise level:-143 dBm
       Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
       Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```



Anyone here have any ideas....???? I know I can get it going using a gui... but I dont want one as it takes resources I want. Anyways any help would be appreciated!!!  :D

---

