---
title: "Is it possible to pass the GRC ShieldsUp test with an FTP+web server?"
date: 2009-11-23
forum: Security
---

### Post by KIAaze on 2009-11-23
Hi,

I just tried the [GRC ShieldsUp test]("http://www.grc.com") and it failed with:
> Solicited TCP Packets: RECEIVED (FAILED) &#8212; As detailed in the port report below, one or more of your system's ports actively responded to our deliberate attempts to establish a connection. It is generally possible to increase your system's security by hiding it from the probes of potentially hostile hackers. Please see the details presented by the specific port links below, as well as the various resources on this site, and in our extremely helpful and active user community.

Ping Reply: RECEIVED (FAILED) &#8212; Your system REPLIED to our Ping (ICMP Echo) requests, making it visible on the Internet. Most personal firewalls can be configured to block, drop, and ignore such ping requests in order to better hide systems from hackers. This is highly recommended since "Ping" is among the oldest and most common methods used to locate systems prior to further exploitation.


Open ports:
21 -> ftp
25 -> smtp
80 -> http
143 -> imap
443 -> https

Closed port:
113 -> ident

The rest is stealthed.

Since this is on a server offering http+https+ftp, is it even possible to pass the GRC ShieldsUP test?
Won't stealthing those ports prevent usage of the website and/or FTP server?

P.S.: Also, which is safer: stealthed or closed ports? closed would seem more logical, but I just want to be sure. :)

---

### Post by XCan on 2009-11-23
You could pass it by blocking off the ports in your firewalls, making them only accessible by authorized IPs. But if your servers are public, as you realized, you can't pass (according to their standards).

Stealth vs closed is a beat horse. People will tell you differently. Just go with either one and you should be fine.

---

### Post by KIAaze on 2009-11-23
Ok, thanks.

---

