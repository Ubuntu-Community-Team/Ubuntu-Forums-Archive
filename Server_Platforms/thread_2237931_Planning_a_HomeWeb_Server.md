---
title: "Planning a Home/Web Server"
date: 2014-08-04
forum: Server Platforms
---

### Post by hipnerd on 2014-08-04
Hey guys,

I recently moved to a new house that has fiber to the door. I now have the bandwidth to run my own web server. I have several hobby sites that I would like to host myself. 

I picked up a used Dell rackmount server with dual Xeons, 4GB of RAM, dual Gigabit ehternet ports and a RAID 10 SCSI array for $80. I've checked and port 80 is unblocked, so I think I am good to go.

I could use help setting things up, though. I want to do things right and I want to leverage the maximum benefit from the server.

Currently, I have: 

[LIST]
[*]one desktop running Win7 Home
[*]one laptop running Ubuntu 14.04 
[*]one Seagate NAS drive acting as a media server
[*]one Intel Atom PC running linux and XBMC
[*]one PS3, one Tivo, one SMART TV, etc.
[/LIST]

Currently, I have the Internet going into a Dlink router that handles DHCP for the network connected to a Gigabit switch that distributes to all my various PCs, devices and printers.

If I am setting up the server to act as a web server, do I place it "between" the Internet and the router? If there is an up-to-date guide available, I would love to read it. I tried the link to the Ultimate Server in the sticky thread and it was broke, and most of the other guides I am finding with Google are to set up a web server for internal use only, or they are for Ubuntu 9.10 or something and I am concerned that they are badly out of date.

I appreciate any help you can offer.

---

