---
title: "Making my firewall / router Ubuntu 12 server connect to a VPN service"
date: 2014-03-19
forum: Server Platforms
---

### Post by rbuanno on 2014-03-19
Title says it all.
I would like to connect my server to a VPN service, What would i need to do to :
1. connect to the service and make tunnel
2. make sure my LAN network traffic gets sent through the tunnel
3. would installing a proxy service like squid later on my server cause issues?

thanks in advance,
Ron

---

### Post by rbuanno on 2014-03-19
I want to use my account at privateinternetaccess.com
if that matters at all.

---

### Post by d4m1r on 2014-03-24
So you have access to a VPN service from that company, and you want to route all internet-bound traffic from your server THROUGH your VPN connection?

Is it a physical server you have at home, or?

---

### Post by aaron_surabhi on 2014-10-03
[h=3][COLOR=#222222][FONT=Verdana]my friend uses [/FONT][/COLOR][COLOR=#222222][FONT=Verdana][VyprVPN]("https://www.bestvpnservicemag.com/best-vpn-for-linux/") for his pc. [/FONT][/COLOR][COLOR=#222222][FONT=Verdana]hope that helps! Good luck![/FONT][/COLOR][/h]

---

### Post by volkswagner on 2014-10-04
Well it seems your provider supports OpenVPN.

You will want to install OpenVPN on your server and set it up as a client. since your provider does not provide how-to's for
command line systems, you'll need to pull info from several sources.

[https://openvpn.net/index.php/open-source/documentation/howto.html](https://openvpn.net/index.php/open-source/documentation/howto.html)
[https://www.privateinternetaccess.com/pages/client-support/#ubuntu_openvpn_installer](https://www.privateinternetaccess.com/pages/client-support/#ubuntu_openvpn_installer) (obviously you don't want to use network manager)
[https://openvpn.net/index.php/open-source/documentation/howto.html#startup](https://openvpn.net/index.php/open-source/documentation/howto.html#startup)


I have not configured a OpenVPN client via command line (only servers). I also don't know best practice
to route all dhcp client traffic through the VPN tun interface.
I don't think Squid install later will be a problem, but it likely won't be a "cookie cutter" install/configuration.

I suggest making this several steps. Get a working vpn connection to the server, make sure you can ping the server
via client and all your routes look correct, along with surviving a reboot. After you have a working client config, move
to making the tun adapter your gateway for client DCHP machines or try static config client first.

---

