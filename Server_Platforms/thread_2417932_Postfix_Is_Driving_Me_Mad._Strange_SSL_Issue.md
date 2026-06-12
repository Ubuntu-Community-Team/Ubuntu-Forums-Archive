---
title: "Postfix Is Driving Me Mad. Strange SSL Issue"
date: 2019-04-29
forum: Server Platforms
---

### Post by marwan832 on 2019-04-29
Hi all,

I'm coming here after I have exhausted all my trials solving this. So I hope someone helps or something.

I have an Ubuntu server running Postfix. I'm using letsencrypt SSL for both incoming and outgoing. I have multi-domains and all these domains are covered in the SSL. Lately, Outlook and Thunderbird started to complain about the "reality" of the SSL. Most probably Postfix and Dovecot are serving the self signed SSL. But, I'm sure all is good. I run the SSL test and I get everything is perfect. But still, mail clients are complaining.

Any suggestions?

---

### Post by dolios on 2019-04-29
> **marwan832 said:**
> Hi all,

I'm coming here after I have exhausted all my trials solving this. So I hope someone helps or something.

I have an Ubuntu server running Postfix. I'm using letsencrypt SSL for both incoming and outgoing. I have multi-domains and all these domains are covered in the SSL. Lately, Outlook and Thunderbird started to complain about the "reality" of the SSL. Most probably Postfix and Dovecot are serving the self signed SSL. But, I'm sure all is good. I run the SSL test  and I get everything is perfect. But still, mail clients are complaining.

Any suggestions?

Do you mean complaining as in the SSL is not trusted? And it has worked before, but suddenly they just started to complain?

---

