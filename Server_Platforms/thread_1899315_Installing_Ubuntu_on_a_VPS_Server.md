---
title: "Installing Ubuntu on a VPS Server"
date: 2011-12-23
forum: Server Platforms
---

### Post by 1cookie on 2011-12-23
hi

So far in my web development experiences Ive always used shared hosting solutions. It's relatively simple to FTP some PHP files to the server and your away. Taking the next step; I'd like to find out a little more about VPS servers and configuring Ubuntu to run a LAMP stack for my website needs.

A couple of preliminary questions:

Let's say Ive found a host that will provide me with a basic package on a virtual server:

 with let's say 50GB webspace, 1gb RAM, no control panel for £30 a month


Would I get a static IP address with the deal, or is this negotiable from company to company?

Would i need to configure DNS myself? How would i configure DNS? How would I map a static IP to [www.mydomain.com]("http://www.mydomain.com") say?

I'm not likely to have physical access to the host machine. Would the host pre install Ubuntu for me using an image file or something? 



I have more questions (MySQL, PHP, FTP, Apache, Email servers) but for now this is where i start my VPS server journey. :)

---

### Post by spynappels on 2011-12-23
As you say, each provider varies, but there are some things which are fairly standard to them all.

Firstly, for the money you're talking, 512MB RAM is more reasonable, and plenty good enough for a basic webserver.

You will find that most providers will do a vanilla OS install for you, they basically copy an image to the VPS. You then access this and do what you like with it. It's up to you to make sure you secure it (think firewall etc) and to make sure it is patched etc.

Your DNS record will often be handled by your domain registrar, and you just set up an A record pointing to the public IP your VPS provider gives you. They will normally give 1 static public IP address, if you need more you'll have to pay extra in most cases.

There are a few points I'd suggest, as someone who has administered a lot of VPS servers.

Put the VPS on a simple VPN like OpenVPN, you can even use the VPS as the VPN server and connect to it from whatever workstation you are working on. Then firewall (inbound) every port except 80 and/or 443 (and your VPN port if it is a VPN server), this means that you won't have script kiddies hammering your box constantly. It will mean that the number of attack vectors has been considerably reduced to just whatever comes in on ports 80 and 443, and coupled with Apache/MySQL hardening and good coding practices will make your server less likely to be compromised. Do all administration through your VPN tunnel, including FTP of pages to the server.

Stefan

---

### Post by 1cookie on 2011-12-23
hi, and thanks for the tips.

> **spynappels said:**
> 

you just set up an A record pointing to the public IP your VPS provider gives you. 

The A record...does this reside on the Ubuntu server somewhere?

> 
Put the VPS on a simple VPN like OpenVPN, 
How do these two fit together exactly? Download a software package (from OpenVPN) that's compatible with my server OS; then buy [$5] a license? Am I correct in thinking that a paid host (generally) will be using a 64bit architecture?

---

### Post by spynappels on 2011-12-23
> **1cookie said:**
> The A record...does this reside on the Ubuntu server somewhere?
This is a setting/record set up by the people who you bought the domain from normally, they will have wizards to point your domain to your public IP

> **1cookie said:**
> 
How do these two fit together exactly? Download a software package (from OpenVPN) that's compatible with my server OS; then buy [$5] a license? Am I correct in thinking that a paid host (generally) will be using a 64bit architecture?

There are different ways of doing this, the cheapest is to install the OpenVPN package on your VPS server, configure it, and get an OpenVPN client for your laptop/desktop. This will cost you a grand total of $0. There is some configuration to do, but there are some good guides out there to follow if you are confident enough to do this. Check out [www.openvpn.net](www.openvpn.net) for a start. You want to look at the Community tab.

I should just emphasize how important it is to follow some basic rules if you are running an Internet facing server, to avoid being compromised and having your server used to attack others. You should read the sticky threads in the Security forum to get a basic understanding, and if you are not sure, ask here. 

Above all, have fun learning, we all started much the same way.

---

### Post by 1cookie on 2011-12-23
> **spynappels said:**
> 

install the OpenVPN package on your VPS server, configure it, and get an OpenVPN client for your laptop/desktop.

So these two pieces of software talk to each other in effect?

> 

I should just emphasize how important it is to follow some basic rules if you are running an Internet facing server, to avoid being compromised and having your server used to attack others.
Indeed, I wouldn't want my server to be hijacked. That would be bad.

> 
 You should read the sticky threads in the Security forum to get a basic understanding, and if you are not sure, ask here. 
For sure. I will.

> 

Above all, have fun learning, we all started much the same way.
Yes, it''s fun. There's a lot of food for thought on openvpn.net for sure.

---

