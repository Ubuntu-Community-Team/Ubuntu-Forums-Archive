---
title: "Static IP and DNS from DHCP?"
date: 2014-03-22
forum: Server Platforms
---

### Post by mrhub on 2014-03-22
Can i somehow get the DNS from my routers DHCP and set the IP manually?
My IPs change the DNS from time to time and my router gets really weird if I set IP reservations...

My thought was to make a script that asked the DHCP for settings and use the DNS from the response somehow, is that even possible?

---

### Post by nerdtron on 2014-03-22
Set static IP of the server in the /etc/network/interfaces file.
Then how do you check if your ISP changes the DNS? You can write a script on on that then save the extracted DNS IPs to the /etc/resolv.conf file.

---

### Post by steeldriver on 2014-03-22
Most consumer routers will act as DNS servers, so wouldn't the easiest thing be to set your router (gateway) IP as dns-nameservers for your static LAN clients and have the router pull the new upstream DNS servers from your ISP via DHCP?

---

### Post by d4m1r on 2014-03-24
Sorry, why is that exactly necessary?

Isn't it just easier to set the DNS on the server to point to your router, which in term you can change DNS servers in 1 place across all devices (on your router itself)?

---

### Post by steeldriver on 2014-03-24
> **d4m1r said:**
> Sorry, why is that exactly necessary?

Isn't it just easier to set the DNS on the server to point to your router, which in term you can change DNS servers in 1 place across all devices (on your router itself)?

That's exactly what I'm suggesting (sorry if that was not clear)

---

