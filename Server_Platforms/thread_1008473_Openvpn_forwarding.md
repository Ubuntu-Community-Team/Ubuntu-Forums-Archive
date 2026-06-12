---
title: "Openvpn forwarding?"
date: 2008-12-11
forum: Server Platforms
---

### Post by xinel on 2008-12-11
Hello,

My plan is to have a local server connect to openvpn accounts to servers around the world as needed and for all network traffic on the lan to go through my server. Is this possible? is there a tutorial on how to do it?

Cheers

- xinel

---

### Post by cdenley on 2008-12-11
It's possible, but depending on what kind of traffic you need forwarded, using ssh would be much simpler. Do you want to allow users to connect to services on the VPN server or it's LAN, or use it as a proxy to access the internet? You can create an ssh tunnel that works as a socks proxy.
```

ssh -D 8080 mydomain.com

```

---

### Post by xinel on 2008-12-12
Would that socks proxy handle all traffic? or only web traffic?

Cheers

- xinel

---

### Post by cdenley on 2008-12-12
All internet traffic. I never tried it with LAN traffic.

---

### Post by xinel on 2008-12-12
Nice, thanx for the help :)

---

