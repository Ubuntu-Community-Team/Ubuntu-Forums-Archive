---
title: "/etc/hosts"
date: 2011-05-03
forum: Security
---

### Post by amalafrida on 2011-05-03
nope. still a problem. /etc/hosts blocks every site I put there but [www.iwsearch.net](www.iwsearch.net) ... just cannot find the combination to stop this crap from redirecting ...

any suggestions?

/etc/hosts/ contains these lines (among others)
0.0.0.0 [www.iwsearch.net](www.iwsearch.net)
0.0.0.0 ad.turn.com
attempt to open [www.iwsearch.net](www.iwsearch.net) should redirect to my default page, but does not
attempt to open ad.turn.com does redirect

got me over a log ...

any help will be much appreciated. i've worked at this for three days now and without success.

what surprises the hell out of me is the apparent absence of information on this problem with the search engines.

robert

---

### Post by bodhi.zazen on 2011-05-03
Try noscript =)

---

### Post by dfreer on 2011-05-03
Could the problem be that he's mapping them to the 0.0.0.0? Try 127.0.0.1 instead.

---

### Post by bodhi.zazen on 2011-05-03
> **dfreer said:**
> Could the problem be that he's mapping them to the 0.0.0.0? Try 127.0.0.1 instead.

either 0.0.0.0 or 127.0.0.1 will work in the hosts file to block. If the "home page" is a custom html or page locally, 127.0.0.1 is needed.

I suspect the OP is being re-directed by javascript or some such.

---

