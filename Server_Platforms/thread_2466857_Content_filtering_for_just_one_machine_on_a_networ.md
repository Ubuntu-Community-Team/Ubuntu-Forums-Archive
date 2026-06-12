---
title: "Content filtering for just one machine on a network"
date: 2021-09-08
forum: Server Platforms
---

### Post by grant-howat on 2021-09-08
Hello,

I'm looking for a bit of assistance. I have one machine, a chromebook, that I want using a proxy server while on my network via my wifi AP.

So, is there a way to use a DHCP server to deploy proxy settings to one, specific MAC, but not to other MACs?

If I can just get a name of a DHCP server that is capable of doing that, I should be able to sort it out.

Perhaps it isn't possible. But if somebody knows of a way, I'd really appreciate it.

Thank you,
Grant

---

### Post by LHammonds on 2021-09-09
Or have all go thru the proxy and have different rules on the proxy based on MAC address?

Just a guess.  I do not use proxy's for that.

LHammonds

---

### Post by scorp123 on 2021-09-09
My Synology router could do that if I wanted to, e.g. I can pick different devices from my LAN and pack them into different groups in the "Safe Access" app, so that different rules apply to them. I could for example pack my daughter's devices into a filter group so she can't access sites that I deem unsuitable for her (e.g. gambling, mobile games, etc.), while my own devices are in a different group where only Ads are blocked.

[https://kb.synology.com/en-us/SRM/help/SafeAccess/safeaccess_desc?version=]("https://kb.synology.com/en-us/SRM/help/SafeAccess/safeaccess_desc?version=")

---

### Post by scorp123 on 2021-09-09
Accidental double-post, please ignore.

---

