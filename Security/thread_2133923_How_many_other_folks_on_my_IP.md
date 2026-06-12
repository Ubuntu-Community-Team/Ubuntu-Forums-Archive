---
title: "How many other folks on my IP?"
date: 2013-04-09
forum: Security
---

### Post by Paqman on 2013-04-09
I've installed Tinyproxy on a remote server and it works fine. One thing I don't particularly like about it is the way the only security it offers is IP-based. I assume my ISP has quite a few of us on the same IP and does some NAT trickery behind the scenes. Is there any way I can find out how many people are likely to be on the same IP as me?

---

### Post by SeijiSensei on 2013-04-09
is this a transparent proxy, or do you have to configure it in the browser?  If the latter, I don't think you need to worry.  Who, other than you, would know that the proxy even exists?

Also if it keeps logs of requests, do you see requests you didn't make yourself?

---

### Post by Paqman on 2013-04-09
> **SeijiSensei said:**
> Who, other than you, would know that the proxy even exists?


The proxy does return an error if an IP outside it's allowed range tries to connect, so presumably a script could detect it's presence. I'm with a major ISP. If there's 10,000 of us on this IP I would have to assume that some were both technically competent and mischievous enough to be sniffing around for such things. If there's only 10 of us then that's less of an issue.

I'm not massively worried about this, just wondering if there was some way I could find out the size of the hole I've opened.

---

### Post by SeijiSensei on 2013-04-09
Where is the proxy located?  Isn't it upstream from you somewhere?  If so, how would someone else even knows it exists, much less what IP address it is located at?

---

### Post by lisati on 2013-04-09
There's some stuff people at sites you visit can do to tell if you're using a proxy. How successfully the "tricks" I know about work depends part on the degree of anonymising the proxy service you are using does.

[http://lisati.homelinux.com/whoami](http://lisati.homelinux.com/whoami) regonises some of the indicators, but is fairly unsophisticated in its approach.

---

### Post by Paqman on 2013-04-09
> **SeijiSensei said:**
> Where is the proxy located?  Isn't it upstream from you somewhere?  If so, how would someone else even knows it exists, much less what IP address it is located at?

People scan IPs speculatively looking for open proxies. Or rather, I imagine people's botnets do so. I've changed the default port, but that's only going to stop the lazy ones. I figure with a funny port and only accepting a single IP it's reasonably safe, but that really depends on just how many people share that IP. Hence my question.

---

### Post by CharlesA on 2013-04-09
I guess it depends on the ISP. Most of the ones I've used used DHCP + the MAC of your modem to assign you an address. The IP I have at home is a public address and I don't see why an ISP would share those.

However, some of the smaller ISP might do it a different way, like assign each customer a private IP for their external IP, but then do some fancy NATing or whatever to get a bunch of users under one external public IP.

---

### Post by Paqman on 2013-04-09
> **CharlesA said:**
> The IP I have at home is a public address and I don't see why an ISP would share those.

IPv4 addresses are getting in pretty short supply, so there is a move towards NAT to make them last longer. It's not clear which ISP's are and which aren't, or even how much they're doing it. All I've heard from my ISP is a wishy-washy admission that it would be pretty much inevitable for them to start doing it, but that doesn't really help in the here and now. I'd like to be able to assume I've got my own IP, but I can't be sure.

---

### Post by SeijiSensei on 2013-04-10
If you control both ends of the connection, why not set up an OpenVPN tunnel and send your proxy traffic over that?  [Static-key tunnels]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") are really a cinch to configure.  Make the proxy server the VPN server and use the "remote" directive on your end to set up the tunnel.  That works through NAT and doesn't require a static address on the client side.

---

### Post by Paqman on 2013-04-10
I'll have a look at that, cheers.

---

