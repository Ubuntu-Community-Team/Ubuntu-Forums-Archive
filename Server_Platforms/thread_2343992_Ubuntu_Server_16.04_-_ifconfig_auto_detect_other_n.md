---
title: "Ubuntu Server 16.04 - ifconfig auto detect other nics"
date: 2016-11-21
forum: Server Platforms
---

### Post by stan26 on 2016-11-21
Im trying to find the packages used in the gui that auto detects the other nic's and adds them to ifconfig without adding them to /etc/network/interfaces.
atm my ifconfig looks like this, using names only to keep it sweet
```

username@ubuntu:~$ ifconfig
enp6s0    Link encap:Ethernet  HWaddr d8:cb:8a:a4:26:6c 
lo        Link encap:Local Loopback

```But when using the **-a** switch i get
```
username@ubuntu:~$ ifconfig -a
enp3s0f0  Link encap:Ethernet  HWaddr 00:15:17:b1:9a:7d
enp3s0f1  Link encap:Ethernet  HWaddr 00:15:17:b1:9a:7c
enp4s0f0  Link encap:Ethernet  HWaddr 00:15:17:b1:9a:7f
enp4s0f1  Link encap:Ethernet  HWaddr 00:15:17:b1:9a:7e
enp6s0    Link encap:Ethernet  HWaddr d8:cb:8a:a4:26:6c 
lo        Link encap:Local Loopback
wlp5s0    Link encap:Ethernet  HWaddr 7c:5c:f8:d4:bc:d7

```

if anyone knows the core ubuntu gui network manager package and can help me add them to my non gui server so my remaining nics they are detected in ifconfig this will be great.

---

### Post by stan26 on 2016-11-22
```
sudo apt-get install network-manager
```

> [COLOR=#333333][FONT=Ubuntu]Network Manager aims for Network Connectivity which[ "Just Works".]("https://help.ubuntu.com/community/NetworkManager") [/FONT][/COLOR]

---

### Post by TheFu on 2016-11-22
According to the ifconfig manpage, the -a switch shows all network interfaces, including those that are not configured.  Without that switch, only interfaces that aren't "down" are displayed.  

If you want to use network-manager on a server, at least use the CLI version.  Think nmcli is the name.  I use wicd-curses myself, but only for wifi stuff. For other server networking things, edit the interfaces file manually referencing the manpage for detailed information on settings.  NICs in the interfaces file are ignored by nm, I understand. It is a conflict resolution thing they decided.

---

### Post by stan26 on 2016-11-22
Thanks fu for the update atm Im just after anything that will get this server up and running for the family.
I do have the wlp5s0/intel 7260 so i will have a look into command line versions but for now, Im just so happy that i have broken away from the gui after 8months off getting this pc and having to learn other os i tried back during GGibon but found it to difficult to understand ironic GG

---

### Post by slickymaster on 2016-11-22
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2016-11-22
I have a 7260 wifi card in my chromebook.  Works fine with wicd-curses.
```
       product: Wireless 7260
       vendor: Intel Corporation
```
For a server, I would never use wifi as the main connection. Servers really, really, really, need to be wired.  But after doing 1200+ wifi deployments, I use wired ethernet whenever possible.  Had to change some settings on the wifi-AP (40Mhz channels, N-only connections) to get N speeds (my AP is only 802.11n - 300Mbps capable) from 5 ft away in the same room, LOS.  Real throughput is 65-70Mbps tops according to iperf.  Using wired, I see 920Mbps.  Night and day difference.

Wifi throughput is one of the great lies in the world.  Powerline networking throughput is another. A 600Mbps system usually provides 45Mbps or so when deployed.  OTOH, wired ethernet is really pretty close to advertised and easy to achieve.  BTW, use **iwconfig** to manage wifi adapters, not ifconfig. Also check that **rfkill** isn't blocking the device.

Don't know what wlp5s0 is. Sorry.

**sudo lshw -C network** output would help.

---

