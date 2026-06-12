---
title: "Detect DNS used by a client"
date: 2009-03-16
forum: Server Platforms
---

### Post by Clodo_zz on 2009-03-16
I need to detect what DNS Server are in using by a client.

There are many web sites that show the client IP.
I found only one web-site that show also the client DNS (now offline), and i'm trying to understand how-to.

A friend suggest me this way:
- Configure bind9 on your domain.
- Ask to client to ping an address "<clientip>.mydomain.net".
- Check the server log.

It's right? Some other suggestions?
Thanks!

---

### Post by Clodo_zz on 2009-03-16
I'm trying to explain well my project. Sorry for my english.

In Italy we have our ISP that have weight blacklist on domains resolution.
Also, different ISP have very different blacklist.

For example, img5.imageshack.com are blocked (DNS redirect to 127.0.0.1) from some ISP.
Cigarettes online-store are blocked.
Thousand of domain relative to bet & poker are blocked from an organization called AAMS.
Some P2P forum are blocked (for example, piratebay.org for a couple of month).

For that, i write a "net neutrality monitor": friends from different ISP launch a probe-program (in c++) that test DNS resolution of our ISP and send to me the results.

I wrote all, only DNS detect used by the probe are missing now.
Before, i parse an external URL that dump this information, but now it's off-line, and i'm looking for an affidable solution.

Thanks for reading that!

---

### Post by hyper_ch on 2009-03-17
you want to find out what dns server a specific client queried in order to get a domain name resolution?

---

### Post by Clodo_zz on 2009-03-17
> **hyper_ch said:**
> you want to find out what dns server a specific client queried in order to get a domain name resolution?
Yes, thanks.
I know that i can have different results, for example from cache server; after, with a querying to RIPE for each IP detected, i group the results by ISP.

---

### Post by hyper_ch on 2009-03-17
unless the clients won't tell you what dns servers they queried you can't find out.

---

### Post by Clodo_zz on 2009-03-17
> **hyper_ch said:**
> unless the clients won't tell you what dns servers they queried you can't find out.
In this page:
[http://private.dnsstuff.com/tools/aboutyou.ch](http://private.dnsstuff.com/tools/aboutyou.ch)
about a week ago, the lastest raw was "Your DNS Server:".
And work perfectly.
I also trying to use OpenDNS or other DNS Server, and the page reflect the correct information.
I'm trying to understand how they do that.
I don't know why there isn't available now.

---

### Post by askreet on 2009-03-17
In theory, it's not possible to determine what DNS server they used to obtain your IP.

---

### Post by Clodo_zz on 2009-03-17
> **askreet said:**
> In theory, it's not possible to determine what DNS server they used to obtain your IP.
Thanks for feedback!

Sorry, maybe i don't know very well how DNS works.
If i ask a client to reach an inexistent third-level domain, for example "213_21_43_24.mydomain.net", and i have the second-level domain "mydomain.net", the DNS server of the client ask to my domain (authoritive?) how to resolve, right?
If i log this query, i can associate the client IP (213.21.43.24) to the DNS server that he use (by logging who ask to my server to resolve "213_21_43_24.mydomain.net").
I don't know if this is an applicable way... this is the suggestion that some other people give to my problem.
Actually, i'm trying to test this way, for this reason i'm here in this forum.

---

### Post by askreet on 2009-03-18
Actually, that's quite ingenious, and sound like it would work.  You would just need a script to be watching for failed DNS requests.

---

