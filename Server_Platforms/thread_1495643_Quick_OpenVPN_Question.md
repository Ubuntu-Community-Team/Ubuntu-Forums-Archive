---
title: "Quick OpenVPN Question"
date: 2010-05-28
forum: Server Platforms
---

### Post by spynappels on 2010-05-28
Hi,

I have a very quick OpenVPN question.

If I want to run multiple instances of OpenVPN from my Ubuntu Laptop, each connecting to a different VPN (home and work), can I just place both conf files in the /etc/openvpn directory and they will both start when OpenVPN starts, or is some more magic required?

Thanks.

---

### Post by spynappels on 2010-05-28
To answer my own question, it appears that placing the two conf files into the /etc/openvpn directory DOES work, I have both running now.

There is a slightly strange thing I have noticed however: ifconfig only shows 1 tun interface, which is the one created by the last conf file to be started. Anybody know why this is?

---

