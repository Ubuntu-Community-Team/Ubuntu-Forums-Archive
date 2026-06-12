---
title: "Package authentication from country mirrors"
date: 2008-06-06
forum: Security
---

### Post by todb on 2008-06-06
After upgrading from Gibbon (7.10) to Heron (8.04), I started getting socked with the following warnings from apt-get on all new packages:

```
WARNING: The following packages cannot be authenticated!
```

Prior to the upgrade, I had set up my sources list (/etc/apt/sources.list) to point to the UK country mirrors -- [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) and friends.

I edited my sources.list to remove the "uk." subdomain, ran apt-get update, re-added my uk. subdomains, ran apt-get update again, and the problem went away.

Since I wasn't doing any special logging at the time, and since /var/log/apt/term.log and /var/log/dpkg.log are both unhelpful, I'm not sure why this worked.

I presume that I have good keys now since swinging by the "main" archive, and my future apt-gets will not be backdoored full of evil. But that's kind of a leap of faith at the moment. 

If you have an idea as to why this solved my issue, I'd love to hear it. I clearly have an imperfect understanding of the mirror-ness of the country mirrors, and how initial and subsequent key verification works.

At any rate, I'm posting this because the whole episode has made me fairly nervous in light of the recent openssl debian debacle.

TIA.

---

