---
title: "DHCP connection sharing"
date: 2010-12-29
forum: Server Platforms
---

### Post by idny on 2010-12-29
I did search, but could not find a solution.

Right
I've installed Ubuntu Server 10.10 on an old machine, installed fine and the system is running. 
I have a windows 7 desktop that is connected to the internet via wireless. The desktop then has an ethernet connection which is shared to the ubuntu server. The network looks like this.

Modem > Router > Desktop > Switch > Ubuntu Server

My problem here is that there appears to be no connection from the server to the desktop. The server cannot connect to the internet.

When i ifconfig the ubuntu machine shows.
eth0 link encap:Ethernet
inet address: 192.168.137.2 Bcast:192.168.137.255 Mask 255.255.255.0

However on the windows desktop (the machine sharing the internet)
these are the details for the connection to ubuntu server.
ip 169.254.170.50
mask 255.255.255.0

is this a dhcp problem? is my server configured wrong?

if it doesn't make sense let me know :)
thanks.

---

### Post by koenn on 2010-12-29
it doesn't make sense

---

### Post by drdos2006 on 2010-12-29
Your Windows 7 is on a different network to your server.
inet address: 192.168.137.2 server
ip 169.254.170.50 
Windows 7 does not appear to be getting its IP from your router.
It would probably make more sense to connect your server and the desktop to the router rather than to the switch, that way both machines can be given a DHCP lease from the router.

What IP range is your router set to give out ?

regards

---

### Post by Justin_Ferrell on 2010-12-29
well the 169.254.170.50 is a zero config ip address. This means that you are not recieving an IP address from your DHCP server. Now, this can be caused by many things. One could be MAC filtering from your ISP modem. Another issue you may be having is a broken winsock on you windows machine. Open your command prompt an type netsh winsock reset and reboot your machine. Last it could be how you have your network layed out. try Modem >Router > Switch > Desktop & Ubuntu Server

---

### Post by elico on 2010-12-30
well it's pretty obvious...
now what you have is:
[IMG]http://img402.imageshack.us/img402/2996/93306411.jpg[/IMG]

and you sou should build it like this... or ....use windows connections shareing but it wont be connected to you lan.
[http://www.windowsreference.com/windows-vista/step-by-step-internet-connection-sharing-ics-setup-in-vista/](http://www.windowsreference.com/windows-vista/step-by-step-internet-connection-sharing-ics-setup-in-vista/)

[IMG]http://img46.imageshack.us/img46/8333/75096873.jpg[/IMG]

---

