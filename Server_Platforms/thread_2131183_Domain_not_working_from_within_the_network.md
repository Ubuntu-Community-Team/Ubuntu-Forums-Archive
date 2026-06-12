---
title: "Domain not working from within the network"
date: 2013-04-01
forum: Server Platforms
---

### Post by Jacobm001 on 2013-04-01
I am hosting my own server from my home network running the latest version of Ubuntu server.  I'm using Dreamhost as my domain registar and I have no problem connecting to my server unless I'm within my home network.  If I'm on any other internet connection mydomain.org goes directly to my server, but at home it simply times out.  The hostname of my server is set to the domain name.  Any ideas why I'm having issues?

---

### Post by darkod on 2013-04-01
The DNS of the registrar is usually pointed to your public IP, right?

So, on your computer when you try to access the domain, it tries going to the public IP, which means going outside to the internet and then right back inside. Some home routers can't do this.

Since you are on the same local network as the server, and I assume the server has a private IP in your LAN, simply open the hosts file and add an entry for the domain using the server private IP. For example, if the server private IP is 192.168.1.15 you would add:
192.168.1.15   mydomain.com

After doing that, the browser will try to open it using the local IP, which will be much faster too, since it will be using the local LAN. No going out to the internet.

---

### Post by Jacobm001 on 2013-04-01
I have been assuming it's something to do with my router... Most of my devices are portable, my phone and laptop for example.  One of the things I'm using the server for is Tiny Tiny RSS.  If I edit my laptop/phone's hostfile and then go outside the network the DNS change won't allow me to connect.  Any ideas on how to get around that?

---

### Post by darkod on 2013-04-01
Not really. If you are often moving the devices outside your network and trying to access your website from the outside with them too, I guess it will be an issue changing the hosts file. You could keep two versions of the hosts file and simply replace the main file with one or the other.

From what I've read here, if the router can't send the traffic back you can't really do much to change that. So, the hosts file sounds like your only choice, but you are right, it will be an issue when going outside the LAN with the device.

---

### Post by rubylaser on 2013-04-01
If your home router provides DHCP and DNS for your network (it probably does), then you just need to make a host entry on your router that resolves your private ip ([COLOR=#000000]192.168.1.15)[/COLOR] to the hostname([COLOR=#000000]mydomain.com). Any machine on your home network that gets a DHCP address or that uses your home DNS server first will properly resolve to the [/COLOR][COLOR=#000000]192.168.1.15[/COLOR][COLOR=#000000] address for that hostname.[/COLOR]

---

