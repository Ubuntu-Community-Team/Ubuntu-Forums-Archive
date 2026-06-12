---
title: "DNS bind9 configuration for alternate www port"
date: 2008-08-15
forum: Server Platforms
---

### Post by jucadizo on 2008-08-15
Hello

I'm trying to bypass the default port 80 for www and i'm not having success configuring the bind zone file:

This is what it looks like: 
$TTL 5d
@    IN    SOA    ns.mydomain.com  root.mydomain.com {
    2d
    2d
    2d
    2d
    2d }

       NS   ns.mydomain.com.
       MX   10 mail.mydomain.com.

       IN   A   10.0.0.1:8119
www    IN   A   10.0.0.1:8119
mail   IN   A   10.0.0.1


**** end of file**************

The port i'm trying to use for www is 8119 but this file is causing an error on /var/log/syslog that says:
"... bad dotted quad"

I also tried: 
"...   IN   A   10.0.0.1/8119"  but it didn't work

Does the zone configuration files accept specific ports for traffic redirection?
what else can I try?

thank you

---

### Post by windependence on 2008-08-16
You don't even need to be running your own nameserver. You are just complicating things. You can just have Apache listen on a different server, and then get yourself an account with no-ip.com. Point your domain at the account you created with them and then make the redirect point at your server:port. If you get the paid account for $25 a year, you can then mask the domain so no one would ever know that it is redirected. 

Most people running a single or a few web servers don't need to be running a DNS server or nameserver on their systems. Use your registrar's DNS and nameservers. In some cases your registrar can even mask the domain and point it right to your non-standard port.

-Tim

---

### Post by MJN on 2008-08-16
> **jucadizo said:**
> Does the zone configuration files accept specific ports for traffic redirection? what else can I try?DNS has no concept of ports. Your only option is to use an application-layer redirect as Tim mentioned (which, confusingly, come from DNS providers - but they're not actually using DNS to perform the redirect but rather a webserver sat on top of it).

Mathew

---

### Post by jucadizo on 2008-08-22
thank you guys
I'll try tio get the dns service outside to go around that port

---

