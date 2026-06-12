---
title: "problems with dansquardian/squid"
date: 2010-03-17
forum: Server Platforms
---

### Post by monkeyslayer56 on 2010-03-17
well i helped someone set up a transparent dansgaurdian with squid for a school proxy but before doing so i set up a test server(xbuntu 8.04) at my house and it worked great however when i set it up for the school(ubuntu server 9.10) there was a HUGE impact on performance. when doing a speedtest on a non proxyed the results are  3-4 Mb/s download and 13 Mb/s upload and ping <100ms while on a proxied system 1-2 Mb/s download with upload <1000 b/s and ping around 5000ms. there were at most 2 people going through the proxy at the time. at the moment i don't have acces to the server(only go out once a week and remote access isn't configured yet) so i can't post my config files yet but is there anything i can look for when i do get access again? i DO have reverse lookup setup on dansgaurdian and a few blocking lists enabled the rest is default. and for squid i installed the squid3 package and made sure that any system can connect to it(for debugging reasons later plan for dansgaurdian to be the only connection to squid) and as far as that its the default configuration. and iptables redirect port 80 to 8080 and the browsers are configured for the proxy so that https works. im posting this now so that i can have a heads up on what to look for since when i make it back out there friday i wont have much time because of some previous arrangements. but hopefully i'll have remote access soon.

---

