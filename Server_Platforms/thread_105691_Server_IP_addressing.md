---
title: "Server IP addressing"
date: 2005-12-18
forum: Server Platforms
---

### Post by Rajan Varadarajan on 2005-12-18
I have installed ubuntu 5.10 on two machines connected by a 5-port ethernet switch which in turn is connected to a DSL modem/router. On one machine I have installed apache, vsftpd, mysql, etc. - to set up a LAMP environment. The other machine I am using as a desktop.

I didn't configure any IP addresses and let DHCP take care of the IP addressing. How do I address and connect to the server machine from the desktop machine? Do I have to come up with an artificial IP address and set it as a static IP address for the server? Obviously, I don't need to do that for the desktop machine.

Thanks in advance for your help/suggestions.

---

### Post by greenway on 2005-12-19
If you want to keep the sever on a dynamic IP, check it's ip address by typing "ifconfig" into a terminal. This will provide you with it's current IP adrress, however since it's dynamic it will change sooner or later and you will have to look it up again.

You work around this by letting your DHCP server provide your server with the same IP address every time. For this you usually need to know the MAC address of the hosts which needs the same IP address all the time (this can also be found using the "ifconfig" command). Then you will have to configure your DHCP server to tide the MAC address of your server to one and the same IP address. The way to do this depends on your DHCP server (in this case your DSL modem/router). You will probably have to enter it's configuration application via a browser and look for the DHCP section.

If you need anything more, just post it here.

-mattijs

---

