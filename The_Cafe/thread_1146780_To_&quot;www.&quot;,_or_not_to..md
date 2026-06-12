---
title: "To &quot;www.&quot;, or not to."
date: 2009-05-02
forum: The Cafe
---

### Post by jamieh on 2009-05-02
Hi,

Should I keep my site at _www._mysite.com, or mysite.com?
Does the W3 have a standard, or does not really matter?

Thanks

---

### Post by lisati on 2009-05-02
I don't know if there is a standard, but I have noticed that for most of the sites I visit, I can leave off "www" quite safely, but with some, I need to put in the "www"

---

### Post by Saint Angeles on 2009-05-02
i assume you are talking about the setting in your .htaccess file that changes these kind of things (or is it php.ini?)

i think, and i could be wrong, but if you set it up so you don't NEED the www, it will still work with the [www..](www..). but i'm prolly wrong

---

### Post by jpmelos on 2009-05-02
The problem here is that your site won't be Search Engine Optimized. If you let users use both possibilities, then your traffic will be split in two different sites to the search engines. So the best thing is the use one of them to redirect the traffic to the other one, so both will work and you will get full traffic for one of them.

Well, I heard of this once, so I might be very wrong here. I would check this out more carefully.

Peace.

---

### Post by Peasantoid on 2009-05-02
Using "www." is stupid.

---

### Post by CharmyBee on 2009-05-02
yeah bring us back to keywords like AOL, prodigy and Compuserve

GO REDSOX

---

### Post by Kareeser on 2009-05-03
Appending the "www" subdomain to a domain name simply means you are asking the DNS server to redirect you to the server hosting that particular subdomain.

If the DNS server is not properly configured, [www.domain.com](www.domain.com) and domain.com will not go to the same place. That is, if the DNS forwards connections to "www", but not the empty subdomain, people accessing domain.com will not resolve.

Most DNS servers are configured to have both [www.domain.com](www.domain.com) and domain.com resolve to the same IP address, since everybody else configures their servers thusly.

So in essence, you could have a website at "www.domain.com" leading to your personal website, and "domain.com" leading to your business website, if you so wish.

I hope that clears that up.

---

### Post by -grubby on 2009-05-03
"www." is one of my pet peeves. Have the main site on site.com and have [www.site.com](www.site.com) just redirect.

---

### Post by Kareeser on 2009-05-03
> **nathangrubb said:**
> "www." is one of my pet peeves. Have the main site on site.com and have [www.site.com](www.site.com) just redirect.

Correct, that's what is usually done. www can be added as a CNAME record.

---

