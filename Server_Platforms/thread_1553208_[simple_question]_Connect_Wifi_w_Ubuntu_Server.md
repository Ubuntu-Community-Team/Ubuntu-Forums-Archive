---
title: "[simple question] Connect Wifi w/ Ubuntu Server"
date: 2010-08-14
forum: Server Platforms
---

### Post by golfromeo on 2010-08-14
I've been trying unsuccessfully to connect my Ubuntu 10.04 Server to wifi...

I have gotten to the point that when I type "sudo iwlist scan", under wlan0, I can see the Wifi network that I want to connect to. How do I connect to that network? Thanks for any help in advance.

NOTE: I've also gotten to the point where when I execute "sudo dhclient wlan0", I get a "No DHCPOFFERS received" error. Is there something I need to do to get a DHCP offer?

---

### Post by Joe of loath on 2010-08-14
Is the wifi network open, WEP or WPA?

---

### Post by golfromeo on 2010-08-14
It's open (I changed it temporarily to be without a password so I could see if I could connect at all)

When I run iwconfig, everything *seems* to be set right (for example, the ESSID is correct), but when I try to connect, I keep getting this "No DHCPOFFERS received" error.

---

### Post by golfromeo on 2010-08-14
also, running "sudo lshw -C network" returns my wireless interface correctly, and I can see the wireless network by doing iwlist scan. Yet somehow, I keep getting that DHCPOFFERS error.

---

