---
title: "Shorewall Firewall Setup?"
date: 2011-01-03
forum: Security
---

### Post by ryanteck on 2011-01-03
Hi guys
I got Shorewall firewall all Set-up perfect but I'm stuck at 1 last bit.
The aim is to let on 2 clients max onto my server.

i have the policy setup in webmin as.
[[IMG]http://img24.imageshack.us/img24/1174/fireaf.png[/IMG]](http://img24.imageshack.us/i/fireaf.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

More than 2 clients can get onto the server. the aim is to have it as a ddos protection allowing 100 clients on and a max burst of 10 clients at a time.

please help

thanks ryan walmsley

---

### Post by bodhi.zazen on 2011-01-03
That makes little or no sense.

If you wish to allow only 2 clients, then white list their IP addresses and block all others.

If you wish to allow only 2 total clients, you are easier to DOS as all it takes is 2 clients to block all other traffic.

There is no way to stop a DDOS, how can your server differentiate a needle in a hay stack ? Let us imagine you have 10,000 rquests for service from a DDOS and 100 legitiate requests, how do you identify the legitimate traffic ?

You can look at tools such a iptables:

[http://blog.bodhizazen.net/linux/prevent-dos-with-iptables/](http://blog.bodhizazen.net/linux/prevent-dos-with-iptables/)

although you should read the comments.

And you can install something such as mod_security and mod_evasive

---

### Post by ryanteck on 2011-01-03
the burst means amount of traffic at one time yes? if so a burst of over 50 should be known as a ddos...

---

### Post by bodhi.zazen on 2011-01-03
> **ryanteck said:**
> the burst means amount of traffic at one time yes? if so a burst of over 50 should be known as a ddos...

Apache can handle thousands of requests, 50 is a drop in the bucket. If your server can not handle a burst of 50 I would check the configuration.

By definition a ddos involves more then one source :

> Distributed Denial of Service (DDoS) attack is a DoS attack that occurs from more than one source, and/or from more than one location, at the same time.

[http://www.crime-research.org/articles/network-security-dos-ddos-attacks/](http://www.crime-research.org/articles/network-security-dos-ddos-attacks/)

Apache can handle thousands of requests / second, see:

[http://blog.bodhizazen.net/linux/optimize-wordpress-for-speed/](http://blog.bodhizazen.net/linux/optimize-wordpress-for-speed/)

Where I posted benchmarks. Benchmark your server.

> **Requests per second: 1942.31 [#/sec] (mean)**
Time per request: 5.149 [ms] (mean)
Time per request: 0.515 [ms] (mean, across all concurrent requests)
**Transfer rate: 18947.97 [Kbytes/sec]** received

Web servers are designed to receive thousands of requests.

If your network card / internet connection can not handle that, there is not much you can do other then upgrade the hardware or internet connection.

---

