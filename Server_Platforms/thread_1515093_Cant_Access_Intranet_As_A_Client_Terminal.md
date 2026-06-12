---
title: "Cant Access Intranet As A Client Terminal"
date: 2010-06-21
forum: Server Platforms
---

### Post by Nhoel on 2010-06-21
We currently have a web server installed on a windows machine. We bought a new computer and I installed a ubuntu linux on it. My problem is that I can't access the intranet web application just like windows does [http://mysebserver/mypage](http://mysebserver/mypage).

If we can make this work, we can save HUGE cost. Since these terminals are only intended to be sue as a client for our internal web apps.

PLEASE HELP!

---

### Post by BobVila on 2010-06-22
It's probably a DNS server problem. Your windows machines, when joined to an Active Directoy, will use the AD servers as their DNS servers. If you haven't set the network up properly, the Linux machine probably isn't using the same IPs. 

To check this, try going to [http://xxx.xxx.xxx.xxx/mysite](http://xxx.xxx.xxx.xxx/mysite) (where the x's are the webserver's IP address.)

If that works, you need to add your Windows DC's IP address to the nameservers list on your Ubuntu box.

Of course, all of this assumes that you have a Windows domain there and that you can access this intranet site from the Windows workstations... If that's not the case, you've got bigger problems.

---

### Post by koenn on 2010-06-22
@BobVilla:
I agree is most likely a DNS issue, but your explanation is a bit off. Windows domain members need ***a*** DNS server, but that is not necesarily a Domain Controller.



@OP
first, test with IP addresses the way BobVilla described
then,  check what DNS servers these 'terminals' use, and whether this DNS server knows  the address of your intranet web server

if that's OK, your prroblem is possibly that you use the server's hostname. You may need a Fully Qualified Domain Name, such as myserver.mydomain.tld

The reason your windows clients don't need this, is either you have netbios/wins that allows them to use netbios hostnames, or they automatically append the domain portion when doing DNS requests. 
The latter can also be configured on your Linux clients

or you could simply make shortcuts/bookmarks that include the FQDN

---

### Post by Nhoel on 2010-06-23
Watda! it works!
BobVila's [http://xxx.xxx.x.x/mypage](http://xxx.xxx.x.x/mypage) totally works!

I can't still do this on [http://webserver/webpage](http://webserver/webpage).
But I'll use that tweak as a band-aid solution.

@BobVila
I can access the intranet site using windows machines.
Ill check the DNS issue.
thanks, hope I can do this on [http://webserver/webpage](http://webserver/webpage)

thanks a lot! you all rocks:guitar:

---

### Post by Nhoel on 2010-06-23
okay, im back. if it's not too much. can you please teach me how to do the DNS thing.
Im still starting playing with linux, ill be googling this, but it will be great if you can teach me here.

@KOENN -Im just curious on who's OP? Is that me? What's OP? thanks koenn.

---

### Post by koenn on 2010-06-24
> **Nhoel said:**
> 

@KOENN -Im just curious on who's OP? Is that me? What's OP? thanks koenn.
OP = Original Poster (thread starter, you) or Original Post (first post, post that started this thread)

---

### Post by koenn on 2010-06-24
in /etc/resolv.conf of your linux clients, add a 'domain' or 'search' directive.

eg
```

search mydomain.tld
nameserver 123.123.123.123

```
now, if this pc needs the adress of 'myserver', it will ask for the address of 'myserver.mydomain.tld'. 


If you configure clients through dhcp, you should include the dhcp option "domain name = mydomain.tld"

---

