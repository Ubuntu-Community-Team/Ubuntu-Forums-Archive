---
title: "Forward DNS using DNSmasq or Bind"
date: 2014-10-27
forum: Server Platforms
---

### Post by jon70 on 2014-10-27
Hi guys,
I have a server set up with webmin and I am trying to configure bind or dnsmasq to resolve a subdomain.

I would like to have for example the subdomain ddns.example.com, within this I would like to create a subdomain from this for my users:

for example ddns.example.com will hit my server
bob.ddns.exmaple.com will hit bobs ip say 80.154.121.111

I have managed to set this up with dnsmasq, but only when pinging on the server itself, not form outside.

What is the best way to achieve this using bind or dnsmasq? Also if Bind is the way to go, are you actually able to add a master zone for a subdomain as this seems to fail for me.

Please also see this post for more information of my issue:
[http://serverfault.com/questions/639992/dns-bind-webmin-forward-dns-requests-for-subdomain](http://serverfault.com/questions/639992/dns-bind-webmin-forward-dns-requests-for-subdomain)

Many thanks for any help

---

### Post by koenn on 2014-11-03
use dnsmasq, it's simple
you can use your server's /etc/hosts file ad address database. Just add what's needed. (There are other files you can use if you wnt, read the comments in dnsmasq.conf)

You do understand that for a DNS server to work, it needs to be accessible by its clients, don't you ?

---

### Post by sandyd on 2014-11-04
> **jon70 said:**
> Hi guys,
I have a server set up with webmin and I am trying to configure bind or dnsmasq to resolve a subdomain.

I would like to have for example the subdomain ddns.example.com, within this I would like to create a subdomain from this for my users:

for example ddns.example.com will hit my server
bob.ddns.exmaple.com will hit bobs ip say 80.154.121.111

I have managed to set this up with dnsmasq, but only when pinging on the server itself, not form outside.

What is the best way to achieve this using bind or dnsmasq? Also if Bind is the way to go, are you actually able to add a master zone for a subdomain as this seems to fail for me.

Please also see this post for more information of my issue:
[http://serverfault.com/questions/639992/dns-bind-webmin-forward-dns-requests-for-subdomain](http://serverfault.com/questions/639992/dns-bind-webmin-forward-dns-requests-for-subdomain)

Many thanks for any help
If you set the domain as local in dnsmasq (i.e. local=/ddns.example.com/), dnsmasq should use the DHCP hostnames as part of resolution. That is, assuming that you can switch (or are using) dnsmasq as the DHCP server.

For example, a computer named "adrainie" should be pingable by "adranie.ddns.example.com".

---

