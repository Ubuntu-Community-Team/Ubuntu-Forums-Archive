---
title: "Can't update. Missing repositories on Ubuntu 23.04 LTS"
date: 2023-07-10
forum: Server Platforms
---

### Post by eian2 on 2023-07-10
I have installed Ubuntu 23.04 LTS edition on my Raspberrypi home server. Until recently I was able to install software however now I can't anymore. This is the first error indication I get when I run sudo apt update is: ```
Err:1 http://ports.ubuntu.com/ubuntu-ports lunar InRelease  Temporary failure resolving 'ports.ubuntu.com'
```
Doing a google search the suggested solutions would be adding the correct nameserver to /etc/resolve.conf  (a.i. my default gateway or DNS server, which did not solve the issue) and looking into the [FONT=var(--ff-mono)]/etc/apt/sources.list for bad repositories which I did not find. What I did find out was that the repositories that spewed the error messages did not exist in this file. Which are the one I mentioned above, [/FONT]lunar-updates InRelease, lunar-backports InRelease and lunar-security InRelease. How can this be and how can this be solved?

---

### Post by darkod on 2023-07-10
From that error it doesn't look like it is complaining on specific part of the repo (like lunar, inrelease, etc). It says it can't resolve ports.ubuntu.com so you need to look into using nameservers that you are sure work.

Using your home router is what people often do, but sometimes it can get stuck or not support too many dns queries. Better to use some public nameservers like google, 8.8.8.8, 8.8.4.4.

And test to see if you can resolve that url which you should be able to do with dig:
```
dig ports.ubuntu.com
```

---

### Post by eian2 on 2023-07-10
Thanks for your reaction. I think you are on to something with 'can't resolve ports.ubuntu.com'. I did a sudo ping ports.ubuntu.com and got: ```
ping: ports.ubuntu.com: Temporary failure in name resolution
``` And the outcome of dig ports.ubuntu.com: ```
; <<>> DiG 9.18.12-1ubuntu1.1-Ubuntu <<>> ports.ubuntu.com;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 107
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;ports.ubuntu.com.        IN    A


;; Query time: 0 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Mon Jul 10 07:33:25 CEST 2023
;; MSG SIZE  rcvd: 45



```
My default gateway should be 192.168.2.1 not 127.0.0.53.:confused:

Changed the nameserver in resolve.conf: ```
ejan@raspberrypi:~$ sudo cat /etc/resolve.conf
nameserver 8.8.8.8

```
However the error remains. Should I create a netplan configuration file perhaps?

---

### Post by eian2 on 2023-07-11
[SIZE=2][FONT=lucida console]So after a night of sleep I decided to redo some tests and my oh my I found out the nameserver in /etc/resolve.conf somehow magically changed to [COLOR=#000000]127.0.0.53. When I changed it back to 8.8.8.8 I was able to do an apt update but later on again the nameserver magically was changed to [/COLOR][COLOR=#000000]127.0.0.53 (whatever that may be). Someone please tell me what to do to make the nameserver in /etc/resolve.conf persistent.[/COLOR][/FONT][/SIZE]

---

### Post by darkod on 2023-07-12
It is normal 127.0.0.53 to show as nameserver in ubuntu. They changed that few versions ago. It is like internal part that communicates with the real nameserver. So don't worry that it shows like that.

But what you need to do is adjust your server network configuration to use 8.8.8.8 and 8.8.4.4 instead of the gateway.

PS. I forgot to add. Don't modify the resolv.conf, it gets overwritten. That is not how you control the dns nameservers in the recent versions of ubuntu. Do it in the network settings.

---

### Post by Skaperen on 2023-07-13
try [FONT=courier new]/etc/resolv.conf[/FONT] (remove the '[FONT=courier new]e[/FONT]').

---

### Post by guiverc on 2023-07-13
Please be aware that Ubuntu 23.04 is **not** a LTS or *long term support* release

An annoucement of the release can be found [here]("https://fridge.ubuntu.com/2023/04/20/ubuntu-23-04-lunar-lobster-released/") which states

> Maintenance updates will be provided for 9 months for all flavours releasing with 23.04.


thus if you hoped this was a LTS as your question refers to it, it's not.  Support (*especially security fixes etc*) will only occur until January 2024.

---

### Post by MAFoElffen on 2023-07-14
What does the netplan config file say? Is it static or dhcp? If DHCP, is dhcp client working?
```

mafoelffen@Mikes-ThinkPad-T520:~$ resolvectl query ports.ubuntu.com
ports.ubuntu.com: 2620:2d:4000:1::16           -- link: wlp3s0
                  2620:2d:4000:1::19           -- link: wlp3s0
                  185.125.190.39               -- link: wlp3s0
                  185.125.190.36               -- link: wlp3s0

-- Information acquired via protocol DNS in 105.9ms.
-- Data is authenticated: no; Data was acquired via local or encrypted transport: no
-- Data from: network

mafoelffen@Mikes-ThinkPad-T520:~$ sudo dhclient -v $(ip a | grep 'state UP' | awk '{print $2}' | sed 's/://g' )
Internet Systems Consortium DHCP Client 4.4.1
Copyright 2004-2018 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlp3s0/24:77:03:8a:42:38
Sending on   LPF/wlp3s0/24:77:03:8a:42:38
Sending on   Socket/fallback
DHCPDISCOVER on wlp3s0 to 255.255.255.255 port 67 interval 3 (xid=0xd9438976)
DHCPOFFER of 10.0.0.170 from 10.0.0.1
DHCPREQUEST for 10.0.0.170 on wlp3s0 to 255.255.255.255 port 67 (xid=0x768943d9)
DHCPACK of 10.0.0.170 from 10.0.0.1 (xid=0xd9438976)
RTNETLINK answers: File exists
bound to 10.0.0.170 -- renewal in 72975 seconds.

mafoelffen@Mikes-ThinkPad-T520:~$ grep -i 'dhcpack' /var/log/syslog | sort -r | grep . -m1
Jul 14 02:43:48 Mikes-ThinkPad-T520 dhclient[90072]: DHCPACK of 10.0.0.170 from 10.0.0.1 (xid=0xd9438976)

mafoelffen@Mikes-ThinkPad-T520:~$ grep -i 'dhclient' /var/log/syslog | sort -r | grep . -m1
Jul 14 02:43:48 Mikes-ThinkPad-T520 dhclient[90072]: Sending on   Socket/fallback

mafoelffen@Mikes-ThinkPad-T520:~$ grep "nameserver" /etc/resolv.conf
nameserver 127.0.0.53

```
Just saying...

---

