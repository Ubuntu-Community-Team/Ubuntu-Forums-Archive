---
title: "Questions about DNS and E-mail servers"
date: 2011-08-06
forum: Server Platforms
---

### Post by spy_1134 on 2011-08-06
Hey guys, I have an Ubuntu 10.04.2 LTS Server Edition box running from a dynamic IP address.

I have been thinking about buying a domain name, probably from GoDaddy and having it direct to my server. I already have a DynDNS account and the updater client installed to the server to keep the IP current.

Could I just bounce my domain name off of the DynDNS URL? Or would I have to set up a DNS server? If I have to have a DNS server, how hard would it be to set up/maintain?

I have also been thinking of making the box host an e-mail server, but a lot of the documentation is out of date and leaves me with a bunch of errors. Does anyone have any up-to-date links, or could they walk me through it?

I'm sorry if this isn't the right place to post this, but I was unsure of what section to place this under.

Some more detailed info about the server:
Dell Optiplex GX620
Intel Pentium D dual core@2.8GHz
2GB of DDR2 RAM
150GB HDD
1Gbps Ethernet
Ubuntu Server Edition 10.04.2 64 bit

Thanks for any help guys. If you need more info just ask, I'll be checking back periodically.

---

### Post by spy_1134 on 2011-08-07
I went ahead and purchased a domain name from GoDaddy. They have their own DNS system that you could use, but I wanted more control over my name servers so I set up BIND as well. I used Webmin to change up my BIND zones for the website and everything is running smoothly.

I couldn't get the requests to forward to my DynDNS account though. So let's just hope that my dynamic IP address doesn't change too often 8-)

---

