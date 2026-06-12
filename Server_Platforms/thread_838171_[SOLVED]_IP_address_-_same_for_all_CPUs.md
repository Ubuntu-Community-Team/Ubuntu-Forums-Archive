---
title: "[SOLVED] IP address - same for all CPUs"
date: 2008-06-23
forum: Server Platforms
---

### Post by weryl on 2008-06-23
Good morning yall,

I'm having a strange problem with my machines at home: they all have the same external IP address (when I look it up from [www.whatismyip.com](www.whatismyip.com) or similar sites). I administrate my server using either SSH or Webmin and it works fine when i use the internal IP address (192.168.1.101) but that makes my server pretty useless if i have to be local to access it...

Heres my setup:
server:  ubuntu server 8.04
         webmin, samba, ssh, xorg (not used, except to query for external ip)
pc:      winxp SP3
router:  linksys

Btw i dont know if its related but i tried setting my server as dynamic and static ip address (both were ...101) but i couldnt even go on the web with a static ip (though the local network worked fine).

Thanx

Mike

---

### Post by Cappy on 2008-06-23
This is just how it works when you hook up multiple computers to one internet connection through a router.

You can change SSH or webmin or whatever's ports on each computer to something different and then forward each port to the internal network IPs on the router (probably under a "Port Forwarding" tab on the router's configuration page, which is normally located at 192.168.1.1 or 192.168.0.1).

You can also have it so that one computer can be contacted by SSH by the outside (the internet) and then ssh from that computer to all the rest on your network. To access webadmin on other computers you would use SSH tunneling.

---

### Post by weryl on 2008-06-23
Still, I dont understand why my server would loose its access to the internet simply because I set the IP to static instead of dynamic (through webmin) for eth0.

---

### Post by +Eric on 2008-06-23
nvm.

---

### Post by weryl on 2008-06-23
Hum so that's problably my problem: I set the static ip to ...101 which is in the dhcp range of my router. The other options (gateway, mask, bdcast, etc) seem fine, but ill confirm that when i get back home.
Thanx alot

---

### Post by +Eric on 2008-06-23
I don't know much about the specifics of your setup.

In fact, I'm not sure I even understand what you're trying to do completely.

You've got several machines behind a router? And one is a server? Only the server you want to admin remotely over the net? And you want to set up static IP's for that machine or possibly all machines? 

What is your router make/model? You may be able to set up the static IP via DHCP using the mac address. In other words, your router would assign the IP that you tell it to, to the server, after seeing it's mac address.

But yes, make sure, you're statically assigned address is outside of DHCP range, unless you're using the router itself to assign the static IP via DHCP, then you may not have to be outside of that range.

For example, on my network, I have three computer that are wired to the network full time. Two laptops that either get wired or use wireless. My DHCP server assigns addresss from 192.168.0.100 to 192.168.0.200. I have it statically assign IP's to the known pc's on the newtork (3 desktops, 2 laptops) vian DHCP that way they always have the same IP's (I do 192.168.0.2, 192.168.0.4, etc for that). However it makes moving them to another network (esp. the laptops) easy since I don't have to go back in and set them to DHCP again.

This all hardly matters for a server, since it's very likely it won't get moved.

Then you can just do a simple port forward on your router and you're gtg.

---

### Post by weryl on 2008-06-23
> **+Eric said:**
> I don't know much about the specifics of your setup.
In fact, I'm not sure I even understand what you're trying to do completely.
You've got several machines behind a router? And one is a server? Only the server you want to admin remotely over the net? And you want to set up static IP's for that machine or possibly all machines?

Ok i'll try to detail my setup. I do have several machines behind a router. Most of them are winxp PCs/laptops and use dynamic IPs. One of em, however, is a ubuntu server with a hdd shared locally with samba and another to become accessible externally via ftp.

I use webmin and putty (SSH) to admin the server locally (192.168.1.101...) but i dont know exactly how to do it externally (ie WAN). Im not even sure if i need a static ip address for that or if i can simply setup my router to forward the right ports to the machine using either its name or mac addr.

---

### Post by uidb4056 on 2008-06-23
> **weryl said:**
> Ok i'll try to detail my setup. I do have several machines behind a router. Most of them are winxp PCs/laptops and use dynamic IPs. One of em, however, is a ubuntu server with a hdd shared locally with samba and another to become accessible externally via ftp.

I use webmin and putty (SSH) to admin the server locally (192.168.1.101...) but i dont know exactly how to do it externally (ie WAN). Im not even sure if i need a static ip address for that or if i can simply setup my router to forward the right ports to the machine using either its name or mac addr.

In addition to that you have to be sure (ask your ISP provider ) that you have a fixed external address in your router, normally the ISP gives to the routers dynamically assigned IP's and if you want a fixed external IP you probably have to pay a little bit more.

---

### Post by +Eric on 2008-06-23
Very likely, the server will need a static IP behind the router. Then you can use that IP to do a port forward from you public IP to the private one!

Should work from there!

Also, that is a good note about the external IP not being static, uidb4056.

You may want to see if you're router is capable of updating something like:

[http://www.dyndns.com/services/dns/dyndns/](http://www.dyndns.com/services/dns/dyndns/)

If not, you can certainly have one of your windows boxes update it, via a small client.

---

### Post by weryl on 2008-06-23
Aaaah now i really got it working. Gotta tell how though:

Being rather pissed at webmin for not getting the static ip to work (couldnt go on the net), i finally set my netmask to 255.255.255.255 (i know, totally stupid, my bad). so then i edit my /etc/network/interface manually and found out that webmin messed that file completely.

i reconfigured it to look like this :

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.2
gateway 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

and now its working flawlessly. btw webmin didnt set the gateway and set the network to 192.168.1.2 (same as address).

yay!

---

