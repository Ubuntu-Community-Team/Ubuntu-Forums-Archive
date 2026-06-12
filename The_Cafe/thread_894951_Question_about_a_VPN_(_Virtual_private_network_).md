---
title: "Question about a VPN ( Virtual private network )"
date: 2008-08-19
forum: The Cafe
---

### Post by ODF on 2008-08-19
My girlfriend is working at home by internet using a VPN, she asked me if it's possible for her employer to see what she's doing on her computer. Since I'm not 100% sure it is not possible I'm asking to you guys =)

Thx a lot.

---

### Post by Daveski on 2008-08-19
If they could, this would have nothing to do with the connection being a VPN. If they can see what you are doing when plugged in to their network, then they will be also able to see what you are doing while VPN connected. Any 'spying' would not be related to the type of connection.

---

### Post by ODF on 2008-08-19
Thank you =)

If someone have something interesting to say about a VPN it would be appreciated.

---

### Post by toupeiro on 2008-08-19
Most company VPN's, for all intensive purposes, provide an extention of their business intra-network to your machine over the internet by some method of secure authentication like RSA or Radius.

Typically, VPN's become the primary interface on a client machine while activated, meaning you do not have access to your private LAN while connected, but generally neither to they.  You can sometimes "trick" this by having multiple interfaces enabled on your machine to access both networks, but I'd say its generally not in your best interests to do this..  Its a GOOD thing you cannot do both...  If you want to browse the web while VPN connected, you may have to resolve to an intra-network proxy server.  While the business network may not be able to access your home LAN, that is not necessarily the case for your machine and local filesystems.  Your machine has become a peer on another network, and if permissions have been applied locally to let accounts other than local accounts access your filesystems, they can be accessed unless that functionality has been explicitly denied at the VPN entrypoint.

Think of it like a multi-lane freeway under some sort of construction.  They may use cinderblock to "tunnel" a specific kind of traffic through another route to a specific destination.  This is sort of what a VPN tunnel does with your internet connection.  Its still a part of the overall freeway, which would be equivalant to your ISP connection, but it is point-to-point and other "Traffic" cannot enter or exit the tunnel unless it is originating from either point, and in some cases allowed to flow both directions..

---

### Post by Daveski on 2008-08-19
Split tunneling can allow you to continue to access your private network and / or that of the public internet while connected to another private network via VPN. However, this is considered a security risk as your machine can become a bridge between the 2 private networks (yours and theirs). Theoretically it is also possible in this situation that another client on the corporate network could access other machines on your private network (bit tricky to setup though).

BTW if the corporate VPN is the Microsoft PPTP system, then it is a breaze to setup the VPN in Ubuntu by just asking the network manager to configure a VPN connection. You just need the host or IP of the PPTP server and your username and password.

---

### Post by mrsteveman1 on 2008-08-19
Usually VPNs just provide access to a specific IP range at a corporate network, so anything you do on that network is visible to the employer just like if you were in the building.

Everything else should work normally and they can't tell what else you do on the internet or on your computer.

---

### Post by mips on 2008-08-20
> **ODF said:**
> My girlfriend is working at home by internet using a VPN, she asked me if it's possible for her employer to **see what she's doing on her computer**. Since I'm not 100% sure it is not possible I'm asking to you guys =)

Thx a lot.

Depends. If she is using the works internet access via the VPN then they would be able to see all her internet traffic.

If the work is managing her computer (like many corporates) and have remote access to her machine then yes they can see everything.

Same goes for things like sharing folders etc on her computer.

---

