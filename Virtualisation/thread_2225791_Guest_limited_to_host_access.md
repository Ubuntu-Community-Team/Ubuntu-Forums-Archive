---
title: "Guest limited to host access"
date: 2014-05-23
forum: Virtualisation
---

### Post by henry24 on 2014-05-23
Ubuntu Server 14.04

I have setup a simple virtual network. Unfortunately my guests can only reach the host as per:
[http://wiki.libvirt.org/page/Guest_can_reach_host%2C_but_can%27t_reach_outside_network](http://wiki.libvirt.org/page/Guest_can_reach_host%2C_but_can%27t_reach_outside_network)

I have vrified (1) and (2) so my problem is (3)

"[COLOR=#000000][FONT=Verdana]If your libvirt network is using <forward mode='route'/>, you are responsible for informing the rest of your network that the gateway to this network is the external/public IP address of your virtualization host. Instructions on how to do this are dependent on the setup of your network, and beyond the scope of this troubleshooting guide."

Can anyone tell me what this means and how it may be resolved please.[/FONT][/COLOR]

---

