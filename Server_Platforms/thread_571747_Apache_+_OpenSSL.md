---
title: "Apache + OpenSSL"
date: 2007-10-09
forum: Server Platforms
---

### Post by stuffradio on 2007-10-09
I want to install and configure OpenSSL properly. Is there a howto guide?

---

### Post by MJN on 2007-10-09
Many (which can be a good *and* bad thing!)

The one I've always referred to is somewhat of a classic in my book - first used it a few years back with RedHat and it's still a useful reference for me even now:

[http://www.vanemery.com/Linux/Apache/apache-SSL.html](http://www.vanemery.com/Linux/Apache/apache-SSL.html)

(you can finish at Step 5 although the rest, particularly the removal of the server key passphrase, may be of interest)

I'm sure there are other worthwhile recommendations, perhaps being more Ubuntu-specific (that HowTo suffices, but there may be subtle difference like Apache2 not using httpd.conf etc on Ubuntu). I'd certainly recommend using a guide that teaches you what's happening at each step, and why, as I feel it's just a waste blindly following a series of commands - the lack-of-knowledge from doing so only comes back to haunt you (and the rest of us on the forums!) ;)

Good luck,

Mathew

P.S. If you're after a recognised CA to sign your certificate (i.e. not self-signing) I can certainly recommend RapidSSL's Equifax root - I've got a URL buried somewhere to enable you to get these for $15/yr which has to be the cheapest trusted single-root certificate around (unless someone knows of a cheaper one?)

P.P.S. In view of the above I've just checked out RapidSSL's site out and found they have what looks like a good Apache SSL guide - [http://www.rapidssl.com/resources/pdfs/apache_white_paper_v1.01.pdf](http://www.rapidssl.com/resources/pdfs/apache_white_paper_v1.01.pdf) - ignoring the obvious sales speak it seems to cover all aspects from theory through to actual implementation.

---

