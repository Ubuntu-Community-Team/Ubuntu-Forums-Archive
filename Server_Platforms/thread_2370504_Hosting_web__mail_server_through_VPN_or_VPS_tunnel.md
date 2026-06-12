---
title: "Hosting web / mail server through VPN or VPS tunnel"
date: 2017-09-04
forum: Server Platforms
---

### Post by devin0 on 2017-09-04
I am looking to run a web and mail server from my local business. I have a machine with modest hardware specs, i want to use it to run a mail and web server.
Unfortunately, on the internet connection the equipment is located at, ports needed for hosting are blocked and the IP is most certainly on spam blacklists. Would it be possible to 
rent a VPS or vpn, and have the traffic go to my hardware at the business? It seems like it should be possible, but I am uncertain of how to go about doing so. Something like a VPS connection or a ssh tunnel.

The end goal would be for traffic to get to my local hardware but it have the external IP of the VPN or VPS host.

Any help or suggestions are much appreciated.

---

### Post by darkod on 2017-09-04
It can work, but if you already get a VPS, why not use that for the web/mail hosting? That way it will be located in a provider datacentre and with a good fast internet connection.

---

### Post by devin0 on 2017-09-04
I have a lot of hardware on hand locally. I want to use it.

Seems kind of senseless and redundant, easier to just rent a VPS, I know, but i want to do it that way anyhow.

---

### Post by SeijiSensei on 2017-09-04
I rent virtual servers from [Linode](https://linode.com).  One of them accepts my inbound mail and hosts web sites.  Another runs MailScanner to cleanse the mail of viruses and spam, then routes the cleaned traffic off to delivery servers, one of which in is my home office.

To do this I use OpenVPN with [static point-to-point tunnels](http://openvpn.net/static.html).  The mail server in my house connects as a client (using OpenVPN's "remote" directive) to one of the Linodes and sets up the primary tunnel.  That Linode runs as a router connecting to my other cloud servers over other such tunnels.  Each one requires a unique open port.  My iptables rules only allow connections to those ports from the public IP addresses of the machines they serve.  Create a good encryption key like the result of 
```
ps auxw | sha256sum | awk '{print $1}'
```

Using your own servers is fine as long as you're not hosting other peoples' services.  I switched from hardware to virtual machines some years ago now to avoid the inevitable outages that comes with maintaining physical machines.  Now I let Linode host everything in big honking server rooms with good A/C, electrical power, and a large pipe to the Internet.  I also pay them a couple of bucks each month for daily snapshot backups of each VM in case disaster strikes.  In addition, I make an rsync backup of selected directories from these machines each night to a drive in my home office.

---

