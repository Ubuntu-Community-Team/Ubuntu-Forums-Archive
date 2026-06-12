---
title: "Setup static DNS server"
date: 2009-05-10
forum: Server Platforms
---

### Post by Bike-and-snow on 2009-05-10
Hello

I am trying to setup a "static" DNS server.

What I want to do is to create a server that offers the same functionality as /etc/hosts. For example:

```
mail.lan   192.168.0.10
files.lan  192.168.0.11
web.lan    192.168.0.12
```

At the moment we have lot's of servers (above is a simpified example) and they are listed in /etc/hosts on a lot of machines. And it's become unmanagable.

I've installed bind on a Ubuntu server. But I can't get my head around the syntax to add those static entries.

Should I continue with bind? If so does anyone know how to setup something really basic as my example above?

Thanks

---

### Post by NetworkGuy on 2009-05-10
BIND is the direction to go.

Look into using Webmin to setup your DNS server if you are having problems with the file(s) syntax.

---

### Post by capscrew on 2009-05-10
> **Bike-and-snow said:**
> Hello

I am trying to setup a "static" DNS server.

What I want to do is to create a server that offers the same functionality as /etc/hosts...

There are alternatives to bind.  Bind is WAY more complicated for what you seem to need.  Have a look at DNSmasq for your network. It uses a centralized /etc/hosts file for name mapping.  

It's a  lightweight DHCP/DNS server for local networks and will act as a DNS forwarder for Internet DNS requests.  In addition it will handle dynamic mapping for hostnames to DHCP IP addresses.

The main page for DNSmasq is [[COLOR="Blue"]**http://thekelleys.org.uk/dnsmasq/doc.html**[/COLOR]]("http://thekelleys.org.uk/dnsmasq/doc.html")

All the documentation is located at [[COLOR="Blue"]**http://thekelleys.org.uk/dnsmasq/docs/**[/COLOR]]("http://thekelleys.org.uk/dnsmasq/docs/")

Read the man page all the way through and very carefully. It is available at: [[COLOR="Blue"]**http://thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html**[/COLOR]]("http://thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html")

And of course there is Wikipedia's write up at: [[COLOR="Blue"]**http://en.wikipedia.org/wiki/Dnsmasq**[/COLOR]]("http://en.wikipedia.org/wiki/Dnsmasq")

---

### Post by Bike-and-snow on 2009-05-10
Thanks. DNSmasq looks perfect. I'll give that a go.

---

