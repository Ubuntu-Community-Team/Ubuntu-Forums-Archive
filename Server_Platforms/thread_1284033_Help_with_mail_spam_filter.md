---
title: "Help with mail spam filter"
date: 2009-10-06
forum: Server Platforms
---

### Post by dragos2 on 2009-10-06
I deliver some email through Linux mail utility and the particular mail server that
holds the domains I send to rejects them as Spam based on this score:

```

   Content analysis details:   (6.5 points, 5.0 required)
   
   pts rule name              description
  ---- ---------------------- --------------------------------------------------
   0.9 RCVD_IN_PBL            RBL: Received via a relay in Spamhaus PBL
                              [x.y.z.w listed in zen.spamhaus.org]
   3.7 HELO_LH_HOME           HELO_LH_HOME
   1.9 DATE_IN_FUTURE_06_12   Date: is 6 to 12 hours after Received: date
  -0.7 BAYES_20               BODY: Bayesian spam probability is 5 to 20%
                              [score: 0.0581]
   0.1 RDNS_NONE              Delivered to trusted network by a host with no rDNS
   0.6 AWL                    AWL: From: address is in the auto white-list
  
```   
Why did it got 3.7 spam points for HELO_LH_HOME ?


Also how can I set date so it won't be in the future ?

---

### Post by dragos2 on 2009-10-07
Bump.

I fixed date in future and PBL, but I still don't know what

 [FONT=&quot]3.7 HELO_LH_HOME means[/FONT]

Any clues?

---

