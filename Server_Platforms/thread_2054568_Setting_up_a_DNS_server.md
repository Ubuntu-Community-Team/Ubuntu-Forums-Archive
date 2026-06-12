---
title: "Setting up a DNS server"
date: 2012-09-07
forum: Server Platforms
---

### Post by Bcordrey on 2012-09-07
Hello,

I am new to using Ubuntu as a DNS solution, and need some assistance. I have a server with a public static IP that I would like to use as an authoritative nameserver for various domain I own, and a few clients' domains as well. I have a specific domain I am using to test with so I can get the DNS working; however, after following numerous tutorials, trying both BIND and PowerDNS, and reinstalling the OS at one point, I am still at square one. I have tried using the official Ubuntu documentation, as well. Is there a straightforward how-to on getting this accomplished? I am not new to Ubuntu, nor to linux in general, I have just never had to set up an authoritative nameserver before.

As an example of what is going on, when I get BIND or PowerDNS configured with the zones I need for the test domain, I can dig @localhost ns test.com and get an authroitative answer, but upon trying to point the ns to my server through my registrar I am told it is not a registered nameserver. I can't figure out where I'm going wrong.

I have currently uninstalled both PowerDNS and BIND, and would appreciate a BIND solution to this problem, as I will be using webmin.

Thank you for any assistance.

---

### Post by darkod on 2012-09-07
I never needed to set up bind so far, but I keep this link that looks very simple and easy:
[http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/](http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/)

---

### Post by Cheesemill on 2012-09-07
Also bear in mind that to meet the official requirements you need to set up 2 separate nameservers that use different IP addresses.

[http://www.iana.org/procedures/nameserver-requirements.html](http://www.iana.org/procedures/nameserver-requirements.html)

---

### Post by Bcordrey on 2012-09-07
Thanks for the replies. I think it's sorted now from the info. here.

---

