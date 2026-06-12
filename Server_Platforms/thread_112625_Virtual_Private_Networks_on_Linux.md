---
title: "Virtual Private Networks on Linux???"
date: 2006-01-04
forum: Server Platforms
---

### Post by dalani on 2006-01-04
An [article in a magazine tailored for business types]("http://www.profitguide.com/technology/article.jsp?content=20050602_154329_6436") mentioned VPN :

>  It costs only a few hundred dollars to install a VPN router for 10 to 20 users. If you're accessing large files remotely, the connection can be slow. One solution is Microsoft's Terminal Services tool, which displays a virtual representation of files rather than opening each one. But, it works only with VPNs operating on Microsoft's Small Business Server platform.

Can anyone tell me if there is something similar (or better) on Ubuntu Linux for implementing a virtual private network as easily???

---

### Post by DoorGunner on 2006-01-04
Like you quote says VPN's are usually gateways to larger lan systems. For instance if you work for a large company or government office you probably use a lan system. A vpn is a way inwhich the company can let you in securely. 

Vpn routers will only work properly with other vpn routers. VPN is somewhat propietary and It is still very much in its infancy. If you have access to a cisco vpn and want to use a linksys vpn be sure they are compatable technology. (not all vpns are compatible)

Set up is criticle. If your setup is week you can in advertently feed your codes and encryption to third parties. The third party could easily become the controler of your system.

There are VPN softwares available for linux. But you really need to research you vpn and ensure its compatability.Thats my best advice.

---

### Post by dalani on 2006-01-05
Ok thanks, that's a good overview. I think a password protected webpage with company ready ftp might be an alternative yes.? It's not an immediate need but our co. sends 100meg+ of files through email attachments weekly interupting flow and tying me down with time wasted confirming mailbox quotas and filter settings over the phone with clients. If a gateway or password protected webpage/ftp setup was implemented, it would save time.
Anyways that another discussion...

---

### Post by Soleil-Raid on 2006-01-08
[QUOTE=dalani]Ok thanks, that's a good overview. I think a password protected webpage with company ready ftp might be an alternative yes.? It's not an immediate need but our co. sends 100meg+ of files through email attachments weekly interupting flow and tying me down with time wasted confirming mailbox quotas and filter settings over the phone with clients. If a gateway or password protected webpage/ftp setup was implemented, it would save time.
Anyways that another discussion...[/QUOTE]

Yeah, that's probably easier for your purposes.

However, for VPN's in future, take a look at OpenVPN. works on just about everything except PDAs.

---

### Post by Mr_Grieves on 2006-01-11
Sure.. check this out, OpenVPN:
[http://openvpn.net](http://openvpn.net)

Installation tips:
[http://kerneltrap.org/node/5018](http://kerneltrap.org/node/5018)

For a FTP solution I would strongly advise you to check out VsFTPd, it's the most secure FTP server out there. And aswell, remember to at least use TCP-wrappers something that give the posibility of just allowing sertain IP-networks to connect.
[http://vsftpd.beasts.org](http://vsftpd.beasts.org)

---

### Post by kosmic on 2006-01-14
OpenVPN very simple to configure and use, and works also in Window$

---

