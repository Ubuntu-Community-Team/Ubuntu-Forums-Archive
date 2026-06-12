---
title: "Assistance with multiple IP networking"
date: 2012-12-29
forum: Server Platforms
---

### Post by AliasXNeo on 2012-12-29
Greetings,

I'm a relatively new server owner and am having trouble wrapping my head around using multiple IP addresses. I have recently purchased a dedicated server running Ubuntu server 12.10 and part of the package was 4 additional IPv4 addresses. My goal is to use the server for hosting a game server or two along with a website. Right now I'm just trying to host a Minecraft server on one IP and setup Apache on another IP. 

Can anyone point me in the right direction here? Any help is greatly appreciated, thanks!

---

### Post by darkod on 2012-12-29
Do you also have more than one network adapter to use or you have to use only one?

I don't have much experience with multiple IPs on single adapter, but I don't see much point from it. The Minecraft and Web services will work on different ports in any case, the the max transfer will be limited by the max speed of the adapter. Having one or more IPs on it can't help much in my view.

If you do have multiple adapters too, it's a different story. In that case you can use two or more adapters, each with different IP, and that makes sense because the transfer is done at the same time on both and the bandwith is higher.

---

### Post by AliasXNeo on 2012-12-29
> **darkod said:**
> Do you also have more than one network adapter to use or you have to use only one?

I don't have much experience with multiple IPs on single adapter, but I don't see much point from it. The Minecraft and Web services will work on different ports in any case, the the max transfer will be limited by the max speed of the adapter. Having one or more IPs on it can't help much in my view.

If you do have multiple adapters too, it's a different story. In that case you can use two or more adapters, each with different IP, and that makes sense because the transfer is done at the same time on both and the bandwith is higher.

I'm not sure how to tell how many adapters I have. If ifconfig only shows eth0 and a local loopback does that mean there's only one adapter?

---

### Post by sandyd on 2012-12-29
> **AliasXNeo said:**
> I'm not sure how to tell how many adapters I have. If ifconfig only shows eth0 and a local loopback does that mean there's only one adapter?

yes

---

### Post by volkswagner on 2012-12-29
With only one adapter the major benefit would be reverse dns entry's for dedicated servers.  This will allow each unique ip to have a valid ssl cert without any hacks.

I think you'll likely be handeling the multiple ip's with DNS entries, perhaps unique domain names?  Keep them in your pocket for future needs :)

---

### Post by sandyd on 2012-12-29
> **AliasXNeo said:**
> Greetings,

I'm a relatively new server owner and am having trouble wrapping my head around using multiple IP addresses. I have recently purchased a dedicated server running Ubuntu server 12.10 and part of the package was 4 additional IPv4 addresses. My goal is to use the server for hosting a game server or two along with a website. Right now I'm just trying to host a Minecraft server on one IP and setup Apache on another IP. 

Can anyone point me in the right direction here? Any help is greatly appreciated, thanks!
Generally, I restrict ssh to a single IP, and enable ssh keys and each service (i.e. mail server, TF2 server, .etc .etc) to its own port.

You also probably want to keep one ip unused as a backup, incase your server gets DDOSed or something.

---

### Post by sandyd on 2012-12-29
Generally, I restrict ssh to a single IP, and enable ssh keys and each service (i.e. mail server, TF2 server, .etc .etc) to its own port only for organizational/branding purposes (reverse IP). The only reason I would probably (I actually have a bad habit of running one service on one ip address, and I have 30 -odd ip addresses now...) really recommend seperate IP Addresses is when running things like gameservers and/or sites that are viable to attack.

When under attack, ISPs/providers generally blackhole the ip address, and if that single ip contains your mail server, your web server, and your game server, they all go down. If you have your mail server, web server and game server all on different IP addresses, blackholing one IP Address will only take that service offline.

---

### Post by AliasXNeo on 2012-12-29
> **sandyd said:**
> Generally, I restrict ssh to a single IP, and enable ssh keys and each service (i.e. mail server, TF2 server, .etc .etc) to its own port only for organizational/branding purposes (reverse IP). The only reason I would probably (I actually have a bad habit of running one service on one ip address, and I have 30 -odd ip addresses now...) really recommend seperate IP Addresses is when running things like gameservers and/or sites that are viable to attack.

When under attack, ISPs/providers generally blackhole the ip address, and if that single ip contains your mail server, your web server, and your game server, they all go down. If you have your mail server, web server and game server all on different IP addresses, blackholing one IP Address will only take that service offline.

Good advice, thanks! So if I wanted to separate the Minecraft server instance from everything else, how would I set that up?

---

### Post by spynappels on 2012-12-30
When you run ```
ifconfig
``` is the IP address one from a private subnet (192.168.x.x, 172.16.x.x, 10.x.x.x)? If not, you might be able to use virtual or logical IPs so eth0:1 is IP1, eth0:2 is IP2, etc.

---

### Post by SeijiSensei on 2013-01-01
You can assign the other addresses to the single network adapter using "[aliasing]("http://www.penguintutor.com/linux/networking-ip-alias-tutorial")."  For instance, if the primary IP address is 10.10.10.10, you could have the server listen on 10.10.10.11 as well by adding:

```
ifconfig eth0:0 10.10.10.11
```

to the file /etc/rc.local.  Then upon reboot your machine will appear to have two Ethernet adapters with separate addresses.

I have used aliasing to create multiple SSL-enabled web sites on a single machine using one IP for each domain or virtual host.  It also comes in handy when you want to assign a public IP address that forwards to a service behind the organization's firewall.  

A client got blacklisted by Barracuda the other day because an infected workstation behind the firewall became a spambot.  Luckily the admins fixed the problem and got de-listed, but if the blacklist managers dragged their feet, I was planning on swapping my client's blacklisted address with another one in the subnet we manage and assigning the blacklisted address to a virtual Ethernet adapter to ensure that nothing breaks.  I'd have to make a couple of changes to the iptables ruleset as well, of course.

---

### Post by volkswagner on 2013-01-01
> **SeijiSensei said:**
> You can assign the other addresses to the single network adapter using "[aliasing]("http://www.penguintutor.com/linux/networking-ip-alias-tutorial")."  For instance, if the primary IP address is 10.10.10.10, you could have the server listen on 10.10.10.11 as well by adding:

```
ifconfig eth0:0 10.10.10.11
```

to the file /etc/rc.local.  Then upon reboot your machine will appear to have two Ethernet adapters with separate addresses.

I have used aliasing to create multiple SSL-enabled web sites on a single machine using one IP for each domain or virtual host.  It also comes in handy when you want to assign a public IP address that forwards to a service behind the organization's firewall.  

A client got blacklisted by Barracuda the other day because an infected workstation behind the firewall became a spambot.  Luckily the admins fixed the problem and got de-listed, but if the blacklist managers dragged their feet, I was planning on swapping my client's blacklisted address with another one in the subnet we manage and assigning the blacklisted address to a virtual Ethernet adapter to ensure that nothing breaks.  I'd have to make a couple of changes to the iptables ruleset as well, of course.

According to the link, different subnets are used, which I thought was a requirement.  I did not know you can use ip's in the same subnet for the alias.

Thanks for posting this.

---

### Post by SeijiSensei on 2013-01-01
> **volkswagner said:**
> According to the link, different subnets are used, which I thought was a requirement.  I did not know you can use ip's in the same subnet for the alias.

I think the example chose to use an alias in a different subnet to show it can be done.  I've actually only ever created aliases within the same subnet as the primary IP.

---