### Post by TheFu on 2014-08-04
[http://howtoforge.com/](http://howtoforge.com/)
[http://ubuntuserverguide.com/](http://ubuntuserverguide.com/)

That should get you started.

And just because something is possible, that doesn't mean it is a good idea in any specific situation. Security architecture matters.

---

### Post by brent1975 on 2014-08-05
Hipnerd - It is never a good idea to put your server or computer at that point in front of your router/firewall.... The only reason I can see someone doing this is for trouble shooting. Having your router assign IP's via DHCP is great if all you have is a couple laptops and desktops. However, when you throw a server in the mix you need dedication. I would recommend setting a static IP on your server. From this all you need to do is forward ports through your router to point to your server.

---

### Post by hipnerd on 2014-08-05
That was the piece of information missing from most tutorials. I was not sure if there was a good reason to put the server in front of the router. I've already set static IPs on everything that is hardwired to the network, and I know how to forward ports.

I'm going to plow ahead and set this thing up then figure out what mistakes I have made. I appreciate the advice.

---

### Post by brent1975 on 2014-08-05
You have pretty much the same setup I do... I have a few more PC's and laptops but I also have a house full.. Here is how I would approach the server.
1. Install your headless server. I am using 12.04. I never run the latest. ( I don't care for bugs all that much so I let the new versions get wet a little)

security! security! security!

2. look at your router.. Make sure all ports are closed or you know what they are for. (Never fails to see a port and you ask your self what the heck was that for)
3. Think about changing the SSH port on your server. It's very simple to do with [http://forums.kc-linux.com/index.php/topic/51-how-to-change-default-ssh-port-in-ubuntu/](http://forums.kc-linux.com/index.php/topic/51-how-to-change-default-ssh-port-in-ubuntu/) 

****Optional but suggested****
4. Next I would suggest setting up IPTABLES firewall. [http://forums.kc-linux.com/index.php/topic/18-iptables/](http://forums.kc-linux.com/index.php/topic/18-iptables/)

5. Use samba and point to your NAS for the shares. You will have to change the path to the IP of your NAS but should work nicely. [http://forums.kc-linux.com/index.php/topic/28-samba-file-server/](http://forums.kc-linux.com/index.php/topic/28-samba-file-server/)

6. for the webserver (Apache, PHP, MySQL, PHP MyAdmin) [http://forums.kc-linux.com/index.php/topic/40-installing-apache-php5-mysql-and-phpmyadmin/](http://forums.kc-linux.com/index.php/topic/40-installing-apache-php5-mysql-and-phpmyadmin/)

There is a lot of other things that you can add and or configure but this will get you started. Hope this helps.

---

### Post by TheFu on 2014-08-05
When I mentioned security architecture previously, I should have provided more data that you can follow-up. 
Security is layered. NEVER trust just 1 layer to provide security - always have multiple layers - "belts AND suspenders" is what we call it. You want both.

It all starts with network security. HW firewall with minimal ports opened.

SW firewall on any systems with exposed services, so you can control, limit, log traffic and look for any unwanted stuff.
Block any malformed packets or requests.  I block anything with "php" - since anyone making that request is obviously trying to crack my network. Anyone trying to get to "setup" or "admin" from the internet needs to be blocked for 10 days min too.
I use a reverse proxy to firewall and filter unwanted requests before they ever touch the real server(s).
Don't allow any services onto the internet that don't absolutely have to be available there. 
NEVER allow any DB to be directly accessed over the internet - for example. 

Don't run a web interface tool to "simplify" management of the server, until you KNOW how to do it all from the command line. Why?  Well, chances are those are the primary target for anyone hacking into your system.  I've met the cPanel guys and they are sharp, but they can't prevent much if that system is available on the internet for anyone else to try and hack. Same goes for MySQL admin web-tools. If you need those - you aren't ready.

So ... google "network security architecture" and look for systems architecture diagrams online.  Ratemynetwork has a bunch - the ratings seem more about pretty pictures than security/capability, so beware.

Backups, backups, backups - such that you can recover from being hacked a few weeks earlier. If you run php webapps - be prepared. If you load plugins - BE PREPARED.  Review the "server" forum here for what other people are doing to recover from being hacked.  Do NOT believe it won't happen to you. Be prepared.

Oh - and if you are coding, be certain to join your local OWASP group and memorize their top 10 list.

Don't forget to have fun.

---

### Post by hipnerd on 2014-08-05
1. Done

2. I'll check it using some external tool. I know they are out there. 

3. Seems easy enough, but for my own information: Do I need to do this if I am not forwarding SSH to the server? I can get their on my internal network just fine. And if I want to make a "backdoor" for myself, could I not have the router forward some random port to port 22 on the webserver? Just thinking things through and trying to learn.

4. Good plan.

5. That NAS is a little bastard. It's a Seagate GoFlex that is much harder to get mapped in Linux than my old generic Buffalo NAS. This will teach me to buy nice things.

6. Installed LAMP with the OS. Good call on phpmyadmin. I would have noticed I needed that the first time I installed WordPress.

---

### Post by sandyd on 2014-08-06
> **hipnerd said:**
> 1. Done

2. I'll check it using some external tool. I know they are out there. 

3. Seems easy enough, but for my own information: Do I need to do this if I am not forwarding SSH to the server? I can get their on my internal network just fine. And if I want to make a "backdoor" for myself, could I not have the router forward some random port to port 22 on the webserver? Just thinking things through and trying to learn.

4. Good plan.

5. That NAS is a little bastard. It's a Seagate GoFlex that is much harder to get mapped in Linux than my old generic Buffalo NAS. This will teach me to buy nice things.

6. Installed LAMP with the OS. Good call on phpmyadmin. I would have noticed I needed that the first time I installed WordPress.

3. Port scanning will easily find that open random port. Security through obfuscation is never a good security method.
If you *really* need to have ssh on a public IP, I recommend going the SSH-key way.

1. Generate a SSH Key
2. Use ssh-copy-id to copy the key to the server 
3. Disable SSH logins via /etc/ssh/sshd_config
4. Install some kind of brute-force detector, either fail2ban, or CSF if your looking for a full firewall solution. Make sure you understand what CSF does before you turn it on - otherwise your just locking yourself out.

---

### Post by hipnerd on 2014-08-07
I realized I am missing one component to make this work: nameservers.

Every other time I have set up a website, I use the nameservers provided by the ISP. Barring creating my own nameservers, is there a way to use free or inexpensive nameservers on the Internet to point to my home server?

---

### Post by TheFu on 2014-08-07
Yes. Google "dynamic dns"
* dyn.com
* no-ip.com
are a few options, but there are probably 50 others.  I use both of those. Many routers have built-in support to manage updates for IP addresses that change, so life is easier if your router is configured to manage the updates.

---

### Post by hipnerd on 2014-08-07
I am paying an extra $5 per month for a static IP.

---

### Post by TheFu on 2014-08-07
> **hipnerd said:**
> I am paying an extra $5 per month for a static IP.

If you have a static IP, then you just need a domainname (registrar) and authoritative DNS to tell the registrar who can speak for your domain.  These can be 1 provider or 2 - it is up to you.  I prefer to keep them separate.

---

