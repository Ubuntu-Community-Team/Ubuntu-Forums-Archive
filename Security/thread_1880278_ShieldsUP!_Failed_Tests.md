---
title: "ShieldsUP! Failed Tests"
date: 2011-11-13
forum: Security
---

### Post by fantab on 2011-11-13
While reading one of the Posts on this forum I came across [**ShieldsUP**]("https://www.grc.com/x/ne.dll?bh0bkyd2") and took all the tests. I am particularly concerned about two of them. Common Ports and All Service Ports. Here's what I find discomforting:

[LIST]
[*]COMMON PORTS: RECEIVED (FAILED)[/B]  &#8212; Your system REPLIED to our Ping (ICMP Echo) requests, making it  visible on the Internet. *Most personal firewalls can be configured to  block, drop, and ignore such ping requests in order to better hide  systems from hackers.* This is highly recommended since "Ping" is among  the oldest and most common methods used to locate systems prior to  further exploitation.[/LIST]

[LIST]
[*]ALL SERVICE PORTS: **Solicited TCP Packets: RECEIVED (FAILED)**  &#8212; As detailed in the port report below, one or more of your system's  ports actively responded to our deliberate attempts to establish a  connection. *It is generally possible to increase your system's security  by hiding it from the probes of potentially hostile hackers*. Please see  the details presented by the specific port links below, as well as the  various resources on this site, and in our extremely helpful and active user community.
[/LIST]

[LIST=1]
[*]**Port 623** - asf-rmcp ASF Remote Management and Control Protocol - IS OPEN. Can anyone tell me more about this port?
[*]"*Most personal firewalls can be configured to  block, drop, and ignore such ping requests in order to better hide  systems from hackers.*" HOW CAN I DO THIS?
[*]*It is generally possible to increase your system's security  by hiding it from the probes of potentially hostile hackers*. HOW CAN I ACHIEVE THIS?[/LIST]
Thanks...

---

### Post by Dangertux on 2011-11-13
> **fantab said:**
> [SIZE=2]While reading one of the Posts on this forum I came across [**ShieldsUP**]("https://www.grc.com/x/ne.dll?bh0bkyd2") and took all the tests. I am particularly concerned about two of them. Common Ports and All Service Ports. Here's what I find discomforting:

[/SIZE] 
[LIST]
[*][SIZE=2]COMMON PORTS:  [/SIZE][FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=2][COLOR=Black]**Ping Reply: [FONT=Arial]RECEIVED (FAILED)[/FONT]**  — Your system REPLIED to our Ping (ICMP Echo) requests, making it  visible on the Internet. *Most personal firewalls can be configured to  block, drop, and ignore such ping requests in order to better hide  systems from hackers.* This is highly recommended since "Ping" is among  the oldest and most common methods used to locate systems prior to  further exploitation.[/COLOR][/SIZE][/FONT]
[/LIST]

[LIST]
[*][FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=2][COLOR=Black]ALL SERVICE PORTS: [/COLOR][/SIZE][/FONT][FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=2][COLOR=Black]**Solicited TCP Packets: [FONT=Arial]RECEIVED (FAILED)[/FONT]**  — As detailed in the port report below, one or more of your system's  ports actively responded to our deliberate attempts to establish a  connection. *It is generally possible to increase your system's security  by hiding it from the probes of potentially hostile hackers*. Please see  the details presented by the specific port links below, as well as the  various resources on this site, and in our extremely helpful and active user community.[/COLOR][/SIZE][/FONT]
[/LIST]

[LIST=1]
[*][SIZE=2]**Port 623** - asf-rmcp ASF Remote Management and Control Protocol - IS OPEN. Can anyone tell me more about this port?[/SIZE]
[*][SIZE=2]"[/SIZE][FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=2][COLOR=Black]*Most personal firewalls can be configured to  block, drop, and ignore such ping requests in order to better hide  systems from hackers.*[/COLOR][/SIZE][/FONT][SIZE=2]" HOW CAN I DO THIS?[/SIZE]
[*][FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=2][COLOR=Black]*It is generally possible to increase your system's security  by hiding it from the probes of potentially hostile hackers*. HOW CAN I ACHIEVE THIS?[/COLOR][/SIZE][/FONT]
[/LIST]
[SIZE=2]
Thanks...[/SIZE]

First of all ShieldsUP! is generally speaking a terrible indicator of your system's overall level of security. In general an open port does not necessarily mean a system is easily compromised. I've seen systems with dozens of open ports that are nigh on to impossible to compromise, where as a singular desktop system with no open ports and an uneducated operator could be compromised in hours. Without getting into too much details on that subject as it isn't relavent lets understand what that report is saying about your system.

The first two bullets are essentially saying your system is responding to ICMP echo request (ping) with an ICMP echo reply (pong). The second bullet is saying that it is responding to TCP SYN on an open port (presumably 623)  with TCP ACK. This is normal behavior for a system and is not necessarily indicative of a weak security posture.

That being said, the port 623 is more concerning. I am assuming you are utilizing Network File Sharing (as that is generally what is associated with TCP 623). If you want to enhance your overall level of system security, and "improve" the results of that GRC scan. Then you might consider configuring your firewall.

*Note : you may have to allow some systems access to NFS if you are using it. You may also wish to verify that you are utilizing NFS and that it is not another service running on port 623 you may verify this by doing the following

```

sudo netstat -anlp | grep :623

```

If you are unsure of what the output means you may post it here.

