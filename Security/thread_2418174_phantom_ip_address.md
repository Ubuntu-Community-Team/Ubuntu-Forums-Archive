---
title: "phantom ip address"
date: 2019-05-02
forum: Security
---

### Post by jps984 on 2019-05-02
I have ubuntu 18.04.2 LTS
ATT modem

I have recently installed UFW.  When I check the UFW log it shows attempted loging from IP address from my local network, however when I check my router there are no devices assigned with this ip address.  
Here is an example: 
```
May  2 18:22:42 LeFlyingFish kernel: [ 7623.523363] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:e0:22:04:24:b6:1f:08:00 SRC=192.168.1.86 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  2 18:22:56 LeFlyingFish kernel: [ 7637.245197] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:e0:22:04:24:b6:15:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
```
192.168.1.254 appears to be the locat address of my router DST I understand to be my laptop with Ubuntu.  The other IP I can't figure out.


I am not sure what to make of it?  Is this normal or an indication of a problem.  How could I investigate further?  
If I have posted this in the wrong forum it is because I don't know where else I could post it.  Let me know if there is a better place to post.
Any help is appreciated.

jp

---

### Post by Rubi1200 on 2019-05-03
Hi and welcome to the forums :-)

This should answer the question:
[https://en.wikipedia.org/wiki/Mcast.net](https://en.wikipedia.org/wiki/Mcast.net)

---

### Post by jps984 on 2019-05-03
Hello and thank you for your answer.
From this link I see that 224.0.0.1 is a way to reach all devices on my network.
What I still would like to understand is why this phantom IP address: 192.168.1.86, is trying to reach my devices on my LAN, and where does it come from, who is it?  This address, 192.168.1.86 has not been assigned by my router to any device.  That is puzzling, where is it coming from?

---

### Post by Rubi1200 on 2019-05-03
If you have a Linksys router then those are the IP ranges for a private network:
[https://whatismyipaddress.com/private-ip](https://whatismyipaddress.com/private-ip)

Scroll down to the section starting "What's a Private IP address?" and read on from there.

Hope this helps.

---

### Post by SeijiSensei on 2019-05-03
Can you ping that address from Ubuntu?  Does it appear if you run "arp -a"?

---

### Post by The Cog on 2019-05-03
> **SeijiSensei said:**
> Can you ping that address from Ubuntu?  Does it appear if you run "arp -a"?
With recent Ubuntus, arp is not installed by default. Use "ip neighbour" instead. Do this just after trying to ping 192.168.1.86, and you should see whether the IP address has been resolved to a MAC address. If it has then the device is there whether you can ping or or not.

---

### Post by jps984 on 2019-05-03
Thank you all for the answers.

The Cog and SeijiSensei:

Yes, I can ping that address, and it shows up when typing ip neighbour.  Here are the results:
192.168.1.254 dev wlp3s0 lladdr e0:22:04:24:b6:15 REACHABLE
192.168.1.66 dev wlp3s0 lladdr a0:c9:a0:c6:b8:57 STALE
192.168.1.86 dev wlp3s0 lladdr e0:22:04:24:b6:1f STALE
2600:1700:8170:1500::1 dev wlp3s0 lladdr e0:22:04:24:b6:15 router STALE

fe80::e222:4ff:fe24:b615 dev wlp3s0 lladdr e0:22:04:24:b6:15 router REACHABLE

192.168.1.254 is my router
192.168.1.66 is my Samsung phone
192.168.1.86 does not show up on my router as a device.

How could I investigate further?

Thanks,
jp

---

### Post by jps984 on 2019-05-03
Here is something interesting.  While looking at various logs and pages on my router I found this: 
[LIST]
[*]ipv4 2 tcp 6 86413 ESTABLISHED src=192.168.1.86 dst=52.88.37.87 sport=35136 dport=5222 packets=5727 bytes=548600 src=52.88.37.87 dst=76.218.49.164 sport=5222 dport=35136 packets=4292 bytes=589825 [ASSURED] use=2
[*]What is interesting is that the same phantom ip, 192.169.1.86, established a connection with 52.88.37.87 which when looked up belongs to amazon.  and then back from the src 52.88.37.87 back to my routers' external ip address 76.218.49.164.
[*]I totally don't know what to make of it.  Is there some kind of amazon thing on my browser trying to communicate with Amazon and my UFW firewall is preventing it from coming back?
[/LIST]

---

### Post by rbmorse on 2019-05-03
Maybe that's the Amazon applet that gets installed by default?

---

### Post by Skaperen on 2019-05-04
52.88.37.87 is an IP address in the pool of addresses that Amazon Web Services might assign to a running instance in their EC2 cloud service in region us-west-2 (Oregon).  only Amazon can reveal what AWS customer this is and they probably won't do that w/o a criminal investigation and/or court order.  if it was me, i'd block that one IP for now, if i could not figure out what it is doing.

---

### Post by TheFu on 2019-05-04
Do you have any IoT devices?  Wifi IoT devices might power off their wifi to save power.

An amazon tv stick or regular TV with internet, TV OTA tuners, a Bluray player?  Perhaps a tablet?
IoT devices typically broadcast they are on the network using a few different protocols to make other devices have an easier time.  ZeroConf is one of those, commonly implemented in the Avahi tool installed by default on all Ubuntu desktops.

If you want to hunt down all the devices on your network, you can install nmap and perform a scan.
sudo nmap -sT 192.168.1.1/24 | tee /tmp/ip-log
On my network, this will show the devices, Roku, Routers, QEMU virtual NIC (about 20 of these), Raspberry Pi Foundation, Silicondust Engineering, Dell, Buffalo.inc, ... you get the idea.  My amazon tablet didn't get seen during the scan, but it wasn't actively being used.  Battery management must have disabled the networking.

---

### Post by Doug S on 2019-05-04
> **jps984 said:**
> 192.168.1.254 dev wlp3s0 lladdr e0:22:04:24:b6:1[COLOR="#FF0000"]5[/COLOR] REACHABLE
192.168.1.86 dev wlp3s0 lladdr e0:22:04:24:b6:1[COLOR="#FF0000"]f[/COLOR] STALE

192.168.1.254 is my router
192.168.1.86 does not show up on my router as a device.
Observation: The MAC addresses only differ in the least significant nibble and do not resolve on "MAC to manufacturer" lookup web sites.
Suggestion (evidence to weak to say "Conclusion"): The device is somehow related to the router.

---

### Post by jps984 on 2019-05-04
Thank you all for the help.

I did a bit of research and while I am not 100 certain,  this IP address appears to be related to a function of the ATT modem. See answer to the same issue I had from another ATT customer:
[IMG]https://forums.att.com/html/rank_icons/rank_admin_14x13.png[/IMG] [**ATTCares**]("https://forums.att.com/t5/user/viewprofilepage/user-id/60")
Administrator


[RIGHT][[COLOR=transparent]Post options menu[/COLOR]]("https://forums.att.com/t5/AT-T-Internet-Equipment/1-mysterious-local-IP-addresses-for-5268AC-Gateway/td-p/5489124#")




[COLOR=#747474]May 3, 2018 7:47 AM[/COLOR]

[/RIGHT]

[COLOR=#3E3E3E][h=2][SIZE=2]Re: Re: 1 mysterious local IP addresses for 5268AC Gateway
[/SIZE][SIZE=1]
[/SIZE][SIZE=2]
[/SIZE]
[/h]

[/COLOR]

[COLOR=#3E3E3E][FONT=Lato][SIZE=2]Hello again,[/SIZE][/FONT][/COLOR]
[COLOR=#3E3E3E][FONT=Lato][SIZE=2]Thank you for the fast response and information![/SIZE][/FONT][/COLOR]
[COLOR=#3E3E3E][FONT=Lato][SIZE=2]Thank you for your patience as I look into this for you. After further research, we do believe the IP is associated with our gateway and protocols to make it work with our AirTies device.[/SIZE][/FONT][/COLOR]
[COLOR=#3E3E3E][FONT=Lato][SIZE=2]Have a wonderful day![/SIZE][/FONT][/COLOR]
[COLOR=#3E3E3E][FONT=Lato][SIZE=2]Katie, AT&T Community Specialist[/SIZE][/FONT][/COLOR]

---

### Post by jps984 on 2019-05-04
Doug S, you are correct.  According to ATT it is part of their Air Ties program.
Very good deduction on your part.
Thanks
jp

---

### Post by anissajodi13 on 2019-05-14
why not use this tool to track who he is [https://ipdetectives.io](https://ipdetectives.io) or what country he lives.[COLOR=#000000][FONT=Calibri][/FONT][/COLOR]

---

