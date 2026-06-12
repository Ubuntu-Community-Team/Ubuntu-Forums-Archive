---
title: "Ubuntu Server 18.04 - Goodbye?"
date: 2018-05-03
forum: Server Platforms
---

### Post by erikoma on 2018-05-03
I was very surprised to find that with a clean install of 18.04, I couldn't find a way to do so without risking to destroy existing partitions. Is this no longer an option?
I can't understand that the disks are now identified by their brand name and size, and not by connection (dev/sda etc.). Who cares about that when the important factor is their placement/connection?
 
I have three different web/mail servers, all placed in a shed, and to manually operate one of them I need to carry it to the living-room or kitchen and set them up temporarily with a display and keyboard. Each server also has a partition with a desktop OS, making it more convenient for many tasks. I would strongly recommend that an installer with a graphical interface be made available so a system generation could be performed while doing other tasks. An installer, Ubiquity, exists, but AFAIK it's designed only to install a desktop system, and frankly, I never had any success with it.

The design of the installer has changed. It used to work just fine, so why change it? I had some trouble finding out how to operate it. There were some unnecessary questions, but - well - maybe some installations would need them.

I hoped that the installer would recognize a WiFi interface that I purchased because it was said to be Ubuntu compatible.
It did not, and though the LinuxMint desktop that I use found it with no trouble at all.
The reason I prefer WiFi is that the router doesn't have enough ports - and being fast enough it's not a bottleneck.

Like the unsuccessful Unity interface for the desktop version, it seems that Canonical is making experiments that are not well received by the community. Naturally, I stopped using the Ubuntu desktop, and if there's no better solution for the server edition, I'll seriously consider another OS for that also. CentOS, perhaps - widely used and having used it on external servers before, seems to fulfill at least my requirements just fine.

Any better solution in sight?

---

### Post by bluexmas on 2018-05-03
what iso did you used, "live" or "alternative" for server? I think you should give "alternative" a shot, it has the old installer and structure.

[http://cdimage.ubuntu.com/ubuntu/releases/18.04/release/](http://cdimage.ubuntu.com/ubuntu/releases/18.04/release/)

---

### Post by erikoma on 2018-05-03
> **bluexmas said:**
> what iso did you used, "live" or "alternative" for server? I think you should give "alternative" a shot, it has the old installer and structure.

[http://cdimage.ubuntu.com/ubuntu/releases/18.04/release/](http://cdimage.ubuntu.com/ubuntu/releases/18.04/release/)

I used the 64-bit PC (AMD64) server install image - And I'm a bit confused. There are sooo many choices, but I couldn't find the ones you mention.

BTW, if someone can help with the WiFi interface: My script NETCONFIG finds it (wlp3s0), but the ifupdown program is not found, and the card is not initialized.

---

### Post by LHammonds on 2018-05-03
The ISO image you download "by default" now is the "live" image which has it in the filename.  What you want is the "alternative" server ISO image which installs exactly like the 16.04 server image and does not use the Ubiquity desktop installer.

However, 18.04 no longer uses the same networking system 16.04 used.  They now use netplan.  So any network hardware that was Ubuntu-compatibile might be a different story with 18.04 but I don't know for sure.  It may only be just the initial setup and not related to driver capability.  I don't install to bare-metal so I don't run into the driver issues bare-metal installers do.

LHammonds

---

### Post by erikoma on 2018-05-03
OK, thanks. I understand the system better now, so I'm downloading this alternative version and will try it during the week-end.
I guess I'll have a challenge about the WiFi card, but if I can't make it work I can always use 1m of cable. :)

---

### Post by cruzer001 on 2018-05-03
Perhaps others will join in.

[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1768900](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1768900)

---

### Post by erikoma on 2018-05-03
Sure! Anyone with common sense is welcome! :)
About the "bug" report: I'm not in the habit of digging too deeply into details so some extra information is sometimes needed. It would be nice if the difference between the "live" and "alternative" versions were moved into the daylight.
I've been using Ubuntu since version 7, and during many years habits are formed. Many changes present new challenges, and sometimes frustrations that could/should have been avoided.

---

### Post by bluexmas on 2018-05-03
yeah, I fully agree about having a clear understanding of the differences between "live" and "alternative".

Out colleague LHammonds started a new topic here:

[https://ubuntuforums.org/showthread.php?t=2390785](https://ubuntuforums.org/showthread.php?t=2390785)

where we try to identify and document them.

---

### Post by Irihapeti on 2018-05-03
Incidentally, you can still use the existing networking method - ifupdown - in 18.04 server. See [https://netplan.io/faq#how-to-go-back-to-ifupdown](https://netplan.io/faq#how-to-go-back-to-ifupdown)

---

### Post by erikoma on 2018-05-07
Thanks to everyone for helping. The "Alternative" server was the solution.
To my delight the WiFi card worked after installation, but I'm not sure if it did before my start-up script was executed, which automatically produces the /etc/network/interfaces file:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary (WiFi) network interface
auto wlp2s1
iface wlp2s1 inet dhcp
# address 10.10.10.7

gateway 10.10.10.1
netmask 255.255.255.0
dns-nameservers 193.213.112.4 130.67.15.198

wpa-ssid XXXXXXXXXXX
wpa-psk YYYYYYYYYYYY

ifdown wlp2s1 && ifup -v wlp2s1

```
But the important thing is that it worked! :)

For anyone wondering how to find the card name, try
dmesg | grep wlan0
If you have a WiFi card the response should be something like this:
[    4.929011] iwlwifi 0000:03:00.0 wlp2s1: renamed from wlan0

---

### Post by erikoma on 2018-05-09
Some additional info:

For one of my computers, the installer didn't recognize the WiFi card at all. It was sold as "Ubuntu compatible".
I had to install the system using a cable connection.
After the installation I installed ifupdown and network-manager (don't know if that was necessary) and ran my NETCONFIG script. It produced the same /etc/network/interfaces as above, except it had changed the card name to "wlp3s0".

After this operation the computer takes a long time to boot it the cable is not connected, but after a minute or to it's up and running and connected to my LAN (which consists of 4-6 computers, mainly for backup and internet server). The long startup time is not a big problem because reboot is seldom needed. That's one of the beauties of Linux. I just wish the card was properly supported (netplan?). One of my older computers has a WiFi card from the same manufacturer, and it comes up with no special configuration when the system was installed using the same card.

This is my WiFi controller card.
Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter (rev 01)

Maybe someone can improve the procedure or support for this card?

(Sorry for a somewhat new subject)

---

### Post by sudodus on 2018-05-09
I think you have a better chance to get the attention of the network gurus, if you start a new thread with a good descriptive title (about your network issue). Good luck :-)

---

### Post by erikoma on 2018-05-09
I know. However for me it doesn't seem so important any more. I've finally made the alternative version of 18.04 work, and another thread to cover the subject might benefit someone else. However, all I wanted was comment on how it turned out for me. Selfish? Me? :)

---

