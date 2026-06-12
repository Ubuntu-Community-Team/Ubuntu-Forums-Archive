---
title: "OpenVPN security practices / auditing"
date: 2011-10-19
forum: Security
---

### Post by vajorie on 2011-10-19
I've got an openvpn server on amazon's aws for personal use (me & my family). It uses the usual certificate authentication and also have ssh running (key authentication) though I have amazon's firewall block shh's port to the outside... 

My question is: what are considered as best security practices for an openvpn server; and how do you actually audit an openvpn server?

Edit: It also has ntop installed so that I can have an idea about connected hosts etc.

---

### Post by Dangertux on 2011-10-21
> **vajorie said:**
> I've got an openvpn server on amazon's aws for personal use (me & my family). It uses the usual certificate authentication and also have ssh running (key authentication) though I have amazon's firewall block shh's port to the outside... 

My question is: what are considered as best security practices for an openvpn server; and how do you actually audit an openvpn server?

Edit: It also has ntop installed so that I can have an idea about connected hosts etc.

Best practices in this case fall into two categories. How well the service itself is secured and the encryption used.

OpenVPN's hardening documentation is actually pretty good : [http://openvpn.net/index.php/open-source/documentation/howto.html#security](http://openvpn.net/index.php/open-source/documentation/howto.html#security)


As far as things to look for when auditing a VPN server.

- Open ports (usually 443, 1723, UDP 500) will be present. 
- Look for PSK disclosure (wireshark or tcpdump can help you here)
- Authentication Header disclosures (again wireshark or ike-scan)
- PSK strength , can be audited with cain & abel.

Hope that helps :-)

Good luck.

---

