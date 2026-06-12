---
title: "Replacing Windows 2000 server with ubuntu server steps?"
date: 2012-07-27
forum: Server Platforms
---

### Post by X1R1 on 2012-07-27
Hi guys,

Currently our windows 2000 server provides Active Directory,DNS and DHCP services for my small office network.

Also there is an ubuntu server 10.04 that provides samba, proxy (squid) and firewall (shorewall) for the whole network.

The windows 2000 server has being giving a lot of problems regarding performance and service availability (it fails almost every day) so I want to move all of the services the Windows Box provides to my Ubuntu Box (which runs perfectly atm :D)

I have succesfully setup the DHCP server on the ubuntu machine (I set it as authoritative), although I haven't deactivated the DHCP server on the win 2000 machine.

How should I proceed with the other services? Active Directory I guess might give me some problems but I think samba has that covered right? I would need to change the domain controller so that the ubuntu machine is now the Primary Domain Controller.

Is it best to create a new domain on the ubuntu machine and then join the machines to the new domain? or can I just leave the same domain name and just "transfer" the PDC to the ubuntu machine?

And what about DNS? can there be problems with the migration?

thanks a lot for the input!!!!

---

### Post by sentinelace on 2012-07-29
Well I don't think Ubuntu is an ideal dc.  Samba has very poor performance compared to windows.  Why not upgrade to server 2008r2?  There is no ad in Ubuntu.  Install bind for dns.

personally if you want to use Ubuntu server, you need to thoroughly test your network in a test environment and make sure everything works.  Do all your software apps run under Linux?

---

### Post by X1R1 on 2012-07-30
sentinelace, to answer your questions:

Why no upgrade to server 2008r2: The server hardware in which win 2000 server is installed is not really a server, its just a normal computer with normal specs that performs poorly (takes about 5-7 mins to boot or restart).

Imagine putting 2008r2 inside this machine, I dont even think the system would boot :D

On the other hand, the Ubuntu server already in place there has very good hardware and performace, more than capable of absorbing the win 2000 tasks.

Do all my software apps run under Linux: Yes, the primary software we use is just a remote connection, no software to install on any machine, and the win 2000 server has nothing to do with it.

Also the AD in place is just providing login authentication, so even If samba has poor performance in comparison to windows AD, it still serves for my purposes.

---

### Post by albandy on 2012-07-30
> **sentinelace said:**
> Well I don't think Ubuntu is an ideal dc.  Samba has very poor performance compared to windows.  Why not upgrade to server 2008r2?  There is no ad in Ubuntu.  Install bind for dns.

personally if you want to use Ubuntu server, you need to thoroughly test your network in a test environment and make sure everything works.  Do all your software apps run under Linux?

We migrated from 2003 server to Linux Samba for file sharing. Our tests reported that Linux with samba was 3 times faster.

And some tests made by others showed similar results:
[http://www.kegel.com/nt-linux-benchmarks.html#file](http://www.kegel.com/nt-linux-benchmarks.html#file)

---

### Post by albandy on 2012-07-30
> **X1R1 said:**
> sentinelace, to answer your questions:

Why no upgrade to server 2008r2: The server hardware in which win 2000 server is installed is not really a server, its just a normal computer with normal specs that performs poorly (takes about 5-7 mins to boot or restart).

Imagine putting 2008r2 inside this machine, I dont even think the system would boot :D

On the other hand, the Ubuntu server already in place there has very good hardware and performace, more than capable of absorbing the win 2000 tasks.

Do all my software apps run under Linux: Yes, the primary software we use is just a remote connection, no software to install on any machine, and the win 2000 server has nothing to do with it.

Also the AD in place is just providing login authentication, so even If samba has poor performance in comparison to windows AD, it still serves for my purposes.

Esta guia te puede resultar útil. Yo la utilicé cuando hice la migración, pero está algo desfasada, es para 8.04 aunque no hay muchas diferencias, quizás tengas algún problema con la configuración del LDAP, pero googleando un poco lo conseguirás.

[http://www.tuxjm.net/docs/samba+ldap-como/html-onechunk/](http://www.tuxjm.net/docs/samba+ldap-como/html-onechunk/)

---

