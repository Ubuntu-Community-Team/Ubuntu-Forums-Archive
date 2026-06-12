---
title: "Virtual domain setup not working"
date: 2013-05-10
forum: Server Platforms
---

### Post by mcraul on 2013-05-10
So I want to host a domain on an Amazon EC2 server that's running Ubuntu 10.04.1 with Webmin version 1.620 running on top of that. 
I made a virtual domain using the apache interface on Webmin and made sure Apache was listening on port 80.
I then restarted apache to save that.

I then decided to use the Amazon route 53 DNS server and added the dns servers to my domain at my registrar and then adjusted the A record to point to the server ip address.
So so far so good, at least I think.

I then waited 24 hours for all that to route out and tested it.

And its not routing. I dont know why its not and I thought I had everything setup correctly.

Maybe I missed a step?  I put  the domain files here 

Server Name localhost
Document Root /var/www/xxlito


Any ideas or thoughts?

When I Ping it the ip address of the server comes up but does not route

C:\Users\raul>ping xxulito.net

Pinging xxulito.net [50.112.xx.xxx] with 32 bytes of data:
Request timed out.
Request timed out.
Request timed out.
Request timed out.

Ping statistics for 50.112.xx.xxx:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),



Thanks!

---

### Post by snathan99 on 2013-05-13
Before you go DNS, you will need to figure out how to get a response to tcp/ping.  Use 
```

telnet <ip> 80

```
for checking if machine is listening on port 80.  Proceed from there to figure out apache issues followed by DNS issues.  If you cannot get the actual routing itself (to the virtual server) you will need to contact Amazon.

---

### Post by SeijiSensei on 2013-05-13
Well, let's start with a basic problem:

```

$ whois xxulito.net

Whois Server Version 2.0

Domain names in the .com and .net domains can now be registered
with many different competing registrars. Go to http://www.internic.net
for detailed information.

No match for "XXULITO.NET".

```

You have not registered this domain with a registrar.  I use [DirectNIC]("http://www.directnic.com/") myself, but there are many, many others.

Even if the domain were registered and configured with an "A" record to point the name xxulito.net to your IP address, your server configuration has
```

ServerName localhost

```
You would need a server configuration with
```

ServerName xxulito.net

```
that points to the /var/www/xxulito directory.  I'd add a "ServerAlias www.xxulito.net" directive to that configuration as well.

---

