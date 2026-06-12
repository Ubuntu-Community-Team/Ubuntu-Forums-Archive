---
title: "squid resolving problem (?) with jaunty (webbrowsers not working with proxy)"
date: 2009-07-28
forum: Server Platforms
---

### Post by Krijk on 2009-07-28
I run a 9.04 server with BIND9 for DNS and Squid 2.7.STABLE3-4 as a proxy (with prefetch)

Today all of a sudden my browsers (firefox and epiphany) couldn't resolve websites anymore.
I checked the internetconnection and it was fine.
I chose a direct internet connection without using squid and firefox was working again. Epiphany wasn't able to connect to internet anymore.

After checking the logfiles the only problem I could find was that 1 of the DNS-forwarders wasn't working properly, but the secondary worked.

It seems though that the proxy is flickering (sometimes working, sometimes not). Firefox works bypassing the proxy, but Epiphany doesn't.

Does anybody have had similar problems or any idea how to solve this? 

PS
I just switched to Jaunty a week ago and before that was running 8.04LTS without a lot of issues.

---

