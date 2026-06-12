---
title: "libxml2 buffer overflow"
date: 2012-11-29
forum: Security
---

### Post by joelolson on 2012-11-29
After upgrading to the latest package (2.7.8.dfsg-4ubuntu0.4) our Cisco ISP is still generating buffer overflow vulnerability warnings for libxml2.

Here is the signature name from the report...

*XML Long Entity Name libxml2 Buffer Overflow*

Next step?

---

### Post by OpSecShellshock on 2012-11-29
OK, so you're dealing with something signature based. The thing you'll want to do is see if it's even anything to worry about in the first place. Read the signature itself to see what it's written to match against, then look at the data that was flagged to see if there's really a match there. You should also check for reference information that the signature is based on. A lot of times they'll refer to a CVE number, which you can search in google to see if it even applies to your version.

Another thing to check for is if the data is encrypted or compressed in some way, as that will often cause signature matches coincidentally due to matching against encoded strings rather than what's actually being transmitted.

Basically, seeing the signature name alone on a report (or sometimes with the total number of times it was matched) is not enough information to even tell you for sure that there is a problem, let alone how to fix it.

---

