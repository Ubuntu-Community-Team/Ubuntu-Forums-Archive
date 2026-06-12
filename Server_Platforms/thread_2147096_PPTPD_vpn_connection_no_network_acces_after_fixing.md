---
title: "PPTPD vpn connection no network acces after fixing no internet"
date: 2013-05-20
forum: Server Platforms
---

### Post by Derlux on 2013-05-20
Hello everyone,

I have set up a pptp server on my ubuntu 12.04 server. It wouldn't give internet acces to clients, becouse it would tunnel the internet connection too. This has been fixed by disabling remote gateway in windows:

[http://cat.pdx.edu/windows/disabling-remote-gateway-on-windows-7.html](http://cat.pdx.edu/windows/disabling-remote-gateway-on-windows-7.html)

This however, fixed the internet problem, but now it won't connect to the network file share anymore!
I have read some things about adding routes in windows, but I'm really stuck atm.

thanks for your help!

---

### Post by Derlux on 2013-05-20
This is what I found, but I don't completely understand it, could someone explain it a little futher?

[http://serverfault.com/questions/387520/windows-vpn-no-internet-access](http://serverfault.com/questions/387520/windows-vpn-no-internet-access)

"

[COLOR=#000000][FONT=Arial]You need "use default gateway on remote network" unchecked, and you need to manually add routes to the VPN network on your windows workstation.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]On the Command Line, do:[/FONT][/COLOR]

route ADD 157.0.0.0 MASK 255.0.0.0  157.55.80.1[COLOR=#000000][FONT=Arial]with your appropriate IP's, where **157.0.0.0** is the *VPN Network (internal LAN on your remote end),***255.0.0.0** is the *appropriate netmask* and **157.55.80.1** is the [I]gateway interface (your remote gateway)

"[/I][/FONT][/COLOR]

---

