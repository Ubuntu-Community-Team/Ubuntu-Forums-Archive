---
title: "Ubuntu Server 14.04 acting as router and VPN server"
date: 2015-04-11
forum: Server Platforms
---

### Post by adrian.tomov on 2015-04-11
Hi guys,

I know there are like a million topics on how to setup a VPN server but the more I read the more confused I get so I hope you don't mind me formulating my question as a new topic.
The situation goes like this, I have a small office setup with one PC with two NICs running a Ubuntu Server 14.04 and acting as a gateway/router. My internet connection is connected to the first NIC and all traffic is routed to the second NIC with a DHCP server enabled. I have connected 4 PCs, 2 laptops, a network printer and a NAS device. To visualize the setup a bit:
Gateway:
eth0 - ip: 77.70.***.***
etho1 - ip: 10.0.0.1

Clients:
ip-range: 10.0.0.2 - 10.0.0.30

Here comes my problem. My business requires that I have 8-10 android devices connected to my office network so that all traffic goes through my static ip at the office and also to have access to my NAS and printer. Also in the near future several laptops will need to do the same from outside my office internal network. So far I have decided that the best option is to setup some form of VPN. Here is where my knowledge seizes. I want to setup a VPN server on my gateway so that clients can connect to it from the outside world, however I want to make all devices in the office part of the VPN network. Any ideas how to do that? 

Thanks in advance for your help?

---

### Post by darkod on 2015-04-12
Hold on... Connecting outside devices to your VPN is clear. That is the usual role of VPN to make outside devices as part of the internal network.

But your office devices are already part of your internal network. What do you mean by "make all devices at the office part of the VPN network"? There is no need to do anything about them... They already go out through your ubuntu server as gateway, and through your public internet IP.

As for installing OpenVPN, that's easy, and configuring is also quite easy.

To do the installation part you can follow this: [https://help.ubuntu.com/lts/serverguide/openvpn.html](https://help.ubuntu.com/lts/serverguide/openvpn.html)

Install the software and create the public key infrastructure setup. Then you need to decide if you will connect clients with certificates or username/password.

The sample server.conf file has plenty of parameters, when you get to that step we can give you a short version with the basic parameters only.

---

