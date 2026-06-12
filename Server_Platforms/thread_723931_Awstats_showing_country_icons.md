---
title: "Awstats showing country icons"
date: 2008-03-14
forum: Server Platforms
---

### Post by tommytomato on 2008-03-14
Hi all

I've had awstats running for some time, seem to have no probs with it, how ever, I've decide to try and show my icons for the Countries table to see what countries are viewing our site in detail.

some how I cant seem to be able to get it going, am i doing some thing wrong ?, I followed what the link says here.

> Unique visitors and Number of visits available in Countries table
 Thanks to a contribution from Josep Ruano, it is now possible to see a breakdown of visits and unique visitors by country in the countries table. (AWStats 6.5+)

To enable extended country reporting, you must modify your awstats.mysite.conf configuration file, adding the letters U and V (users and visits) to ShowDomainsStats:

# Show domains/country chart
# Context: Web, Streaming, Mail, Ftp
# Default: PHB, Possible column codes: PHB
ShowDomainsStats=UVPHB

The change is retroactive and is effective immediately.


[http://www.antezeta.com/awstats.html](http://www.antezeta.com/awstats.html)

image on what it looks like if i get it going

[http://www.antezeta.com/i/awstats_6.5_visits_country.html](http://www.antezeta.com/i/awstats_6.5_visits_country.html)

I'm running Advanced Web Statistics 6.5 (build 1.857)

Can any one tell me what I'm doing wrong please.

```
# Show domains/country chart
# Context: Web, Streaming, Mail, Ftp
# Default: PHB, Possible column codes: PHB
#ShowDomainsStats=PHB
ShowDomainsStats=UVPHB
```

I've changed what it says to do then I ran 

```
/usr/local/awstats# ./awstats_updateall.pl now
```

TT

---

