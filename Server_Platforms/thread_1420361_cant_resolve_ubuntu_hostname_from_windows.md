---
title: "cant resolve ubuntu hostname from windows"
date: 2010-03-03
forum: Server Platforms
---

### Post by Hathadar on 2010-03-03
I have two computers.

Computer A = windows 7.
Computer B = Ubuntu Server 9.10

Computer B automatically receives an IP address from my router.

I can ping computer B from computer A using the IP address.
I cannot ping computer B from computer A using its hostname.

My router did not show a hostname under it's active clients table.
After some searching I found a threat where somebody suggested modifying /etc/dhcp3/dhclient.conf and adding 'send hostname "blahblah"'
This allowed me to see the hostname in my router but I still cannot resolve it from my windows box.

How can I correct this?

---

### Post by techstop on 2010-03-03
The quickest method would be to put an entry in the hosts file on the Windows machine. There's plenty of howtos on this, google it, or try this example;

[http://www.ezlan.net/host.html](http://www.ezlan.net/host.html)

A long-term solution (if you have plenty of machines you want to access the server by host-name) is to install a DNS service on the ubuntu server.

[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

---

### Post by redmk2 on 2010-03-03
> **Hathadar said:**
> I have two computers.

Computer A = windows 7.
Computer B = Ubuntu Server 9.10

Computer B automatically receives an IP address from my router.

I can ping computer B from computer A using the IP address.
I cannot ping computer B from computer A using its hostname.

My router did not show a hostname under it's active clients table.
After some searching I found a threat where somebody suggested modifying /etc/dhcp3/dhclient.conf and adding 'send hostname "blahblah"'
This allowed me to see the hostname in my router but I still cannot resolve it from my windows box.

How can I correct this?

The windows machine needs to use the routers address as the primary DNS resolver.  If you have the Windows host get that information from the DHCP server (in the router) then you need to configure your DHCP settings.  make sure you include you ISP's DNS server as secondary resolver.

@techstop -- The "*an entry in the hosts file on the Windows machine*" method will only work if the IP address stays the same.  With DHCP you can't guarantee that.  As this is a dynamic process you need coordination between DHCP and DNS.  This is not possible with a static file.

---

### Post by techstop on 2010-03-03
> **redmk2 said:**
> @techstop -- The "*an entry in the hosts file on the Windows machine*" method will only work if the IP address stays the same.  With DHCP you can't guarantee that.  As this is a dynamic process you need coordination between DHCP and DNS.  This is not possible with a static file.

By suggesting to add an entry to the hosts file, I expected that it was understood that a static IP would be required. Not sure what you mean by > As this is a dynamic process you need coordination between DHCP and DNS.  This is not possible with a static file.

You can set DNS server addresses while using a static address (but on a home network this is likely to be the same as the gateway address).

EDIT: now you've got me confused, you don't need a DHCP server for a static IP.

---

### Post by redmk2 on 2010-03-03
> **techstop said:**
> By suggesting to add an entry to the hosts file, I expected that it was understood that a static IP would be required. 

The OP specifically stated that he was using DHCP by this statement : *[COLOR="Blue"]Computer B automatically receives an IP address from my router.[/COLOR]*

> 


Not sure what you mean by [QUOTE]As this is a dynamic process you need coordination between DHCP and DNS. This is not possible with a static file.

[/QUOTE]What this means is that the ***entries in the DNS server*** would need changing if the IP address changes (e.g. the mapping between the IP address and the hostname).  The address of the servers is not what I was taling about.  With a static file the mappings are set until you manually change them.> 

You can set DNS server addresses while using a static address (but on a home network this is likely to be the same as the gateway address).

EDIT: now you've got me confused, you don't need a DHCP server for a static IP.

Once again the OP sets the conditions and he/she said dhcp.

I personally prefer static addressing (manually configured IP addresses and DNS entries).

---

### Post by techstop on 2010-03-03
> **redmk2 said:**
> The OP specifically stated that he was using DHCP by this statement : *[COLOR="Blue"]Computer B automatically receives an IP address from my router.[/COLOR]*


OP is welcome (and encouraged) to change their network configuration to achieve their goals of being able to use hostname rather than IP address to access their ubuntu server

> Once again the OP sets the conditions and he/she said dhcp.
OP is welcome (and encouraged) to change their network configuration to achieve their goals of being able to use hostname rather than IP address to access their ubuntu server

> I personally prefer static addressing (manually configured IP addresses and DNS entries).

Good then. We agree.

---

### Post by redmk2 on 2010-03-03
> **techstop said:**
> ...


Good then. We agree.

No we do not agree.  In your original reply you made no mention of converting the Ubuntu host to a static IP address.  The OP may be unaware that he needs to do that.  Incomplete advice is worse that no advice at all.

---

### Post by doas777 on 2010-03-03
one way, is to configure samba as a wins server ("wins support = yes" in smb.conf and point your win boxes to it but it would require the server to have a static ip), but I'm sure there is a way to do it with just winbindd. google around to see.

---

### Post by Morbius1 on 2010-03-03
Have Computer B continue to get it's IP address from the router. Have the router assign the same IP address to that machine based on that machines MAC address.

For Netgear routers it's called "DHCP Address Reservation"
For D-Link routers it's called "Static DHCP"
Linksys routers are more problematic. Some routers can do it and some cannot.
It also goes by the names: "reserved DHCP", "reserved leases", and "Pre-assigned DHCP" .

Then the host file method would work assuming at that point you still need to do something at the hostname level since now all ip address are fixed.

---

### Post by redmk2 on 2010-03-03
> **doas777 said:**
> one way, is to configure samba as a wins server ("wins support = yes" in smb.conf and point your win boxes to it but it would require the server to have a static ip), but I'm sure there is a way to do it with just winbindd. google around to see.

An interesting addition of complexity to the situation.  The OP barely understands what he is doing at this point and you want him to add yet another server to the mix.

Winbind has nothing to do with name resolution.  The Winbind service is used to resolve user and group information from Windows NT/2000/2003/2008 servers.

---

### Post by Hathadar on 2010-03-03
Thank you for all who responded.  I still don't quite know where to go as there are there seems to be argument on the best way to proceed.

Some people say use a host file.  I prefer to not do this and keep everything dynamic.

Some people say use my machine as a DNS server however that seems to indicate I would have to assign a static IP to my ubuntu box.  Again, I would like to keep things dynamic.

Here is a question.  How do windows machines automatically resolve host names on a local network without using a DNS server or host files?  How is it that I can plug in a new windows box into my network and automatically be able to ping it via it's host name?

---

### Post by doas777 on 2010-03-03
> **Hathadar said:**
> Thank you for all who responded.  I still don't quite know where to go as there are there seems to be argument on the best way to proceed.

Some people say use a host file.  I prefer to not do this and keep everything dynamic.

Some people say use my machine as a DNS server however that seems to indicate I would have to assign a static IP to my ubuntu box.  Again, I would like to keep things dynamic.

Here is a question.  How do windows machines automatically resolve host names on a local network without using a DNS server or host files?  How is it that I can plug in a new windows box into my network and automatically be able to ping it via it's host name?

that functionality is part of the SMB protocol. SAMBA is the linux port of SMB. here is some info on smb/samba name resolution. [http://oreilly.com/catalog/samba/chapter/book/ch07_03.html](http://oreilly.com/catalog/samba/chapter/book/ch07_03.html)

---

### Post by Hathadar on 2010-03-03
Thanks, problem fixed.
I installed samba and configured it to be a wins server.
This allowed my windows machine to ping via host name.
I also installed winbind to allow my ubuntu box to ping my windows box.

---

