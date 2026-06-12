---
title: "Ubuntu Server 12.10 - minidlna randomly not visible by devices"
date: 2013-03-19
forum: Server Platforms
---

### Post by stando007 on 2013-03-19
Hi,

I have ubuntu server 12.10. This server is used as a home router, wifi ap, NAS share, torrent downloader, webserver, upnp (dlna) server. As a dlna server I used Mediatomb in the past but then I decided to use minidlna because it was much easier to setup it to support all my devices (I had issue with Samsung TV - did not display subtitles and I had to patch the Mediatomb, etc...)
Minidlna worked "out of the box". I was able to play various kind of video files, music, browsing pictures.
I use these devices:
On wifi: android phone, android tablet
On cable lan: Samsung TV, Onkyo TX-8050 amplifier
From time to time some of the devices did not see the minidlna server. Sometimes restart of the minidlna service helped, sometimes not. Sometimes all devices did not see the minidlna server. I was struggling with this issue for some very long time without success. I found out that using minidlna on my desktop pc with Ubuntu 12.10 is not causing problems and minidlna ran on desktop was always visible.
The only difference between my server and desktop is that server has 2 wired networks interfaces (LAN, WAN) and one wireless network interface (LAN). I have bridged LAN + Wifi LAN interface together on the server. My minidlna is listening on the br0 bridged network adapter which is bridging lan interfaces - eth0+wlan0 and has local ip address assigned. In the minidlna.conf this is specified by:
```
network_interface=br0
```
I was lucky I found the information that bridges have defaultly enabled multicas snooping (information [here]("http://vivrelife.blogspot.sk/2013/01/Disabling-multicast-snooping-in-linux-bridge.html")). So disabling multicast snooping for my bridge resolved the situation. Now no more random "not availability" of minidlna server :)

In my config, I have br0 bridge and disabling the multicast snooping was done by putting this line into /etc/rc.local:
```
echo 0 >> /sys/devices/virtual/net/br0/bridge/multicast_snooping
```

I decided to write this on the forum because it can save a lot of time to somebody with the similar problem. Comments are welcome, too.

Plus I would like to mention about logging of the minidlna. I wanted to have verbose logging enabled, so I set the parameter in the /etc/minidlna.conf
```
log_level=debug
```
But this does nothing :) And this is defaultly in the conf file, but with warn instead of debug and commented
You have to specify the verbosity for particular "module" like this example:
```
log_level=general,artwork,database,inotify,scanner,metadata,http,ssdp,tivo=debug
```
Then you have really verbose log which can help sometimes. :)

---

### Post by Antoniya001 on 2013-07-04
Thanks a lot...  After upgrading my 12.04 server to 13.04 minidlna just wouldn't play nice. This seemed to have solved it. THX.

---

### Post by andre-peters on 2014-01-24
Hi,

yesterday I built a personal network setup with a bridged interface and run into this problem. At first I thought it was related to my minidlna version, because I use a git snapshot. 
When you trace br0, you can even see minidlna multicasting.

Another ugly fix is the br_device.c patch here:
[https://forums.gentoo.org/viewtopic-t-925816-start-0.html](https://forums.gentoo.org/viewtopic-t-925816-start-0.html)

Thank you very much for your thread/help! :)

---

### Post by outlyer on 2014-02-10
Wow THANK YOU!
I always had the problem of my devices not seeing the server until it announced itself and had assumed it was some bug in minidlna since no solution seemed to work... Until now :)

---

### Post by outlyer on 2014-02-10
Damn, double post :/

---

