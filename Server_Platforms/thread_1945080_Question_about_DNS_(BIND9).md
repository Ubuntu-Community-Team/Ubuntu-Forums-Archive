---
title: "Question about DNS (BIND9)"
date: 2012-03-22
forum: Server Platforms
---

### Post by darkod on 2012-03-22
Hi all.

I am setting up (playing around) an Ubuntu Server 10.04 LTS to be firewall with routing capabilities.

I have managed to do that (so far), but I got stuck at one point. The DNS.

I installed bind9 and I only activated the forwarders part entering the ISP DNS servers. My server has two network ports, using them as the external and internal interface.

The routing is set up good I believe. If I ping 8.8.8.8 from a server on the internal network using this 10.04 as gateway, it works. But if I ping [www.google.com]("http://www.google.com") it doesn't resolve the name.

Was I under the wrong impression that the caching nameserver will pass on the queries? Do I need to set it up as Master with the zones files?

In the firewall (ufw) all traffic originating from inside is accepted by default, but just in case I allowed 53/tcp. So it should not be a firewall problem.

If I do a dig from the server is resolves the google.com. It seems it's something to do with passing the queries between the ext and int interface, if this can be done at all.

Thanks a lot for any ideas.

EDIT: To clarify further for people who know more. :) I do not want to set up my own dns server for my own domain, etc. All I want is this server with a public IP on one interface, and private IP 10.0.0.8 on another interface, to pass on the dns information to computers on the internal network.

Right now if I put 10.0.0.8 as only dns server on one computer on the internal network, it doesn't resolve.

I was under the impression that for this function, I only have to use the forwarders section where I enter the ISP dns servers and that's it.

---

### Post by Bachstelze on 2012-03-22
You also need to allow clients to query your server. Typically you would have something like

```
allow-recursion { 192.168.0.0/24; };
```

in the options block in named.conf.options.

---

### Post by Cheesemill on 2012-03-22
If you are looking to just set up DNS caching you could look at dnsmasq, it's a lot more user friendly than BIND.

If you already have /etc/resolv.conf set up on your server then it needs no configuration at all.

---

### Post by darkod on 2012-03-22
> **Cheesemill said:**
> If you are looking to just set up DNS caching you could look at dnsmasq, it's a lot more user friendly than BIND.

If you already have /etc/resolv.conf set up on your server then it needs no configuration at all.

The server is at work so I can try the allow-recursion tomorrow.

When you say /etc/resolv.conf on your server, you mean the firewall/gateway/dns server, or the server on the internal network? Because if we are talking about the internal network the machines will be windows only.

If you are talking about the dns server, what do I need to put in resolv.conf, the ISP DNSs?

---

### Post by Cheesemill on 2012-03-22
> **darkod said:**
> If you are talking about the dns server, what do I need to put in resolv.conf, the ISP DNSs?

Yep.

dnsmasq will use these IP's instead of having to edit a config file as with BIND.

The easiest tutorial I've found about dnsmasq is this one.
[http://wiki.debian.org/HowTo/dnsmasq](http://wiki.debian.org/HowTo/dnsmasq)

---

### Post by darkod on 2012-03-22
> **Cheesemill said:**
> Yep.

dnsmasq will use these IP's instead of having to edit a config file as with BIND.

The easiest tutorial I've found about dnsmasq is this one.
[http://wiki.debian.org/HowTo/dnsmasq](http://wiki.debian.org/HowTo/dnsmasq)

So, if I go this way, should I do something like:
sudo apt-get remove --purge bind9

or leave bind as it is?

---

### Post by |{urse on 2012-03-22
Yes, remove Bind first, I've made that mistake and ended up with borked dns.

---

### Post by darkod on 2012-03-23
> **Cheesemill said:**
> Yep.

dnsmasq will use these IP's instead of having to edit a config file as with BIND.

The easiest tutorial I've found about dnsmasq is this one.
[http://wiki.debian.org/HowTo/dnsmasq](http://wiki.debian.org/HowTo/dnsmasq)

I did this but no luck.

The ISP nameservers were already in /etc/resolv.conf because I entered them during the ubuntu installation.
I purged bind9 and installed dnsmasq, told it to listen to eth1 as in the tutorial, checked that the dhcp part is disabled (don't want it issuing IPs), restarted the whole server.

I have ping [www.google.com]("http://www.google.com") on this server.

On a computer on LAN eth1 ping [www.google.com]("http://www.google.com") doesn't work if this server is the DNS.

Any possible connection with ufw? But if I use another DNS on the same internal computer, it works. So I don't think ufw is blocking me since it wouldn't work for any DNS server.

EDIT: The only possibility for a problem is the fact that I have two interfaces. Not sure if I'm doing it right. So, the bottom line is:
eth0 with public IP, public gateway, ISP nameservers
eth1 with private 10.0.0.8, no gateway
ufw set to ACCEPT forwarding, routing configured correctly it seems

I want this server to be DNS for computers connected to eth1, the private network. I am trying to use 10.0.0.8 as DNS but doesn't work.

Any ideas?

EDIT2: At the end of the day, this is not a huge problem. Only a few servers will be connected to this private interface and as servers they will all have static IPs. Instead of using 10.0.0.8 as dns I can simply use the ISP nameservers. That works, I have tried it.

But setting this forwarding dns seems pretty straightforward and it got me puzzled what am I doing wrong. Knowledge for the future. :)

---

### Post by darkod on 2012-03-23
Got it. I'm officially an idiot. :)

Wasn't aware that dns issues traffic to UDP also. I had ufw enabled with 53/tcp rule. Once I deleted that and did it only as 53 (to accept both protocols), it works with 10.0.0.8 as dns.

---

### Post by Cheesemill on 2012-03-23
Glad you got it sorted.
It's always the simple things isn't it :)

---

