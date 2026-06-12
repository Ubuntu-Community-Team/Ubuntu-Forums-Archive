---
title: "Wifi problems"
date: 2015-04-27
forum: Server Platforms
---

### Post by scrufulufugu517 on 2015-04-27
I want to connect my server through wifi but i can't get it to connect to the internet. I have been able to ping my router which is a apple airport extreme everything else connected to my router works fine: so far I have added this to the file /etc/network/interfaces on my ubuntu server 
```

auto wlan0
iface wlan0 inet static
address 10.0.1.200
netmask 255.255.255.0
gateway 10.0.1.1
wpa-ssid <router>
wpa-psk <wpa_key>
dns-nameservers 8.8.8.8 10.0.1.1

```[FONT=Ubuntu][COLOR=#111111]

Please help[/COLOR][/FONT]

---

