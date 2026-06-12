---
title: "Using Virtual Hosts for resolving other internal IP's"
date: 2014-08-24
forum: Server Platforms
---

### Post by lon0 on 2014-08-24
Hi, so I am using Ubuntu 12.04.5 LTS

What I am trying to do is route external traffic to my Owncloud instance, this in itself isn't an issue, but I also have a separate machine running OpenVPN which I use to generate webpages with user profiles so they can be downloaded. So vpn.example.com takes me to my OpenVPN server. I have on my router port 80 and 443 pointing towards this server.

What I think I need to do is point ports 80 and 443 towards my Ubuntu server(192.168.1.10) and route any traffic to vpn.example.com to my OpenVPN(192.168.1.15) server with Virtual hosts and create a subdomain cloud.example.com to point at the same external IP then deal with that in Virtual hosts too which would then point to my Owncloud instance on my Ubuntu server.

Generally I have a good idea of networking but I haven't dealt with Virtual Hosts a lot and the documentation I have found on it is difficult to understand. If someone could help me with either better documentation or if I am even dealing with this in the right way!

Thanks in advance.

---

### Post by volkswagner on 2014-08-24
You can accomplish your goal with reverse proxy.

I created a quick [how to]("http://ubuntuforums.org/showthread.php?t=1920715") on this.

What you'll want to avoid is redirecting any https ie: 443.

You can come up with a plan such as a landing page with links that direct traffic to alternate ports like :4443 to avoid
redirects.

You'll want to designate one machine as the "main" which will have ports forwarded from router, then reverse proxy to alternate machines.

---

### Post by lon0 on 2014-08-27
Thanks for the response, I've been playing around with what you have suggested and it looks like it fits my needs.

However I am struggling with part 2 "[COLOR=#000000]This assumes you have NameVirtualHosts already working on both servers."

[/COLOR]If you could point me in the direction of how to configure this part first that would be fantastic thanks!

---

### Post by volkswagner on 2014-08-28
The sticky at the top of this forum should help.  [Here is a link to the Apache2 docs]("https://help.ubuntu.com/10.04/serverguide/httpd.html"), which contains setup for vhosts.

---

