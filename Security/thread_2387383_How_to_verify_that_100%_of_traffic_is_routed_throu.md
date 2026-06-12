---
title: "How to verify that 100% of traffic is routed through my VPN"
date: 2018-03-18
forum: Security
---

### Post by WinterMadness on 2018-03-18
Just wondering. I know when I use my web browser it is, but if I am using any other service, or port, I want to know that it is using my VPN too.

Can anyone help me out? I am using Kubuntu 17.10, and I used the KDE Network managers built in OpenVPN option (downloaded a config file from my vpn provider, and imported it)

---

### Post by The Cog on 2018-03-18
Your default route should be out via the tunnel interface, and just a specific route to the VPN server out via the ethernet interface.
Or you might find that rather than replacing your default route, it adds two more specific routes via the tunnel - 0.0.0.0/1 and 128.0.0.0/1. Post your routing table here and we can check it. The command to show that is
```
route -n
```

---

### Post by tuxxy on 2018-03-18
There is a cool app called Nutty that should show you this in a GUI list.

---

### Post by HermanAB on 2018-03-19
Err... tcpdump of course.

# tcpdump -nlX -i eth0

---

