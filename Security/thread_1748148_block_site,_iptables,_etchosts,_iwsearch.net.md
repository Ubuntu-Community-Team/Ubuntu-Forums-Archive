---
title: "block site, iptables, etc/hosts, iwsearch.net"
date: 2011-05-03
forum: Security
---

### Post by amalafrida on 2011-05-03
I've tried everything I can come up with to block [www.iwsearch.net](www.iwsearch.net). Nothing works.

edited /etc/hosts
edited /etc/hosts.deny
set iptables ... 

adblock plus will not stop it ... curious that there is very little known about this site in all the search engines.

any suggestions?

at my wits end.

thanks in advance for any help proffered.

robert

---

### Post by amalafrida on 2011-05-03
nope. seems to be working now in /etc/hosts/ ... my entry was too specific ... should have been simply iwsearch.net not [www.iwsearch.net](www.iwsearch.net)

thanks for your patience.

robert

---

### Post by Hugh Buntu on 2011-11-17
redirection to infoweb.net (iwsearch.net) usually happens for one of two reasons:

(1) Fat-fingering Firefox w/ enter and shift at the same time

(2) DNS misconfiguration where ".net" gets added onto the end of a domain

Example for #2: enter the following into your browser:
[INDENT][INDENT][INDENT][INDENT][http://ubuntoid.com.net](http://ubuntoid.com.net)
[/INDENT][/INDENT][/INDENT][/INDENT]This will return search results for the search term "ubuntoid"

I like it better than a 404 page, YMMV

:-({|=Making a change in /etc/hosts, jumping to the conclusion it's a virus, screwing around with iptables, or self-inducing a panic-attack generally will likely cause new problems, not fix anything. Fixing your typing or DNS config might. 

Hope this helps. ):P

Hugh

---

