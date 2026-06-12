---
title: "Tomato or SmoothWall style web UI for dhcpd/iptables/etc on Ubuntu?"
date: 2011-11-29
forum: Server Platforms
---

### Post by Drock on 2011-11-29
I currently leave my ubuntu based media center pc on full-time but I'd like to let the media center go to sleep when I'm not actively using it. Only problem is that the media center needs to be on 24/7 because it acts as a file server (with software raid 1), streams my music (subsonic), and runs an ssh server so that I can proxy traffic through it for secure browsing. I'd like to move all of these functions off of the media center and onto a lower power machine. Then I started thinking why not just let this new machine be my home router and replace my ageing wrt54g.

Only problem is that I'm lazy (and busy) and don't want to configure iptables/dhcpd/dnsmasq/ntpd/etc by hand.

I'd like to just have some meta-package that installs all of the above and gives me a nice web ui. Does this exist?

I've also considered just running smoothwall in a VM on the new machine. This seems silly but it might be stupid enough to work. Anyone have experience with this?

---

### Post by Drock on 2011-11-29
Looks like [someone else]("http://retout.co.uk/blog/") had a similar idea and has started ripping out the UI of smoothwall express. And porting it to Debian. Check out this post:

[http://retout.co.uk/blog/2010/08/16/smoothwall_express_on_debian](http://retout.co.uk/blog/2010/08/16/smoothwall_express_on_debian)

Looks like it is very alpha at this point.

---

### Post by volkswagner on 2011-11-29
Other options also include [Zentyal]("http://www.zentyal.com/"), [ClearOS]("http://www.clearfoundation.com/Software/overview.html"), or simple alternattive could be to use [pfsense]("http://www.pfsense.org/").

---

