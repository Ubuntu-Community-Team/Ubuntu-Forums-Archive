---
title: "HTTP Error 403.1 - Ubuntu on VMware with Apache"
date: 2010-04-25
forum: Server Platforms
---

### Post by joe12312 on 2010-04-25
Hi, I'm pretty new to all this Ubuntu. I have Ubuntu 9.10 running on VMware which is running Apache so I can use php with MySql. I should also add that currently, I have a server machine which is running IIS. From the server machine, on the DNS I forward php.josephsawyer.net towards the IP of the virtual machine. When I visit php.josephsawyer.net in the LAN I can see the page with php and everything nicely. When a user outside of the LAN visits, they get an error. Click the link below to see the error for yourself:
[http://php.josephsawyer.net]("http://php.josephsawyer.net/")

I would really appreciate it if someone has a solution for my problem.
Thanks in advance,
joe12312.

---

### Post by koenn on 2010-04-25
Hm, that's an **IIS** generated error, so it's hardly an Ubuntu or Apache problem :
> HTTP Error 403.1 - Forbidden: Execute access is denied.
Internet Information Services (IIS)


Apparently, you don't allow script execution > 
You have attempted to execute a CGI, ISAPI, or other executable program from a directory that does not allow programs to be executed.


So, if you expected that internet users would get your Ubuntu/Apache website, that "forwarding" of yours isn't working.

What did you do ?

---

### Post by joe12312 on 2010-04-25
Well, I did the same as I do for anyother domain/subdomain in DSN by creating a new Host (A) and then for the data set it to the IP of the Ubuntu VM instead of the server machine.

---

### Post by koenn on 2010-04-25
> **joe12312 said:**
> Well, I did the same as I do for anyother domain/subdomain in DSN by creating a new Host (A) and then for the data set it to the IP of the Ubuntu VM instead of the server machine.

I assume you mean DNS ? DSN is for database connectivity, iirc

I have no idea how you did the other (sub)domain, so that doesn't really help. 

That DNS server, is it a publicly accessible server ?
Does that virtual machine have a routeable address? Does a route exist from the internet to the IP address of that VM ? ...

---

### Post by joe12312 on 2010-04-25
Yes, I did mean DNS.
Yes, the DNS server is publicaly accessible. This is how I have it set up:

Server machine running Windows Server 2003 - on dnsmgmt under SERVER>Forward Lookup Zones>josephsawyer.net there are several Host(A)'s with the Data of 192.168.2.4 (Server's local IP). I added a new Host(A) with the name of php and set the Data to 192.168.2.13 (Ubuntu's local IP).

The Host (A)'s that lead to the server's IP all work and are fully functioning on the web.

---

### Post by koenn on 2010-04-25
DNS for your domain is
```

;; ANSWER SECTION:
josephsawyer.net.	86204	IN	NS	ns3.ukdnsservers.co.uk.
josephsawyer.net.	86204	IN	NS	ns3.ukdnsservers.co.uk.

```

according to those name servers, you're at
```

josephsawyer.net.	86400	IN	A	81.86.240.96

```

so all this DNS stuff you're doing on the Windows 2k3 server is meaningless to the internet. Those 192.168.x.x adresses aren't routable, anyway.
To the internet, php.josephsawyer.net is at 81.86.240.96.


This isn't something you can fix with DNS. You probably want port forwarding on your router. 
There's plenty of threads on that on these forums
[http://www.google.be/search?q=site%3Aubuntuforums.org+router+port+forward](http://www.google.be/search?q=site%3Aubuntuforums.org+router+port+forward)

---

