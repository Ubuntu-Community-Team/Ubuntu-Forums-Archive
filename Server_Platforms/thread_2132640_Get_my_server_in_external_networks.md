---
title: "Get my server in external networks"
date: 2013-04-05
forum: Server Platforms
---

### Post by Derlux on 2013-04-05
Im lately really into ubuntu and learning allot about it for the past 3 months. I have my server up and running but now I want some more where google didn´t give me what I wanted.

I have my network at home with my server set up, using samba file share and sabnzbd and running websites. 
What I want now is that my girlfriend, and me when I´m traveling, to see my server in the network with the shared files by samba, so it appears the server is in my network while it actually is at my home.
I have tried vpn but this gave as result it only connected to my network at home. I only want the server to appear in the network my gf is, next to her normal network, so an extra pc connected to hers.

I couldn´t find where I was looking for, and I´m still a newbie compared to the rest at these forums so take that in account :)

I hope that someone can help me out!

---

### Post by darkod on 2013-04-05
You can't do that. A remote location can never appear the same as your local network/location.

The VPN is the right way to do it. After connecting the VPN connection you can access anything in your home network just like if you were at home. Plus, the connection is encrypted and secure (make sure you set up secure VPN).

---

### Post by Derlux on 2013-04-06
Oke thanks, appearantly I just ran into the first thing I can't do :)

I think that you are right and a VPN is the right way. pptp did it's job really quick, what about openvpn or another protocol? What would you advice?

---

### Post by darkod on 2013-04-06
I haven't had the chance to configure vpn server on ubuntu yet, but OpenVPN seems the one used most often.

[https://help.ubuntu.com/12.04/serverguide/openvpn.html](https://help.ubuntu.com/12.04/serverguide/openvpn.html)

---

