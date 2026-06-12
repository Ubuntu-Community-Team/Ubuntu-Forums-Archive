---
title: "Ubuntu Server 16.04.3 not connecting to network withWifi"
date: 2017-09-18
forum: Server Platforms
---

### Post by su:bhatta on 2017-09-18
Hello All,

I am new to Ubuntu Server section.

I installed Ubuntu Server 16.04.3 today and during installation I was able to choose my Wifi Network and selected it as primary.
During installation there were no problems but on first log on I was unable to connect to internet.
I was getting error : Network-manager.service not found.

This is on a laptop and I had no LAN cable handy..

After going through a lot of material on internet I was able to resolve this issue by manually editing /etc/network/interfaces.

I had to put the below details :

```

auto lo iface lo inet loopback 

auto wlan0
iface wlan0 inet dhcp
address xxx.xxx.x.xxx
netmask xxx.xxx.xxx.x
gateway xxx.xxx.x.x
wpa-ssid XXXXXXX
wpa-psk XXXXXXX
dns-nameservers 8.8.8.8 192.168.1.1 
```

then I did :
```

sudo ifdown wlan0 && ifup -v wlan0  
dhclient -r 
/etc/init.d/networking restart 
```

only then I was able to connect to internet.

My issue is resolved and my questions is :
Is this how it is intended to be or was this a problem specific to me  since I did something wrong while installing.

Your inputs are appreciated

---

### Post by TheFu on 2017-09-19
The installer for a Server isn't the same as the the OS run by the server.  "Servers" don't use wifi, hence why no wifi setup is provided.
It has been this way since at least 14.04.

---

### Post by su:bhatta on 2017-09-27
> **TheFu said:**
> The installer for a Server isn't the same as the the OS run by the server.  "Servers" don't use wifi, hence why no wifi setup is provided.
It has been this way since at least 14.04.

Thanks The Fu

Its all cool then. got the point now. I am marking this as Solved , the documentation is scratchy in this regards.
My Server is set up for hosting [Moodle]("https://moodle.org/")  :)

---

