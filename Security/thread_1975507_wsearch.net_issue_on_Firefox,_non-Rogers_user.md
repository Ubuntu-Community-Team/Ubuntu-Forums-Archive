---
title: "wsearch.net issue on Firefox, non-Rogers user"
date: 2012-05-07
forum: Security
---

### Post by wandawanderer on 2012-05-07
When I search for something on the address bar or open some YouTube links, I am redirected to wsearch.net instead, which looks like a malicious site. I went through older posts about this but they seemed to affect Rogers users and the solutions also seemed to be for those users as well.

I'm in Thailand and not a Rogers user. Anyone has an idea of a solutions for me?

OS: Ubuntu 10.04 LTS
Browser: Firefox 12.0 (just removed older version and re-installed)

---

### Post by CharlesA on 2012-05-07
When did this start happening?

Have you tried using different DNS servers?

I've been using 8.8.8.8 and 8.8.4.4

---

### Post by OpSecShellshock on 2012-05-07
From what I've been able to find it appears to be integrated into certain types of network hardware, used on multiple ISPs. Changing DNS settings does indeed appear to be the way to fix it.

Have you recently gotten new hardware or services from your ISP?

---

### Post by CharlesA on 2012-05-07
> **OpSecShellshock said:**
> From what I've been able to find it appears to be integrated into certain types of network hardware, used on multiple ISPs. Changing DNS settings does indeed appear to be the way to fix it.

I had a similar thing happen with my ISP as well - they were doing DNS hijacking to redirect search bar searches to their search engine instead of the one I picked.

Changing DNS fixed that.

---

### Post by OpSecShellshock on 2012-05-07
> **CharlesA said:**
> I had a similar thing happen with my ISP as well - they were doing DNS hijacking to redirect search bar searches to their search engine instead of the one I picked.

Changing DNS fixed that.

Yes, unfortunately it's a thing they do. They strike deals with companies that sell ad space on landing pages and then when someone types a domain that doesn't exist or spells it incorrectly the user gets redirected instead of getting the response dictated by web standards. Apparently some hardware manufacturers wanted in on the deal as well. Shame.

---

### Post by CharlesA on 2012-05-07
> **OpSecShellshock said:**
> Yes, unfortunately it's a thing they do. They strike deals with companies that sell ad space on landing pages and then when someone types a domain that doesn't exist or spells it incorrectly the user gets redirected instead of getting the response dictated by web standards. Apparently some hardware manufacturers wanted in on the deal as well. Shame.
Indeed. Such a shame.

Anything to make a buck.

---

### Post by wandawanderer on 2012-05-08
Changed DNS settings, shut down, waited for a while and started the laptop again. That did solve my problem. Thank you very much -- you guys rock! :guitar:

---

