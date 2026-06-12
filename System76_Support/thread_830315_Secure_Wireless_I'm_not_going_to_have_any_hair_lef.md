---
title: "Secure Wireless: I'm not going to have any hair left...."
date: 2008-06-15
forum: System76 Support
---

### Post by lightnb on 2008-06-15
I can get wireless to work if I setup my router (Linksys WRT54GS) unsecured. So the hardware works...

But with security- there's a billion settings on the router, and a billion settings on the laptop...

The router shows up with:
sudo iwlist scan:

```

wlan0     Scan completed :
          Cell 01 - Address: 00:12:17:C8:E5:A2
                    ESSID:"Balrog"
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=88/100  Signal level=-45 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000000002d3cb3d

```

The router is using "WPA-pre-shared key", "AES" algorithm. SSID broadcast is off, MAC Address filtering is off.

I can see the router, but no internet, etc. How do I troubleshoot this?

---

### Post by thomasaaron on 2008-06-16
If you've tinkered with a bunch of stuff and don't remember enough about it to get it all back to default settings, I would reset the router. It has a reset button on the back.

You may then need to go into the router and enable wireless.

Then, clean up your interfaces file using the following instructions:

> To fix your /etc/network/interfaces file, go to a terminal
(Application > Accessories > Terminal) and enter the following command:

sudo gedit /etc/network/interfaces

This will launch a text editor with the interfaces file opened in it.

In this file, put a comment (#) in front of EVERY line of the file
EXCEPT for these two lines:

auto lo
iface lo inet loopback

Click SAVE on the text editor and reboot your computer.
It should now boot faster and connect to networks more easily.

NOTE:
Unless you are dealing with static IP addresses (which is pretty rare for the
general end-user) you should NOT establish a network connection by going to
System > Administration > Network.

Instead, you should connect to the Internet using the Network Manager icon
in the upper right corner of your screen (the one that looks like a little
computer monitor).

Then, in your router, record your WEP or WPA key, left-click your Network Manager icon and select your access point.

You will be prompted for the security code. Make sure it is set up exactly like the router (i.e. WPA or WEP, 32-bit or 64-bit), and enter your passphrase.

---

### Post by lightnb on 2008-06-16
Hi Thomas,

I'm using KDE, so the built in wireless network tool that comes with Ubuntu isn't there...

There is a program called "Wireless Assistant" that allows me to find networks and connect to them, but it doesn't work unless your router broadcasts its ESSID-- which I have turned off.

So I found a tutorial that tells you to modify your "/etc/network/interfaces" file, so you can add your network manually, which is what I've tried doing. But it won't connect.

I think something in that file must be mis-configured?

My "/etc/network/interfaces file" File:
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto wlan0
iface wlan0 inet static
address 192.168.5.3
gateway 192.168.5.251
dns-nameservers 192.168.5.251
netmask 255.255.255.0
wpa-driver wext
wpa-ssid Balrog
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk ca354283ab9bf0952e5af1c8843aabc8177148599209bb6b8f4fd64fd42758ca
```

Router settings:
```

Security Mode: WPA Pre-Shared Key
WPA Algorithm: AES (TKIP is also an option)
WPA Shared Key: (some plain text words)
Group Key Renewal: 3600 seconds
SSID: Balrog
SSID Broadcast: Disabled

```

I'd like to leave SSID Broadcast Disabled, and use some sort of encryption. I could use WEP, but read that it's less secure, and slower than WPA.

I don't know the difference between TKIP and AES.

My computers use static IPs for port forwarding

---

### Post by thomasaaron on 2008-06-17
Ah, the dreaded Kubuntu!

We don't support it, and I've never messed with Wireless Assistant.
I'll do some googling on this issue and see what I can find, but I'm not really set up to try to recreate and solve Kubuntu issues.

---

### Post by kettyheloD on 2009-03-26
You can resert the router setting . :KSI think that it's ok.  [hair accessories](http://www.hairaccessoriesusa.com/)

---

### Post by Derath on 2009-03-27
You can install Network Manager and use it, I've been using it in KDE for a long time. You can also try installing wicd, either one will work. 

You can also try leaving it unsecured and in the router settings you can limit access by MAC address where only specified MAC addresses can connect to the router (not terribly secure, but does present as a nuisance to anyone trying to get in.

I know some that have ESSID not advertised, WEP protected and MAC address limited and haven't had any problems.

---

### Post by betrunkenaffe on 2009-03-28
I have the same router, use WPA2 (AES + TKIP), set the SSID to open and then connect to it wirelessly in the open. Once you have confirmed that you can connect, then work on with the SSID hidden.

Eliminate the problems so you know what you actually have to work on, it could be that the SSID being hidden is your problem, it could be the encryption (I'm using the above spec, would rather straight AES but ran into issues)

PS: I have WPA2, SSID hidden and no mac filtering (I just don't see need as it prevents me connecting additional machines)

---

