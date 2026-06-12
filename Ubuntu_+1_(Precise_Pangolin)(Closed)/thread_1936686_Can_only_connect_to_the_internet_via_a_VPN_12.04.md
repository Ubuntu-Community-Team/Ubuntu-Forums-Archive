---
title: "Can only connect to the internet via a VPN 12.04"
date: 2012-03-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by imafatmess on 2012-03-06
On my home network I usually connect to the internet straight from the ubuntu desktop. This all worked fine until yesterday.

At university to connect to the internet, I have to go through a VPN client and an automatic proxy: [http://wwwcache.gla.ac.uk/glasgow.pac](http://wwwcache.gla.ac.uk/glasgow.pac)

This again all works fine. However earlier today whilst at university my laptop ran out of battery mid use. This usually wouldn't be a problem.

I got home today and as I usually would do when I get home from uni, I changed the proxy settings to None to connect to my home network, applied this system wide and usually everything would be hunky dory. However it won't connect at all with no VPN.

I can still connect to the internet if I use Cisco VPN software to connect to the Uni VPN and using the automatic proxy but without this I cannot connect.

I'm not sure what to do in this situation, would anyone be able to give me a hand? (and yes I'm on the beta 12.04 release, probably not the best idea in the world but thus far it seemed exceedingly stable)

Thanks! Greatly appreciated!

---

### Post by imafatmess on 2012-03-06
Just worked out this is a problem with my proxy settings. If I override the system proxy in firefox, by using firefox's own proxy settings I can connect to the internet, just the network proxy settings aren't too happy right now.

Anyone got any suggestions?

Thanks!

EDIT -> Scrap that, doesn't work at all. Without Cisco VPN or the proxy I can access gla.ac.uk website and that is all. Otherwise I get the standard "problem loading page" style screen

---

### Post by Iowan on 2012-03-06
Moved to Ubuntu +1 (Precise Pangolin)

---

### Post by imafatmess on 2012-03-07
I have now worked out that it is a system wide setting which seems to not be changing. When I log in with a different user I still get the same problem, without Cisco VPN and an automatic proxy I can connect to gla.ac.uk and that is it. With Cisco VPN and automatic proxy I can connect to any site.

---

