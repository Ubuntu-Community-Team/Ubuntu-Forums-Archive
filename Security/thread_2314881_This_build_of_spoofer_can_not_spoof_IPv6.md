---
title: "This build of spoofer can not spoof IPv6?"
date: 2016-02-24
forum: Security
---

### Post by trpted on 2016-02-24
While this works fine on my Windows computer [DSLR (dslreports) -> Forums -> Software and Operating Systems -> Security -> Test your firewall / ISP for anti-spoofing filters (very cool utility)](https://www.dslreports.com/forum/r30600735-Test-your-firewall-ISP-for-anti-spoofing-filters-very-cool-utility) on my lubutu computer shows/tells me this error:
> This build of spoofer can not spoof IPv6

:(

On my Windows computer it does not show/tell me that.

Any ideas of how to fix this?

Thank you

---

### Post by trpted on 2016-04-16
As how it is was solved.

It can be confusing but, when you have the machine build software, it needs the 'development' package of a dependency, which is not spelled out in the READMEs quite often, if not typically. I would suggest to install libpcap0.8-dev and try again.

---

