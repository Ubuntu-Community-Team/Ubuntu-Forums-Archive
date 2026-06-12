---
title: "Gateway server in desktop"
date: 2007-09-10
forum: Server Platforms
---

### Post by Mario_Lib on 2007-09-10
is there a way to configure ubuntu desktop as internet gateway in GUI environment without any comands ??

---

### Post by NewbieNik on 2007-09-10
possibly the easiest way would be to use firestarter (Firewall GUI) and Squid proxy server with Webmin (Web-based control panel) then set that bases IP address as the gateway for the network.
In fact if you install dhcp3 server you could specify the routers option to point to the lan IP address for all devices requesting Ip addresses.

---

### Post by koenn on 2007-09-10
yes. 
install iptables and a gui front-end for them, eg FireStarter

Then configure firestarter. 
Depending on what sort of "gateway" you have in mind, you will (probably) want to tell Firestarter to do "MASQUERADING" or "NAT"

If you want a serious gateway, you might also want to install eg a web proxy (squid), but I don't know about GUIs for that, except maybe Webmin. 

If you want a really serious gateway, you'll forget about the "no commands" requirement and just edit a config file or two. Its a lot easier to make an accurate description of what you want in writing than it is by pointing and clicking at general, pre-defined options and combining them into something that hopefully does what you think it does.

edit : hmm, someone beat me to it :)

---

### Post by KCPokes on 2007-09-10
The thing to keep in mind is that a good gateway has very limited services, the basics, to reduce any security exploits.  By running a desktop install to configure the services with a GUI, you somewhat defeat some of that purpose.  

If you truly want to be able to configure a gateway machine, using GUI, you may want to look into either Smoothwall (smoothwall.org) or IPCop (ipcop.org).  Both are firewall solutions running on their own linux distros, but they do have documentation on how to compile the firewall onto the distro of your choice.  

This is not to say you can't move forward with running a desktop install as your gateway, but just keep in mind that a gateway sits on the internet directly (typically, of course it depends on how you use your gateway), thus an unattended service can lead to some very unexpected results.

---

### Post by Mario_Lib on 2007-09-12
Thanks alot for ur help

I just needed something quick just few clicks and I’m done I don't need to read tons of documentations and searching lots of websites i really wish i GUI edition of ubuntu server coz things doesn't need to be so complicated to work good and secure

---

### Post by houston.hemi on 2007-11-26
> **NewbieNik said:**
> possibly the easiest way would be to use firestarter (Firewall GUI) and Squid proxy server with Webmin (Web-based control panel) then set that bases IP address as the gateway for the network.
In fact if you install dhcp3 server you could specify the routers option to point to the lan IP address for all devices requesting Ip addresses.

I'm thinking of setting up my Ubuntu desktop as a firewall/ftp solution.  Would it be best to configure the Ubuntu desktop in front of my linksys router (direct to the internet), then host clients behind the Linksys?

I have a static IP address and I will need customers to access the ftp site as well as access software license files.  I'm thinking of the setup similar to the DMZ version in the Windows world.  Would FIRESTARTER and SQUID solve this topology??

Thanks,

Houston.Hemi

---

