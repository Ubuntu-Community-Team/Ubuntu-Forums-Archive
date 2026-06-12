---
title: "Stupid printing problem"
date: 2007-02-26
forum: Server Platforms
---

### Post by nucklebone on 2007-02-26
I have CUPS installed and running on a Gnu/Linux (Edgy) machine that has a static IP address, connected to a modem/router. The LaserJet is connected via USB to the edgy machine. Printer sharing is turned on.

Also connected to the same modem/router is a Macintosh running OS X. This machine is on the same subnet as the Edgy machine. Additionally, connected to this same modem/router is another router, which is DHCP serving a wireless network of 2 Macintosh Laptops. This 2nd router's static address is also on the same subnet as the Edgy machine, but the 2 DHCP served laptops are on the DHCP server's subnet.

Printing is great from the Edgy machine to the connected USB printer. With sharing enabled, I can print to the Edgy machine's printer from the Macintosh that is on the same subnet. It sees it on the network as a shared printer. My problem is that I also need to print  from my wireless laptops. They are, however, on a different subnet being DHCP served from the 2nd router and do not see the shared printer like the Mac on the same subnet does. As far as I can tell there is no firewall blockage either. That is to say I didn't turn one on or set one up to block any ports. SSH/FTP work fine so I know it's not a physical connectivity issue. Maybe the CUPS config file can be edited to allow access?

My network looks roughly like this:

 ([COLOR="DarkRed"]Edgy machine with USB connected Laser printer[/COLOR])
|
|
[[COLOR="DarkRed"]MODEM/ROUTER[/COLOR]]&#8212;&#8212;([COLOR="DarkRed"]Macintosh Desktop machine[/COLOR])
|
|
([COLOR="DarkRed"]2nd Router[/COLOR])&#8212;([COLOR="Red"]DHCP Served Laptop[/COLOR])&#8212;([COLOR="Red"]DHCP Served Laptop[/COLOR])

---

