---
title: "Setting Up Server/Client"
date: 2010-07-01
forum: Server Platforms
---

### Post by Thunderbolt1164 on 2010-07-01
I have been trying to setup Ubuntu 10,04 as a Terminal Server

I have tried it (and it worked) with Fedora bur think that the people using the clients will like Ubuntu better, (I do)

My problem with Ubuntu seems to be that the Clients are not receiving PXE-BOOT (DHCP)

The server IS behind a Firewalled/DHCP Enabled Router (D-Link Gamer Lounge), (Onboard LAN) which is then sent to a D-link Switch via 3Com LAN Card for the Clients

Since it seems to work with Fedora but not with Ubuntu, I am thinking that I am not setting up the LAN Cards the right way.

Oh, the onboard LAN can FULLY access the Internet

I have Attached a drawing of the network setup I am using.

---

### Post by cariboo on 2010-07-02
Are the second nic and the thin clients on a different netblock from the rest of the network? if the primary nic and the rest of the network is in 192.168.0.1 - 254. the secondary nic and the thin clients should be in 192.168.1.1 - 254.

---

### Post by Thunderbolt1164 on 2010-07-02
I don't think so since I don't know how to setup a second netblock

I will do some reseach on that and get back to you

Thank-You

---

