---
title: "2 domains with different TLDs sites-enabled"
date: 2010-09-20
forum: Server Platforms
---

### Post by idalin on 2010-09-20
I am running an apache on Ubuntu.

I am running Virtual Hosts by creating conf-files in the sites-enabled directory and naming them:

domainname.tld

Now I have this problem.

I have a customer who has the same domain name with different tld's

hisdomain.dk
hisdomain.eu

And the sites are different.

I have a hisdomain.conf

But that means that both domains go to the dk-site :(

What do I do?

---

### Post by perspectoff on 2010-09-20
I'm not sure I understand your exact question, but check out:

[http://ubuntuguide.org/wiki/Apache2_reverse_proxies](http://ubuntuguide.org/wiki/Apache2_reverse_proxies)

or

[http://kubuntuguide.org/Apache2_reverse_proxies](http://kubuntuguide.org/Apache2_reverse_proxies)

and see if this is what you want to do.

---

### Post by Bachstelze on 2010-09-20
If you name the files [font=monospace]domain.tld[/font], why do you have a [font=monospace]domain.conf[/font]? You should have two files, [font=monospace]domain.dk[/font] and [font=monospace]domain.eu[/font].

---