If you are interested in learning to configure your firewall there is a fairly simple guide I wrote here : [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

I hope this helps

---

### Post by lswb on 2011-11-13
If you have a typical connection using a DSL modem or cable modem, the GRC site will actually report the port state of your modem/router, not your PC. It may well be necessary for your ISP to have ICMP (ping) working properly. Not sure about 623 but it is something that possibly can be configured in your modem/router setup. Again, it may be something that your ISP uses to talk to your modem.

---

### Post by fantab on 2011-11-13
> **Dangertux said:**
> First of all ShieldsUP! is generally speaking a terrible indicator of your system's overall level of security. In general an open port does not necessarily mean a system is easily compromised. I've seen systems with dozens of open ports that are nigh on to impossible to compromise, where as a singular desktop system with no open ports and an uneducated operator could be compromised in hours. Without getting into too much details on that subject as it isn't relavent lets understand what that report is saying about your system.

The first two bullets are essentially saying your system is responding to ICMP echo request (ping) with an ICMP echo reply (pong). The second bullet is saying that it is responding to TCP SYN on an open port (presumably 623)  with TCP ACK. This is normal behavior for a system and is not necessarily indicative of a weak security posture.

That being said, the port 623 is more concerning.** I am assuming you are utilizing Network File Sharing **(as that is generally what is associated with TCP 623). If you want to enhance your overall level of system security, and "improve" the results of that GRC scan. Then you might consider configuring your firewall.

*Note : you may have to allow some systems access to NFS if you are using it. You may also wish to verify that you are utilizing NFS and that it is not another service running on port 623 you may verify this by doing the following

```

sudo netstat -anlp | grep :623

```If you are unsure of what the output means you may post it here.

If you are interested in learning to configure your firewall there is a fairly simple guide I wrote here : [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

I hope this helps

No, I don't use Network File Sharing. Neither do I use Router, I just have an ethernet connection plugged into my desktop.

The above sudo command does not show any results. It does nothing.

---

### Post by Dangertux on 2011-11-13
> **fantab said:**
> No, I don't use Network File Sharing. Neither do I use Router, I just have an ethernet connection plugged into my desktop.

The above sudo command does not show any results. It does nothing.

This means that the service is not running on your machine. Which as stated above likely means that the scan is actually of your modem. 

If you would like to verify this you can install nmap

```

sudo apt-get install nmap

```

Then scan your modem's ip (probably 192.168.1.1 but it may be something else)

```

sudo nmap -T4 -v -A 192.168.1.1

```

It will likely indicate that port 623 is open on the modem, as well it will likely elaborate on what service the modem is running.

In any case I hope this has been helpful.

---

### Post by fantab on 2011-11-13
How do I find out my modem's ip? Is it same as my IP? My ISP has DHCP. 

When I run nmap as suggested above using **my IP**  - Result: all 1000 ports scanned are closed. So I guess my Desktop has does not have any open ports.

---

### Post by Dangertux on 2011-11-13
> **fantab said:**
> How do I find out my modem's ip? Is it same as my IP? My ISP has DHCP. 

When I run nmap as suggested above using **my IP**  - Result: all 1000 ports scanned are closed. So I guess my Desktop has does not have any open ports.

if you use the command

```

ifconfig

```You should get output that resembles this

```

wlan0     Link encap:Ethernet  HWaddr CC:AF:78:05:3B:F0  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ceaf:78ff:fe05:3bf0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40858 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23598 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54594130 (52.0 MiB)  TX bytes:3224861 (3.0 MiB)

```if you look at your ip address which is inet addr: 192.168.0.3 (in my case)

This will give you a hint as to your subnet. (The modem will also have an interface on this subnet)

If you do not know the exact router's ip you can nmap that whole subnet (if there is only the modem and your machine connected you should get two sets of results, one for your machine and one for your modem). The nmap command for that would be as follows

```

sudo nmap -T4 -v -A 192.168.0.0/24

```This assumes your ip address is 192.168.0.3 it would scan 192.168.0.0-192.168.0.255

If it was 192.168.1.5 you would do this

```

sudo nmap -T4 -v -A 192.168.1.0/24

```And this would scan 192.168.1.0-192.168.1.255 and so on, this should help you locate your modem's IP. Since it in theory could be anything on the same subnet as yours I can not tell you what it is. By default they are usually .1 or .100 , though this is not always the case.

Hope this helps.

Edit : It's important to understand that hunting for a singular open port on a modem (since your ISP may need that service running) is not really crucial to improving your security. You should really only bother if you're just curious in exploring your network's layout.

---

### Post by fantab on 2011-11-13
You have allayed my doubts quite adeptly. I am just being curious. I also read your brief guide. It very good to get one started. But as it is being argued on these forums, I should learn more about how Linux works first... and then hopefully, someday stop being a hobbyist.

I appreciate your help **Dangertux**, Thanks.

Edit: out of 255 nmap scans only my host is up everything else is down

---

### Post by Dangertux on 2011-11-13
> **fantab said:**
> You have allayed my doubts quite adeptly. I am just being curious. I also read your brief guide. It very good to get one started. But as it is being argued on these forums, I should learn more about how Linux works first... and then hopefully, someday stop being a hobbyist.

I appreciate your help **Dangertux**, Thanks.

Edit: out of 255 nmap scans only my host is up everything else is down

I'm glad it was helpful and if you have any questions feel free to continue asking. Security is a learning experience and an interesting journey. One that can be both enjoyable and frustrating just take it bit at a time :-)

---

