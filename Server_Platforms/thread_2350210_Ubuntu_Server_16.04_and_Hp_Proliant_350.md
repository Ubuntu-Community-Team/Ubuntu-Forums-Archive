---
title: "Ubuntu Server 16.04 and Hp Proliant 350"
date: 2017-01-22
forum: Server Platforms
---

### Post by saulblas77 on 2017-01-22
Good morning before anything and thank you in advance.

I  tell you the problem that I face, we have a network with about 80  computers, connect to the internet through a DHCP server hp with windows  server 2008 RC2 which is used as a DHCP server, there are about 60  computers with ubuntu 16.04 LTS and The  rest manage windows, all of them access the internet through the DHCP  server without problems, without fixed IP or preconfigure DNS, we added a  server that was retired but that works perfectly, had windows server  2003, we have installed ubuntu Server  16.04 and is not able to resolve DNS's, it is able to see all the  computers on the network, see the DHCP server (if I ping the DHCP server  this responds, if I ping the DNS it receives it perfectly) but Is  not able to access the internet., I ping google.com and the answer is  connect: network is unreachable, I access the network using the icon and  it tells me the ip perfectly but it puts me "wired 100 mb - unmanaged"  address (....)  address IPV4 (.....) address IPV6 (....), the parentheses would  represent the IP addresses, I tried to configure the network manually by  putting a fixed IP to the ubuntu server, with Your gateway and DHCP and remains unresolved.

I do not think they are the network card, since I can see all the computers on the network.

How can I solve that? What I can do? Do not let me use gasoline, dynamite or a 20-kilo hammer .... ha ha ha

P.D  .: I took my home server with Ubuntu server 16.04 LTS and connects  perfectly, solves the IPs without problems, all very correct.

---

### Post by darkod on 2017-01-22
First you need to decide if you want to use dynamic or static IP on the server. Servers usually use static IPs that do not change. So, make the decosion and configure the network as needed.

Then, you say you installed the server version but are mentioning icons. Do you have a GUI installed? When you say you installed server version that means the standard installation with command line only. If you installed the Desktop version or added a GUI you need to say so, because the network is controlled differently and people that help need to know that.

What do you have installed exactly?

---

### Post by saulblas77 on 2017-01-23
Thank you very much for answering.

I installed ubuntu server 16.04lts and then installed the Ubuntu desktop.

I have static IP, I do not want it to change.

The problem is  in the following, I can not access the internet, I can not resolve the  DNS of the DHCP server, if I can see the whole network and even work  with the different computers that are on the network, but it does not  allow me to enter the internet.

Thank you very much.

---

### Post by darkod on 2017-01-23
I have never installed a GUI on ubuntu server so I don't know 100% what it does, but I think in such case it installs Network Manager to handle the network. Like on the Desktop version.

Have you checked the Network Manager for connection information to confirm you have set everything correctly? When using static settings all parameters must be correct (IP address, netmask, default gateway, DNS serves to use).

Also have you tried ping 8.8.8.8 from the server? if it works, that means you only have dns issues. If ping 8.8.8.8 does not work, that means you probably have routing issues.

In any case, if you post a screenshot of the connection information it might help locate the problem.

---

### Post by saulblas77 on 2017-02-01
Thank you so much for help me.

As you want me to send you the screenshots.

A cordial greeting:

---

### Post by saulblas77 on 2017-02-01
[IMG]http://hpes.i.lithium.com/t5/image/serverpage/image-id/32873i7B3FED2E70B3AB9C/image-size/original?v=1.0&px=-1[/IMG]

---

### Post by darkod on 2017-02-01
What about the screenshot of the connection information? If you use a GUI, then Network Manager is controlling the network. Click on its icon on the top statuc bar and select Connection Information.

The screenshot you posted does not show which gateway you have configured and which dns server are you using.

PS. Alternatively, if you want to keep working in terminal, post the output of:
```
cat /etc/resolv.conf
route -n
```

You can post just the text output in CODE tags, you don't have to post screenshot if it's only text output in terminal.

---

