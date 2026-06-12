---
title: "Domain name forward to specific server port"
date: 2011-06-22
forum: Server Platforms
---

### Post by inadaze on 2011-06-22
Hello,
I have just setup my ubuntu 10.04 DNS server with a service provide who blocks port 80.  I was wondering if I had other options than using an external service that takes my domain name and forwards it to my server ip and specific port.  Ultimately I would like mydomain.com to open myserver.mydomain.com:8080.  

Is there a way to do this with apache proxy or modifying my bind9 zone configuration to point [www.mydomain.com](www.mydomain.com) to 192.168.0.1:8080?

---

### Post by ruffEdgz on 2011-06-22
DNS doesn't usually worry about ports. The only think DNS worries about is a name and an IP.

If you want 'http://www.mydomain.com' to move to another point like 8080, you will need to make some changes to you apache configurations to:
[list]
[*]Have an html redirect point to mydomain.com:8080 ([http://www.instant-web-site-tools.com/html-redirect.html](http://www.instant-web-site-tools.com/html-redirect.html))
[*]Have a apache 301 redirect ([http://httpd.apache.org/docs/2.0/mod/mod_alias.html](http://httpd.apache.org/docs/2.0/mod/mod_alias.html))
[*]Have iptables take any port 80 traffic and direct it to port 8080 ([http://phpbugs.wordpress.com/2010/07/23/port-redirection-with-iptables-from-port-80-to-8080/](http://phpbugs.wordpress.com/2010/07/23/port-redirection-with-iptables-from-port-80-to-8080/))
[/list]
I hope that points you in the right direction but if you need more information on anything in particular, the forum should be able to help.

Cheers!

---

### Post by inadaze on 2011-06-22
Thanks for the links!  But I am curious how my service provider blocks port 80.  Does my server still get requests for port 80 so that my server could redirect them or are requests for port 80 blocked before they even get to my server?

---

### Post by doas777 on 2011-06-22
> **inadaze said:**
> Thanks for the links!  But I am curious how my service provider blocks port 80.  Does my server still get requests for port 80 so that my server could redirect them or are requests for port 80 blocked before they even get to my server?
the latter.

---

### Post by Corlis on 2011-06-22
You can check, if you have installed apache on your server, using

```

telnet YOURHOST 80

```

If you don't get anything or the connection times out, it most likely is the case, that your SP blocks access to your hosts IP Port 80. Then you cannot help your cause with any modifications on your server. The only thing is some kind of forwarding-service that allows you to switch ports, or that the company you bought your domain has a versatile backend where you can do such kind of modifications.

---

### Post by doas777 on 2011-06-22
your best bet to test whether tcp\80 traffic is blocked by upstream devices, is to use 
[http://canyouseeme.org/](http://canyouseeme.org/)
to test port 80. if it can't see the port, but telnet can (see Corlis' last post), then they are blocking 80 traffic entering their network, and you will have to get creative.

---

### Post by inadaze on 2011-06-22
Looks like that is the case.  Can anyone suggest a good forwarding service that would allow me to set users who type [www.mydomain.com](www.mydomain.com) to open mydomain.com:8080?

---

### Post by doas777 on 2011-06-22
looks like DynDNS has a URL forwarder service that will do it (at least per their support page)
[http://www.dyndns.com/services/webredirect/](http://www.dyndns.com/services/webredirect/)

---

