---
title: "having remote server connect to my home network using either l2tp or openvpn"
date: 2017-08-02
forum: Server Platforms
---

### Post by kustomjs on 2017-08-02
Hello Guys
I am just wondering if anybody could point to me the correct way to connect my 16.04.1 lts server as either to l2tp or openvpn client to my home network since my server is on remote vps server and they have tun adapter turned on the server.

---

### Post by papibe on 2017-08-02
Hi kustomjs.

Does it have to be one of those two options? Are you open to another VPN software? 

If so, I'd recommend taking a look at [Tinc VPN]("https://www.tinc-vpn.org/"). Here's a [tutorial]("https://groups.google.com/forum/#!topic/homefrontrouter/ayeyqauN1ao").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by kustomjs on 2017-08-02
It haves to be setup this way how my network is setup since I am using Miktroik router that supports l2tp or openvpn

---

### Post by darkod on 2017-08-02
For openvpn it is easy to find examples and tutorials online. You can also try the ubuntu help pages help.ubuntu.com

---

### Post by kustomjs on 2017-08-03
see most of them examples and tutorials dont work if your on VPS server just fyi that is where I am having problems with ubuntu vps with openvpn.

---

### Post by darkod on 2017-08-03
If you have a dedicated public ip for your vps, then it shouldn't matter. Depending what you find more useful for you, you can set it up the home router to be openvpn server and the vps to be the client, or the other way around.
In any case the vps should be able to be server or client. If it doesn't work because of the vps infrastructure, change your provider.

---

