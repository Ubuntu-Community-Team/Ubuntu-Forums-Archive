---
title: "Strange packets in wireshark"
date: 2008-10-26
forum: Security
---

### Post by night_fox on 2008-10-26
My internets being really slow (800Kbps at best and its meant to be 20Mbps). I've phoned my ISP and they say they are fixing it and they've given me some money back. Its Virgin media.

This has prompted me at times of frustratingly low speeds to capture packets for a few minutes with wireshark over the wireless interface to see if any of my housemates are torrenting. I found mainly these packets, and most of them were definately coming from a friends PS3.

1) Bogus IP header something about length being smaller than something
2) Loads of IP fragments or it might have been TCP i can't remember even though in preferences I said to reassemble the fragments
These packets were either coming from or going to my friends PS3's network IP address.
3) More of these fragments, but the source and destination IP addresses were both internet IP addresses.

Is wireshark getting heinously confused or is someone somehow screwing about with our network? How could packets addressed to somewhere on the internet, from somewhere else on the internet end up behind my router where none of the IP addresses belong to my router?

---

### Post by nubdora on 2008-10-26
> **night_fox said:**
> My internets being really slow (800Kbps at best and its meant to be 20Mbps). I've phoned my ISP and they say they are fixing it and they've given me some money back. Its Virgin media.

This has prompted me at times of frustratingly low speeds to capture packets for a few minutes with wireshark over the wireless interface to see if any of my housemates are torrenting. I found mainly these packets, and most of them were definately coming from a friends PS3.

1) Bogus IP header something about length being smaller than something
2) Loads of IP fragments or it might have been TCP i can't remember even though in preferences I said to reassemble the fragments
These packets were either coming from or going to my friends PS3's network IP address.
3) More of these fragments, but the source and destination IP addresses were both internet IP addresses.

Is wireshark getting heinously confused or is someone somehow screwing about with our network? How could packets addressed to somewhere on the internet, from somewhere else on the internet end up behind my router where none of the IP addresses belong to my router?

Didn't happen to install TOR and configure your computer to be a relay?

---

### Post by night_fox on 2008-10-27
Nope I havent got TOR or set my computer up to be a relay. Good thinking though.

---

### Post by stmurray on 2008-10-27
Any traffic found on your wireless lan that has internet addresses for both the source and final destination shouldn't work as the traffic goes out your wireless router to the internet.  A good firewall-type router should stop them, since the source address isn't in the correct subnet (this is usually called egress filtering).  All traffic **from** the internet will be NATTED (that is the Internet address transformed to your internal address) so the traffic shouldn't be coming in through there.  

What are the Internet addresses?  Be careful they aren't 169.254.xx.xx, because that isn't a true Internet Address, but rather the address of a network card that couldn't find an IP address (RFC 3330).

What I would do is look at the traffic in WireShark, and see what the source and destination MAC (Ethernet) address are. One MAC should be your wireless router and the other another device on the network (MAC addresses are layer 2 and therefore only relevant at the LAN level).   If you see one for a device you don't know, you can look up the manufacturer of the NIC via the first half of the MAC address-- just Google for "MAC lookup", there are a ton of web sites that let you put in the first half of the MAC address and will return that manufacturer.  That may help you find out where the traffic is coming from. 

Also, make sure you have the best security your wireless Access Point can do, even if it is WEP (hopefully it can do better with WPA or WPA2, but WEP is better than nothing).

Good luck

---

### Post by The Cog on 2008-10-27
The one thing I would be fairly sure of is that wireshark isn't getting confused. As stmurray says, packets addressed from teh internet to the internet shouldn't be reaching your LAN. Look at theMAC addresses to see who is actually originating them.

---

### Post by night_fox on 2008-10-28
Cheers people. I'm probably going to show myself up now as being stupid as my wireless connection is entirely unencrypted. The only form of protection is mac filtering. IMHO it isnt much worse than WEP as anyone who knows what they are doing could crack either one very easily, anyway when I get round to it i'll use WPA2.

If someone connected they would have to be mac-spoofing. If someone used VPN to connect to my network, what would his IP address be? would it begin with 192.168 or would it be an internet ip address?

I'll post back if I see this again and this time save some more info. I think it might only happen when my friends PS3 is updating or he's playing an internet game.

---

### Post by osgood on 2008-10-29
I'm totally brand new to Linux.  Just installed Ubuntu on my laptop computer today.  I know this is a bit off-topic, but I was wondering how I could setup my wireshark "capture interfaces" so I can start captures and examine stuff.  I know how to use wireshark om n a PC as I've used it for a couple of months now, but I'm not too entirely sure on how to set it up on Linux.

Any help would be appreciated.

---

### Post by The Cog on 2008-10-29
An intruder using your network must necessarily use an IP address that lives within your network or it won't be able to communicate with anything - replies to the packets he sends wouldn't be sent back to him.

@osgood:
It would probably be better for you to start your own thread with a better title than to try and hijack someone else's thread. A title like "Capturing packets with wireshark" might be good. I am not aware of any differences between the Windows and Linux versions of Wireshark so I don't understand why you are having a problem. 

Oh, unless you are not running it as root. To capture packets, launch wireshark by pressing Alt-F2 and enter the command **gksudo wireshark**.

---

### Post by ratmandall on 2008-10-29
> **osgood said:**
> I'm totally brand new to Linux.  Just installed Ubuntu on my laptop computer today.  I know this is a bit off-topic, but I was wondering how I could setup my wireshark "capture interfaces" so I can start captures and examine stuff.  I know how to use wireshark om n a PC as I've used it for a couple of months now, but I'm not too entirely sure on how to set it up on Linux.

Any help would be appreciated.

Try
```
sudo wireshark
```
In the terminal, because normal user permissions can't capture on any of the devices for security reasons.

---

