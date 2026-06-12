---
title: "&quot;Configure VPN&quot; in Network Manager is grayed out, what can I do?"
date: 2017-04-19
forum: Server Platforms
---

### Post by esolve3 on 2017-04-19
I'm using VPN to access network. I have configured PPTP and L2TP.
I upgraded my system from 14.04LTS to 16.04LTS yesterday. During the upgrading, I removed some ppa which seems to be related to L2TP.
After the upgrading, the L2TP function doesn't work(if I click the configured L2TP connection, the network manager icon suddenly disappear), and the "configure VPN" button is grayed out, as shown in the pic.
I installed L2TP through source codes. And now if I click L2TP, it immediately prompts "connection successful", but the connection may not be OK.
And the "Configure VPN" is still grayed out, what can I do?

[http://i.imgur.com/p3zUA6n.jpg](http://i.imgur.com/p3zUA6n.jpg)

---

### Post by feartheterrapin on 2017-04-19
Something odd happened during an update a month ago or so. 

Under &#8220;VPN Connections&#8221;, &#8220;Disconnect VPN&#8221;had been removed.

  Under &#8220;VPN Connections&#8221;, &#8220;Configure VPN&#8221; is greyed out and not longer available.

In addition, if you connected to VPN using OPENVPN, then disconnect from VPN, you would then would not be able to reconnect to VPN until restarting your network services.  The DNS (resolv.conf) seemed to get got hosed.  There was a bug identified and this issue was resolved in the past week.  However, the other two issues were not addressed.

---

### Post by esolve3 on 2017-04-19
> **feartheterrapin said:**
> Something odd happened during an update a month ago or so. 

Under “VPN Connections”, “Disconnect VPN”had been removed.

  Under “VPN Connections”, “Configure VPN” is greyed out and not longer available.

In addition, if you connected to VPN using OPENVPN, then disconnect from VPN, you would then would not be able to reconnect to VPN until restarting your network services.  The DNS (resolv.conf) seemed to get got hosed.  There was a bug identified and this issue was resolved in the past week.  However, the other two issues were not addressed.

you mean the problem I encountered is universal?
all computers with 16.04LTS have their "configure VPN" grayed out?

---

### Post by feartheterrapin on 2017-04-19
> **esolve3 said:**
> you mean the problem I encountered is universal?
all computers with 16.04LTS have their "configure VPN" grayed out?

Yes, I believe it is universal, as well as the “Disconnect VPN” being removed and both issues happened at the same time as the DNS/resolv.conf issue.  But only the DNS/resolv.conf issue was fixed.

---

### Post by esolve3 on 2017-04-20
> **feartheterrapin said:**
> Yes, I believe it is universal, as well as the “Disconnect VPN” being removed and both issues happened at the same time as the DNS/resolv.conf issue.  But only the DNS/resolv.conf issue was fixed.

so you mean we can only wait for the ubuntu devlopers to fix it?

---

### Post by feartheterrapin on 2017-04-20
> **esolve3 said:**
> so you mean we can only wait for the ubuntu devlopers to fix it?

That is my understanding.  And based on the lack of discussion/complaints, I assume there is no priority to fix it.

I assume you know you still can configure VPN under Network/Edit Connections.

---

### Post by esolve3 on 2017-04-20
> **feartheterrapin said:**
> That is my understanding.  And based on the lack of discussion/complaints, I assume there is no priority to fix it.

I assume you know you still can configure VPN under Network/Edit Connections.

 but it doesnt work well, for example, L2TP always pretends to succeed in connection although it doesn't succeed in connecting the VPN proxy server. And google/youtube are not accessable frequently, I don't know why

(I'm in China, I can't use google/facebook if I don't use VPN. I can use the proxy on my phone and visit google/youtube, but not in Ubuntu 16.04LTS on my laptop)

---

### Post by wildmanne39 on 2017-04-20
Please use thumbnails or Url's when posting images because many people have slow internet connections or limited band width.

*Thread moved to **Server Platforms**.*

---

### Post by feartheterrapin on 2017-04-20
> **wildmanne39 said:**
> Please use thumbnails or Url's when posting images because many people have slow internet connections or limited band width.

*Thread moved to **Server Platforms**.*

I am trying to understand why this thread was moved to "Server Platforms".  Isn't this a network issue?  It seemed to came about with network changes.

---

### Post by feartheterrapin on 2017-04-20
> **esolve3 said:**
> but it doesnt work well, for example, L2TP always pretends to succeed in connection although it doesn't succeed in connecting the VPN proxy server. And google/youtube are not accessable frequently, I don't know why

That sounds like the problem I was experiencing before the recent update.  My work around was deleting the etc/resolv.conf  symbolic link and creating a resolv.conf file with DNS servers of my choice.  My  etc/resolv.conf looked like this:

```
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx
```

Just subsitude xxx.xxx.xxx.xxx with the server of your choice.  Maybe you can use Google DNS, 8.8.8.8 and 8.8.4.4

---

### Post by saegerei on 2017-04-20
VPN related packages on my Ubuntu 16.4 laptop:

libnm-glib-vpn1
network-manager-openvpn
network-manager-vpnc
network-manager-vpnc-gnome
openvpn
vpnc
vpnc-scripts

The last two are related to VPN connections of the Cisco type. I don't know exactly what it is but my routers support this type of VPN.

---

### Post by feartheterrapin on 2017-04-20
> **esolve3 said:**
> but it doesnt work well, for example, L2TP always pretends to succeed in connection although it doesn't succeed in connecting the VPN proxy server. 

Looking through my VPN settings, I don't see L2TP..  So Googling shows me it is not a common configuration for Ubuntu 16.  But there were a few guides I saw.

[http://www.jasonernst.com/2016/06/21/l2tp-ipsec-vpn-on-ubuntu-16-04/](http://www.jasonernst.com/2016/06/21/l2tp-ipsec-vpn-on-ubuntu-16-04/)
[https://askubuntu.com/questions/789421/l2tp-ipsec-psk-vpn-client-on-xubuntu-16-04](https://askubuntu.com/questions/789421/l2tp-ipsec-psk-vpn-client-on-xubuntu-16-04)
[https://gist.github.com/psanford/42c550a1a6ad3cb70b13e4aaa94ddb1c](https://gist.github.com/psanford/42c550a1a6ad3cb70b13e4aaa94ddb1c)

---

### Post by klar on 2018-04-16
> **esolve3 said:**
> I'm using VPN to access network. I have configured PPTP and L2TP.
I upgraded my system from 14.04LTS to 16.04LTS yesterday. During the upgrading, I removed some ppa which seems to be related to L2TP.
After the upgrading, the L2TP function doesn't work(if I click the configured L2TP connection, the network manager icon suddenly disappear), and the "configure VPN" button is grayed out, as shown in the pic.
I installed L2TP through source codes. And now if I click L2TP, it immediately prompts "connection successful", but the connection may not be OK.
And the "Configure VPN" is still grayed out, what can I do?

[http://i.imgur.com/p3zUA6n.jpg](http://i.imgur.com/p3zUA6n.jpg)

I've searched the same thing.  No success.

What I really wanted to do, however, is to configure a VPN client connection using an .ovpn (OpenVPN) file I received.
And this without the need to dig in certs structures in the VPN config.

At least on my Ubuntu 16.04.4 LTS with OpenVPN installed, I successfully installed a VPN using
Network manager
-> Edit connections
-> Add
Under the pop-down there is:
-> Import a saved VPN configuration ...
where one can enter a .ovpn file configuring the config & certs for the OpenVPN client.

Maybe this helps ;-)

Happy VPNing,
Klaus

---

