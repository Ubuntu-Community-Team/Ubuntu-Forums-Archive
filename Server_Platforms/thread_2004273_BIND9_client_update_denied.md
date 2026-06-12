---
title: "BIND9 client update denied"
date: 2012-06-15
forum: Server Platforms
---

### Post by anonymouschief on 2012-06-15
Hello All,

I am running BIND9 on Ubuntu Server 12.04. /var/log/syslog constantly reports entries similar to the following (where 192.168.1.100 represents the ip address of one of my dhcp clients and "ubuntuserver" is the DNS Server's hostname):


```
Jun 14 20:44:50 myubuntuserver named[19501]: client 192.168.1.100#50131: update 'example.local/IN' denied
```

I had initially thought that the errors were due to the fact that there is no secondary server so I added the following to my named.conf.options file:

```
allow-transfer {"none";};
```

That did not resolve the issue. Please help.

Thanks.

---

### Post by anonymouschief on 2012-06-15
No worries. I have found out what causes it, and will need to read more about finding a solution. Here is why the message comes up:

```
Q: 	
I keep getting log messages like the following. Why?

Jun 21 12:00:00.000 client 10.0.0.1#1234: update denied

A: 	
Someone is trying to update your DNS data using the RFC2136 Dynamic Update
protocol. Windows 2000 machines have a habit of sending dynamic update
requests to DNS servers without being specifically configured to do so. If
the update requests are coming from a Windows 2000 machine, see
http://support.microsoft.com/support/kb/articles/q246/8/04.asp for
information about how to turn them off.
```
Reference: [http://www.bind9.net/BIND-FAQ](http://www.bind9.net/BIND-FAQ)

---

