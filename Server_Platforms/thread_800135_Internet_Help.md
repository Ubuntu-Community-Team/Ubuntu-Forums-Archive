---
title: "Internet Help"
date: 2008-05-19
forum: Server Platforms
---

### Post by hwang251 on 2008-05-19
I'm having a problem with connecting to the internet with Ubuntu Server.

I tried pinging it, but it just hangs there.

---

### Post by Oak37 on 2008-05-19
Is this a wired ethernet connection you have or a wireless connection? If it is a wired connection then have you properly configured your router/modem?

---

### Post by hwang251 on 2008-05-20
> **Oak37 said:**
> Is this a wired ethernet connection you have or a wireless connection? If it is a wired connection then have you properly configured your router/modem?

Its a wired connection, and we're connecting to a school's network

---

### Post by windependence on 2008-05-20
> **hwang251 said:**
> Its a wired connection, and we're connecting to a school's network

What did you try to ping?

-Tim

---

### Post by hwang251 on 2008-05-20
> **windependence said:**
> What did you try to ping?

-Tim

I tried pinging the school's website

---

### Post by windependence on 2008-05-20
> **hwang251 said:**
> I tried pinging the school's website

You will need to set up the DNS servers and the default gateway to get out to the internet. Is this machine configured via DHCP or does it have a static IP address?

-Tim

---

### Post by hwang251 on 2008-05-20
> **windependence said:**
> You will need to set up the DNS servers and the default gateway to get out to the internet. Is this machine configured via DHCP or does it have a static IP address?

-Tim

The machine is configured via DHCP, so what do I need to do to set up the DNA servers and the default gateway?

---

### Post by cdtech on 2008-05-20
sudo pico /etc/network/interfaces

# The loopback network interface
auto lo eth0
iface lo inet loopback

# The primary network interface
iface eth0 inet dhcp

Hope this helps.....

---

### Post by hwang251 on 2008-05-20
> **cdtech said:**
> sudo pico /etc/network/interfaces

# The loopback network interface
auto lo eth0
iface lo inet loopback

# The primary network interface
iface eth0 inet dhcp

Hope this helps.....

I did that but it still has no connection

---

