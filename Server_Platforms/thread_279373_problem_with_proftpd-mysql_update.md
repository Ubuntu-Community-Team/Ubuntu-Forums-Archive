---
title: "problem with proftpd-mysql update"
date: 2006-10-17
forum: Server Platforms
---

### Post by jjross on 2006-10-17
just did the automatic update today and it changed the configuration files for proftpd.
I got past the config file problems but now I am getting this

> jim@jim:~$ sudo /etc/init.d/proftpd restart
 * Stopping ftp server proftpd                                           [ ok ]
 * Starting ftp server proftpd  
- IPv6 getaddrinfo 'jim' error: Name or service not known

Any ideas where to go from here to fix this

It appears that this does not interfere with the operation of proftpd, but I still have a problem,
When I try to log in to the FTP server it says
> 
server could not be found

I am using VHCS control panel for my server so it may be related to that after the proftpd upgrade.
I will keep looking , but if anyone has any ideas, let me know

---

### Post by jjross on 2006-10-18
I finally found the answer to my problem.
If anyone else is having this problem with VHCS and proftpd 1.3.0
check [this]("http://vhcs.net/new/modules/newbb/viewtopic.php?topic_id=6634&forum=3") link

---

### Post by slapper on 2006-10-21
The same problem here, it seems that the new version of proftpd has that problem. I get the same error just running anonymous ftp server and a vhost ftp
```

- IPv6 getaddrinfo 'mydomain.dyndns.org' error: No address associated with hostname
```

The server can start but when i try to log in as anonymous it takes  a long time

Any ideas ? :???: :???: 

I could not find the way to solve it ..

---

### Post by jjross on 2006-10-21
try this for the ipv6 problem
look at the readme in usr/share/doc/proftpd  it will list this

ProFTPD Server for Debian
-------------------------

** IPv6 issue:

In standalone mode proftpd binds both IPv4 and IPv6 addresses. That
causes a quite annoying message at startup on IPv4-only boxes, such as:

	IPv6 getaddrinfo 'your_host_name' error: Name or service not known

That can be avoided by keeping an IPv6 mapping for your_host_name in your /etc/hosts file, such as:

	::1 ip6-localhost ip6-loopback your_host_name

or also

	::fff:A.B.C.D	your_host_name

when you got a static IPv4 address A.B.C.D. The same is required for all IP4/6 addresses, just
in case your nameserver does not map your hostname and IPs.

this worked for me

---

### Post by slapper on 2006-10-23
Yep!!!! its ok now:) :) 

I just put my host name in /etc/hosts


```
::1 ip6-localhost ip6-loopback your_host_name
```

Thanks!!!!

---

