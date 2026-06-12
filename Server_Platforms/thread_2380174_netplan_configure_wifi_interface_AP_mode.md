---
title: "netplan configure wifi interface AP mode?"
date: 2017-12-14
forum: Server Platforms
---

### Post by bern1 on 2017-12-14
Hi, 
I would like to configure atheros wifi mpcie card interface to work in AP mode. 
I use Ubuntu server 17.10 and networkd (do not use Network Manager).
I'm trying to configure wifi interface using netplan configuration files (each for interface)
I want to set static address for wifi interface so I prepared **/etc/netplan/03-netcfg.yaml** file::
```
network:
  version: 2
  renderer: networkd
   wifis:
    wlp4s0:
      addresses:
       - 192.168.1.2/24
      dhcp4: no
```
However this brakes other interface settings. So after that I don't have any interface....
See my network settings.
Before generating report below I changed 'wifis' to 'ethernets' for wlp4s0 to enable to start other interfaces. 
[http://paste.ubuntu.com/26177281/](http://paste.ubuntu.com/26177281/)

How to configure the wireless network interface to work in AP mode in newest Ubuntu 17.10?

[Documentation of netplan]("http://people.canonical.com/~mtrudel/netplan/") is not clear to me if netplan support networkd or only NetworkManager in respect to wifi.
Can I use 'old' method editing **/etc/network/interfaces **for wifi interface only and stay with netplan for other ethernet interfaces? 
Or maybe install NetworkManager and select it as network renderer for wifi only?
Please advice, 
TIA

---

### Post by bern1 on 2017-12-17
Alhough this is wifi interface I set 'ethernets' in the netplan file:
```
network:
  version: 2
  renderer: networkd
  ethernets:
    wlp4s0:
      addresses:
       - 192.168.1.1/24
      dhcp4: no
```
and wifi wlp4s0 interface receive static address 192.168.1.1 and works OK.

---

