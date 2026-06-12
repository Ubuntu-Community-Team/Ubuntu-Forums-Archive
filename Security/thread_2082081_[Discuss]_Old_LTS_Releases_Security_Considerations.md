---
title: "[Discuss] Old LTS Releases: Security Considerations"
date: 2012-11-08
forum: Security
---

### Post by teward on 2012-11-08
So, what're the security concerns/considerations of using old LTS releases (8.04 for example, since at post-time that was the oldest still-supported LTS)?

I'm looking to get a semi-exhaustive list, but that by no means ensures it'll be 100% complete.

---

### Post by cwsnyder on 2012-11-08
8.04 Hardy Heron would still get its security updates backported, that is almost the definition of remaining under support.  6.06 Dapper Drake would not.

You would actually be *less likely* to have application security problems, because most of the bugs would have been swatted, in comparison of 8.04 Hardy Heron to 12.04 Precise Pangolin.  You would be running older copies of the software, so feature-wise, you may be missing something, but you would not be running software which is any older than Debian old-stable (4.0 Woody), and not as old as some applications in RHEL 5, which is still supported by Red Hat.  Debian Woody is still running on some servers.

For security purposes, an older LTS version is often to be preferred to a newer LTS or non-LTS version.

---

### Post by teward on 2012-11-08
> **cwsnyder said:**
> 8.04 Hardy Heron would still get its security updates backported, that is almost the definition of remaining under support.  6.06 Dapper Drake would not.

You would actually be *less likely* to have application security problems, because most of the bugs would have been swatted, in comparison of 8.04 Hardy Heron to 12.04 Precise Pangolin.  You would be running older copies of the software, so feature-wise, you may be missing something, but you would not be running software which is any older than Debian old-stable (4.0 Woody), and not as old as some applications in RHEL 5, which is still supported by Red Hat.  Debian Woody is still running on some servers.

For security purposes, an older LTS version is often to be preferred to a newer LTS or non-LTS version.

What about CVE bugs?  For something, such as Apache, its CVE bugs would only be backported/applied to Hardy if the severity is high or critical, according to what mdeslaur (IRC name) of the Security Team said to me...

---

### Post by cwsnyder on 2012-11-08
I am not a security expert, nor a sysadmin, I just follow a few discussions around the web on security.

That said, if it is a security vulnerability, that pushes it to a high priority.  It is other types of bugs which don't necessarily get fixed.

---

