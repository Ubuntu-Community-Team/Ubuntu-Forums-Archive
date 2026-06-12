---
title: "Open VPN Bridge configuration"
date: 2011-11-20
forum: Server Platforms
---

### Post by markosjal on 2011-11-20
I have Ububtu 10.04 already running on a VPS server. I thought I would try Squid proxy and I was never able to get any authentication working. I have now given up and will try openVPN .

I have followed the guide at
[https://help.ubuntu.com/10.04/serverguide/C/openvpn.html](https://help.ubuntu.com/10.04/serverguide/C/openvpn.html)

And the bridging info at
[https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html#bridging](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html#bridging)

However I am confused at what IPs in the examples refer to REAL IPS vs Virtual IPs

My VPS has a public IP directly so I have noo firewalling or NAT issues



Where can I get a better explanation?

---

### Post by toshko3 on 2011-11-21
What exactly is your purpose?:confused:

---

### Post by septus1 on 2011-11-24
i'm looking to do something similar. 
I don't know if you want the same thing markosjal, but here is my idea:

i have a VPS with ubuntu 11.10
I want to create a vpn server that can tunnel my internet traffic over the internet. As i travel alot i don't always trust the connection i'm on.
I also want to use the VPS as a personal storage with a AFP/NFS share or similar.

the steps i've already taken:

1. i created a vlan with a private address range and attached a dhcp service to it.
2. i used UFW to close the vps off from the outside world. is still have ssh open because i can't get in otherwise, but the idea is to only open the vpn port. preferably openvpn ssl over port 443 which will get me through firewalls. Ones i'm in i should be able to tunnel my internet traffic and connect to my personal storage share.

The next step would be to install openvpn over ssl and be able to connect to it via tunnelblick. Now this is where is it gets tricky. because the only way to set this up correctly is to have the iptables set up correctly which is pretty hard.

Doesn't anyone know if there is an easy solution to this?

---

