---
title: "blocking a country's or ISP's IP address"
date: 2009-10-27
forum: Security
---

### Post by nhasian on 2009-10-27
last week my shopping cart started getting fraudulent credit card orders.  the bill to & ship to addresses are always in the US, however the credit card numbers are always different.  looks like this hacker always comes to my website from [www.google.com.ng](www.google.com.ng) so far the IP addresses I've blocked are:

41.219.200.245
41.219.225.108
41.219.230.209

See the common pattern?  Should I just block 41.219.*.* ?  How can I see what countries or ISPs it will affect?  according to [http://www.ip-adress.com/ip_tracer/](http://www.ip-adress.com/ip_tracer/) all of those IPs belong to Starcomms Nigeria.
Is it possible to block the entire country of Nigeria?  Or just that particular ISP?  Please advise.

---

### Post by lovinglinux on 2009-10-27
Use [moblock](http://moblock-deb.sourceforge.net/) with a [country ip list](http://www.countryipblocks.net/).

---

### Post by Soul-Sing on 2009-10-28
: [http://iplist.sourceforge.net/start.html](http://iplist.sourceforge.net/start.html)
iplist blocks ip-ranges and countries.

---

### Post by Sarmacid on 2009-10-28
I'd suggest taking a different approach than blocking all of those IPs. If the stuff is being mailed to the US then it's very likely the attacker is just using proxy servers, and if that country is banned, he'll move on to the next one.

---

### Post by nhasian on 2009-10-28
I would be happy to block anonymous proxy servers as well. :)

---

### Post by lovinglinux on 2009-10-28
> **nhasian said:**
> I would be happy to block anonymous proxy servers as well. :)

[http://iblocklist.com/list.php?list=bt_proxy](http://iblocklist.com/list.php?list=bt_proxy)

Other lists [http://iblocklist.com/lists.php](http://iblocklist.com/lists.php)

---

### Post by Lars Noodén on 2009-10-28
> **nhasian said:**
> last week my shopping cart started getting fraudulent credit card orders.  the bill to & ship to addresses are always in the US, however the credit card numbers are always different.  looks like this hacker always comes to my website from [www.google.com.ng](www.google.com.ng) so far the IP addresses I've blocked are:

41.219.200.245
41.219.225.108
41.219.230.209

See the common pattern?  

You can block the range.  Find the range with [whois](http://manpages.ubuntu.com/manpages/karmic/en/man1/whois.1.html)

[FONT="Courier New"][INDENT]$ whois 41.219.200.245;
...
inetnum:        41.219.225.0 - 41.219.225.255
...[/INDENT][/FONT]

There's a contact there to lodge a complaint with.

---

