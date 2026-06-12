---
title: "DNS Name blocking security isn't enough"
date: 2020-09-02
forum: Security
---

### Post by TheFu on 2020-09-02
Attackers abuse Google DNS over HTTPS to download malware
[https://www.bleepingcomputer.com/news/security/attackers-abuse-google-dns-over-https-to-download-malware/](https://www.bleepingcomputer.com/news/security/attackers-abuse-google-dns-over-https-to-download-malware/)

They are embedding the IPs for C&C servers a few levels deep now. The normal dns name filters, as provided by a pi-hole setup, aren't effective when these new techniques are used.  Attackers are hiding IP addresses in other payloads as decimal numbers. These decimal numbers  can be used in web browsers just like IP addresses.  

Automated security network scanners don't see these things, yet. May never.

The security chess match continues.

---

### Post by EuclideanCoffee on 2020-09-02
Wow, that's insane. But I wasn't sure how the attack could be deployed. Hacker news comments helded out.

[https://news.ycombinator.com/item?id=24354453](https://news.ycombinator.com/item?id=24354453)

> 

TFA doesn't explain correctly or adequately what's going on. no wonder there's no comments yet.attackers  put their data as txt records in DNS. victim needs to already otherwise  have the first-order payload installed and running. it (the malware)  queries DNS for C&C or 2nd stage payload location. the point of  using DOH is that IDS systems can't see inside it. In theory, anyone  deploying IDS should be MITM HTTPS anyway, so this data should be  inspectable.
Basically it's IDS avoidance. You must already be infected.
For most users, most orgs, it doesn't matter. Regular DNS would have been fine. I doubt orgs are filtering DNS TXT responses.
It would be interesting to learn from Kaspersky, eset, etc how effective this attack is.               



Something to keep an ear on, I guess. Thanks for the post.

---

### Post by kevdog on 2020-09-23
So don't use Google DOH then?  Just curious if this were an option.

---

