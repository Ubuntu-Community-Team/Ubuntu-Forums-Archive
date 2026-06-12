---
title: "[need advice] is this possible !!!"
date: 2008-06-23
forum: Server Platforms
---

### Post by MAO on 2008-06-23
i've got:

1) Ubuntu Server 8.04 with BIND (DNS Server) - internet ip 222.222.222.222 and local ip 192.168.222.222
2) Windows Server 2003 with only local ip 192.168.222.111

Quation is:

How to use BIND DNS Server and install MS Exchange on Windows Server 2003. And is polisble to install Active Directory on Windows Server 2003?

---

### Post by gtdaqua on 2008-06-23
Certainly possible. 

Are you trying to achieve:
Use Exchange 2003 to send/receive emails over the internet?
Use Active Directory (with exchange) to authenticate users?

Of course, possible.

Use Ubuntu as BIND DNS for name resolution? Why dont you use your Windows DNS as nameserver? Your Win2k3 server will automatically be a DNS because it is going to have AD in it.

Second, you are trying to secure your internal network with local IP addresses. You can set up the public IP on your router and ask your router to perform NAT for the internal network.

Because you are using Exchange for emails, you should also forward SMTP port 25 on your router to the Exchange server.

Basically, a piece of cake :)

---

### Post by rickyjones on 2008-06-23
> **MAO said:**
> i've got:

1) Ubuntu Server 8.04 with BIND (DNS Server) - internet ip 222.222.222.222 and local ip 192.168.222.222
2) Windows Server 2003 with only local ip 192.168.222.111

Quation is:

How to use BIND DNS Server and install MS Exchange on Windows Server 2003. And is polisble to install Active Directory on Windows Server 2003?

Wow, I think your post is a tad confusing. This is how it sounds to me:

1. You have an Ubuntu 8.04 server as your router and DNS server.
2. You have a Windows Server 2003 system on your local network.
3. You want to install Exchange and Active Directory on this Windows server.

First and foremost you will need Active Directory installed on the Windows Server 2003 system in order to install Exchange on it. This is a pre-requisite. Installing AD is not difficult at all, it involves running a single command after you have the basics configured (static IP, working internet, etc...).

Second the Windows server will automatically become a DNS server to accommodate Active Directory. Exchange will use this DNS server. You can configure the DNS services to forward requests to your current DNS server, however.

I hope this helps!

Sincerely,
Richard

---

### Post by MAO on 2008-06-24
[SIZE="1"][COLOR="DarkOrange"]sorry for my English[/COLOR][/SIZE]


> 
First and foremost you will need Active Directory installed on the Windows Server 2003 system in order to install Exchange on it. This is a pre-requisite. Installing AD is not difficult at all, it involves running a single command after you have the basics configured (static IP, working internet, etc...).

Second the Windows server will automatically become a DNS server to accommodate Active Directory. Exchange will use this DNS server. You can configure the DNS services to forward requests to your current DNS server, however.


it means i must work only with Windows Server/

NAT from route to WinSRV by ports 110 25 443?
Thats all ?
Ok i will try!
Thanx for **gtdaqua** and **rickyjones**

---

