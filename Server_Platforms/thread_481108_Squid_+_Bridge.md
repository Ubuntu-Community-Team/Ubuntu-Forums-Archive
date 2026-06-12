---
title: "Squid + Bridge"
date: 2007-06-22
forum: Server Platforms
---

### Post by nabberuk on 2007-06-22
Quick question!
I currently have a bridge set up between eth0 and eth1, both with ips 0.0.0.0 so internet traffic just pass's straight through, Is it possible using iptable to redirect the traffice through the squid proxy first?

This needs to be a truely plug and play thing, so no ips can be set on the adapters!!!

thanks for your help!

---

### Post by turinglabs on 2007-06-22
You want to use ebtables *and* iptables, as you need to get the traffic from layer 2 to layer 3 before it can be redirected. See [http://freshmeat.net/articles/view/1433/](http://freshmeat.net/articles/view/1433/), or just google 'ebtables squid'.  

If the squid proxy is on a different box, that's a bit more complicated, but doable. [http://www.ibiblio.org/pub/linux/docs/HOWTO/TransparentProxy](http://www.ibiblio.org/pub/linux/docs/HOWTO/TransparentProxy) is a bit dated, but the iptables commands are still accurate, see section 6.2 on policy routing.

---

### Post by nabberuk on 2007-06-25
many thanks for your reply, i'll give it a go as soon as i get home.

Thanks!

---

