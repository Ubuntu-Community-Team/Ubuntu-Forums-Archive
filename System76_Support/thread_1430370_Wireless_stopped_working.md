---
title: "Wireless stopped working"
date: 2010-03-15
forum: System76 Support
---

### Post by puddlejumper on 2010-03-15
I have just returned from a trip on which I took my laptop. The hotel I stayed at had wired network access only. I used this network with a cat-5 cable connection.

When I returned home, my wireless network connection was not working. I get the message "Firefox cannot find the server at www.google.com" when I bring up Firefox. I get the message "error while fetching mail" when I bring up Evolution.

I have desktop Ubuntu based systems which are working correctly.

Everything was working perfectly on the laptop before I left.

nm-tool output is:
NetworkManager Tool

State: connected

- Device: wlan0 [Auto linksys] ------------------------------------------------
Type: 802.11 WiFi
Driver: iwlagn
State: connected
Default: yes
HW Address: 00:246:59:6B:C2

Capabilities:
Speed: 54 Mb/s

Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes

Wireless Access Points (* = current AP)
*linksys: Infra, 00:23:699:65:BA, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA

IPv4 Settings:
Address: 192.168.1.102
Prefix: 24 (255.255.255.0)
Gateway: 192.168.1.1

DNS: 192.168.1.1


- Device: eth0 -----------------------------------------------------------------
Type: Wired
Driver: jme
State: unavailable
Default: no
HW Address: 00:90:F5:9A:CA:19

Capabilities:
Carrier Detect: yes
Speed: 10 Mb/s

Wired Properties
Carrier: off

Any help would be appreciated.

Thanks.

My laptop is a System 76 Bonobo system.
Bon-P3
Bluetooth
ATI Mobility Radeon HD 4570 Graphics with 513 MB GDDR2 Memory
250 GB Hard Drive 7200 RPM SATA II
2GB DDR3 1066 MHZ (1 DIMM)
9.10 Karmic Koala 64 bit Linux
i5-520M Processor
Wireless Intel wi-fi 5100 80211-a/g/n

linksys simultaneous dual-band wireless router

---

### Post by puddlejumper on 2010-03-15
I am now connected directly to the wireless router via a cat-5 cable and all is working well as a wired connection.  I don't know if this has any significance.

---

### Post by thomasaaron on 2010-03-15
Puddlejumper... Three things to try...

1. Right-click your network manager icon and make sure "Enable wireless networking" is enabled.

2. To fix your /etc/network/interfaces file, go to a terminal
(Application > Accessories > Terminal) and enter the following command:

sudo gedit /etc/network/interfaces

This will launch a text editor with the interfaces file opened in it.

In this file, put a comment (#) in front of EVERY line of the file
EXCEPT for these two lines:

auto lo
iface lo inet loopback

Click SAVE on the text editor and reboot your computer.


3. Restart your wireless router. Just unplug it. Let it sit for a minute. Plug it back in and let it initialize.


Did any of those fix the problem?

---

### Post by puddlejumper on 2010-03-15
The two lines that you said should remain un-commented are the only two lines in the /networking/interfaces file.

---

### Post by puddlejumper on 2010-03-15
I neglected to say:

Wireless networking is enabled.
I have restarted the router several times.

To an uneducated guy like me, this certainly has the appearance of a DNS problem.

---

### Post by puddlejumper on 2010-03-15
This was a router problem

---

### Post by puddlejumper on 2010-03-15
This was a router problem..

---

