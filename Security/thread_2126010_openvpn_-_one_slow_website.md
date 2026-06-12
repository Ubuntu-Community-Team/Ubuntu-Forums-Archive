---
title: "openvpn - one slow website"
date: 2013-03-15
forum: Security
---

### Post by horace on 2013-03-15
I'm running openvpn on a virtual server, and routing all my web traffic through that. All has been fine, but for the last couple of weeks I have found one website really slow to respond. If I stop the vpn on my local machine it responds as normal, but via the vpn it takes 15-30 seconds to load a page. A traceroute or ping shows no delays, and only one site is affected. Anybody got an explanation for me?
Thanks

Edit: Correction to the above; tcptraceroute shows no delay, but traceroute fails at the last hop to the website.

---

