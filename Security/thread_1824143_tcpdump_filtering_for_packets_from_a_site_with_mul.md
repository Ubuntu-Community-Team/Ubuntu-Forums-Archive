---
title: "tcpdump: filtering for packets from a site with mulitple ip addresses?"
date: 2011-08-13
forum: Security
---

### Post by ltwinner on 2011-08-13
I want to capture all packets from site "www.examplesite.com" so I checked its ip address in an ip address look up and it was 123.456.abc.def.

So I set my filter to "dst host 123.456.abc.def"

However I then realised that multiple ip address point to [www.examplesite.com]("http://www.examplesite.com"), for example say the following ips also go to [www.examplesite.com]("http://www.examplesite.com")
987.654.321.000
111.222.333.444

So is there a filter that will automatically capture all traffic going to [www.examplesite.com]("http://www.examplesite.com") or do I have to go and manually find all it's ip addresses and pass them all to the filter?

---

### Post by Kinstonian on 2011-08-13
Try "dst host www.examplesite.com"

---

### Post by ltwinner on 2011-08-13
Will that capture all packets going to [www.examplesite.com?](www.examplesite.com?) Or does it just take the first ip address it finds for [www.examplesite.com](www.examplesite.com) and uses that for capturing? I need to be sure it captures all packets going there?

---

