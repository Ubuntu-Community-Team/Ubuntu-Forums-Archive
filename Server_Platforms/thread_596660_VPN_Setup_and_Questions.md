---
title: "VPN Setup and Questions"
date: 2007-10-29
forum: Server Platforms
---

### Post by pkarjala on 2007-10-29
This might be more suitable for the Networking forum, but I'm attempting to set up a VPN Server, so here it goes.

We've currently a number of computers that are sitting at different sites behind routers with NAT set up for each individual computer.  Instead of having a multitude of NAT port forwards, we'd like to set up a VPN tunnel to each site to get past the router to the computers behind it and all services involved.

Here's the basic setup:

Main Office |------| Ubuntu LAMP (VPN Server) |------| {Internet} |------| Router @ Remote Site |-------| Remote computers / devices

From anywhere, I'd like to be able to go in through the VPN Server from my laptop, and directly to any of those remote sites.  In other words:

Laptop  -------> {Internet} |------| Ubuntu LAMP (VPN Server) |------| {Internet} |------| Router @ Remote Site |------| Remote computers / devices

The problem with this is that we do not have an Ubuntu box sitting at each of these remote sites; just the Router.  Is there a way to configure the VPN tunnel to each of these remote sites?  Or am I asking the question in the wrong way?

Thanks, as always, for the assistance.

---

### Post by HermanAB on 2007-10-30
You should look at OpenVPN: [http://openvpn.net/](http://openvpn.net/)

It is cross platform, so one end could be Windoze, the other Ubuntu.  Being SSL based, it is relatively easy to configure.

---

### Post by pkarjala on 2007-10-30
Thanks, Herman, I'll take a look into it.

Do you know if it will meet our needs as a VPN Bridge?

---

### Post by tj71587 on 2007-10-31
It is able to be configured as a vpn bridge, however this is alittle more difficult.  I am currently trying to configure as well.

---

### Post by robert_pectol on 2007-11-02
Yes.  Openvpn supports both routed and bridged configurations.  I'm using bridged on mine and so far, it's been working like a charm.  I can now VPN in to my home network from anywhere and have access to my local LAN, browse Windows shares, etc.  It's really nice!  It was easy to set up and it just seems to work!  I've connected to it from both Linux and Windows clients with success.  To get you up and running, have a look at the Openvpn howto here:

[http://openvpn.net/howto.html](http://openvpn.net/howto.html)

For implementing a bridged configuration, see the ethernet bridging howto here:

[http://openvpn.net/bridge.html](http://openvpn.net/bridge.html)

It's very straight forward.

---

