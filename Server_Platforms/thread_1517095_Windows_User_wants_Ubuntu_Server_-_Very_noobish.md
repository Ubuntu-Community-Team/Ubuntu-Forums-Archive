---
title: "Windows User wants Ubuntu Server - Very noobish"
date: 2010-06-24
forum: Server Platforms
---

### Post by InfectionZero on 2010-06-24
Hello All!
I currently run Win 7 and want to upgrade my computer to a server to accomplish the following...

I have a VPN Service. I want the server machine to connect to a VPN providing a secure connection. Then, I want all the machines in the house (windows based) to connect through the server onto the VPN connection. Hopefully this makes sense. Would it be better to stick to Windows Server 2008 or switch to Ubuntu?

---

### Post by VH-BIL on 2010-06-24
Most ADSL modems should accomplish this without having to set up a server. Do you have one?

---

### Post by doas777 on 2010-06-24
I strongly recommend PFSense for this use. it's a BSD-based router OS that can run off CD or be installed to an old PC with two nics. just set it at your network gateway, configure the VPN, pointing the default route through the VPN. then make sure that all the connections get routed through the pfsense box and you should be good. 

using a full ubuntu install for this seems like overkill, and would introduce additional complexity. PFsense is basically an appliance with one function, so it's somwhat easier to configure.

---

### Post by EmanresuusernamE on 2010-06-24
> **InfectionZero said:**
> Hello All!
I currently run Win 7 and want to upgrade my computer to a server to accomplish the following...

I have a VPN Service. I want the server machine to connect to a VPN providing a secure connection. Then, I want all the machines in the house (windows based) to connect through the server onto the VPN connection. Hopefully this makes sense. Would it be better to stick to Windows Server 2008 or switch to Ubuntu?

To be honest, it doesn't make sense to me.  You say that you have a VPN service that provides a secure connection, that's understandable, but may be a bit paranoid for regular surfing.  You want all of your machines to connect to this service, this is all in your house so it's safe to assume that you're using this for a home office, right? :confused:

If you don't have any off-site computers that you plan on connecting too, ie you only have the computers in your house that you use and no one will be remotely connecting to your house or remotely sharing resources, then I'd say you're being overly paranoid.  While you'll be encrypting the traffic between you and your VPN service, anything past the VPN will not be encrypted unless that website/webservice is also encrypted.

I'm not really sure why you want the VPN service, but you'll need something that will automatically connect to it if you are going to go this route.  There used to be SnapGear routers that could do this for you, they are along the lines of $200-$400.  

Pfsense sounds like it would be good for you, another program to consider would be Smooth Wall.  Both can turn your computer into an appliance that you can easily setup...... Thing is, I don't know if they'll make a connection to your VPN service or not.  I don't use them that much since we have those SnapGears.

---

### Post by doas777 on 2010-06-24
> **EmanresuusernamE said:**
> Thing is, I don't know if they'll make a connection to your VPN service or not.  I don't use them that much since we have those SnapGears.
PFSense will create point to point vpn links for tunnel routing, so you;ll be good there. never worked with smoothwall, but i hear good things about it.

---

### Post by VH-BIL on 2010-06-24
> **doas777 said:**
> PFSense will create point to point vpn links for tunnel routing, so you;ll be good there. never worked with smoothwall, but i hear good things about it.

I used to have a corporate version of Smoothwall in my company, It was great but did not load balance connections at the time so I replaced it with a netgear pro series router.

I still suggest checking to see if your ADSL modem (if you have one) supports VPN so you do not have to dedicate a computer just for a VPN tunnel.

---

