---
title: "Do we need PSAD if we already have Fail2Ban?"
date: 2012-11-11
forum: Security
---

### Post by THPubs on 2012-11-11
I already have installed Fail2Ban on my server. I planned to install PSAD on it. Are they equal? Isn't it a good idea to keep them both?

---

### Post by THPubs on 2012-11-13
Any idea?

---

### Post by unspawn on 2012-11-13
> **THPubs said:**
> I already have installed Fail2Ban on my server.
Good choice.


> **THPubs said:**
> I planned to install PSAD on it. Are they equal? 
They are not. The PSAD web site tells you about its origin, its reason-for-being and how it implements things. Know that and you can determine if they are equal.


> **THPubs said:**
> Isn't it a good idea to keep them both?
Since you run a server look at what services you provide and how you have hardened them. Then look at what and how you audit for anomalies, errors and malicious activity. *Then* look at what the past and current "threatscape" tells you about how ninety nine per cent of (say web) servers get compromised. Putting that together should give you an idea of how reconnaissance, exploiting and aftermath should have been *detected* (and prevented or mitigated) at the network and the *application* level. 

Then ask yourself if your server would benefit from running a substitute (partial detection based on an approximation of part of the functionality something else provides, requiring three daemon processes, syslog-filling LOG target rules, doing NS and WHOIS requests for each alert sent and the constant "entertainment" of having to figure out what these email actually try to convey) instead of the functionality the original provides.

---

### Post by OpSecShellshock on 2012-11-13
Port scans are a part of life for systems open to the web. You don't need to be notified of them (unless you really, really want to). Limiting exposure with iptables is probably a better option than logging every possible port scan with PSAD.

Of the two, Fail2Ban is more valuable because it deals with access attempts.

---

### Post by unixfool on 2013-01-05
> **OpSecShellshock said:**
> 

Of the two, Fail2Ban is more valuable because it deals with access attempts.

PSAD can deal with access attempts as well (by blocking the attempts, an option that isn't set as default).  You can set this by enabling "ENABLE_AUTO_IDS" within the conf file.

---

