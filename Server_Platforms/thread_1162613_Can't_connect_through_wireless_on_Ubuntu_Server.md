---
title: "Can't connect through wireless on Ubuntu Server"
date: 2009-05-17
forum: Server Platforms
---

### Post by Buce on 2009-05-17
I've just installed Ubuntu Server (8.04) for the first time, and would like to connect wirelessly so that I don't have to lug the thing over to my router and plug it in with the teeny-tiny ethernet cable I have. I've got a Ralink wifi card using the rt61pci driver, and I'm trying to connect to a Linksys WRT160N router.

I went through [this]("http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html") troubleshooting guide to get the thing to work, but whenever I try any of the iwlist commands, I get something like:
```
user@computer:~$ sudo iwpriv wlan0 set AuthMode=WPAPSK
wlan0     no private ioctls.
```

If I ignore the messages and keep on chugging, the server shows up on my router -- or at least, the static ip address that I gave it during the install shows up, but the host name of the computer doesn't where it normally would ("Bender", the hostname of my other computer, shows up alongside my ip on the router's DHCP client table).

But even though the router seems to recognize it, pinging google doesn't work, and pinging the router gives me:
```
user@computer:~$ ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.17: icmp_seq=1 Destination Host Unreachable
From 192.168.1.17: icmp_seq=2 Destination Host Unreachable
From 192.168.1.17: icmp_seq=3 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2007ms
, pipe 3
```

I'm at a loss as to what to do. Ideas?

---

### Post by ugm6hr on 2009-05-18
I used a RaLink USB device and found I had to use the serialmonkey drivers to et it to work on Hardy.

Might be worth a try.

There is a very thorough How-to here: [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)
WPA details here: [http://ubuntuforums.org/showthread.php?p=5670568#post5670568](http://ubuntuforums.org/showthread.php?p=5670568#post5670568)

Of course, the rt73 needs to be replaced with rt61: [http://linuxkc.wordpress.com/2008/03/10/howto-install-serialmonkey-drivers-for-ralink-rt61-wireless-card/](http://linuxkc.wordpress.com/2008/03/10/howto-install-serialmonkey-drivers-for-ralink-rt61-wireless-card/)

kevdog's Tutorial on manually connecting might also be useful, just check the Tutorials section.

---

