---
title: "First Server! / First time linux user!"
date: 2005-09-08
forum: Server Platforms
---

### Post by Rollo Tamasi on 2005-09-08
Hi lads,

Yesterday i installed Ubuntu on my old laptop in the hope of creating a server which will host one of my websites and be accessible on the internet. But i'm a complete newbie at linux, ubuntu is the first ever linux client that i have ever used.....and i love it so far  :razz:   But i need to gather some info on how to actually create the server,  (some of the questions i'll be asking have probably been asked a thousand times before so excuse my ignorance!).

So far i have installed....
php4
apache2 & 
mysql 

I have a fixed IP also with my ISP. Do i need to buy a domain and setup dns address also......(probably stupid questions I know, but i have to ask!). 

What else do i need to do, any guidance would be greatly appriciated. Thanks guys

---

### Post by emperor on 2005-09-08
I would NOT recommend a laptop as a webserver platform.

Yes, you will need to purchase a domain name!

I also would recommend a 3 port router with one port dedicated as a DMZ. Buy or use old 486 or above with ready made router based distro; several to choose from: M0n0wall, and ipcop (two I have tried and use!)

BTW, You can get web hosting (Linux O/S) for as little as $0.99 a month. I host my website for less than $12/year. [http://www.linxos.com](http://www.linxos.com)

Checkout: [http://www.ultrasurge.com](http://www.ultrasurge.com)  
package is: ULTRAcpanel 250
Annual cost is: $11.88

---

### Post by DJ_Max on 2005-09-08
First time Linux user + Managing server = owned!!

Honestly, I've seen to many people new to Linux use it as an OS, and get hacked because they forgot to secure their /tmp, or forgot to hardend PHP. As a matter of fact, I've known desktop Linux users who try to run a server but fail, as it's a different ball game.

Also, hosting a site from your non-rededunant, probably slow internet connection is a bad idea, and probably against your ISP's Terms of Service, and will get you kicked. Even if they do, unless you have a nice upload speed, around 10mb, your site will be terribly slow.

Setting up your own DNS is a pain for normal server administrators, so I can only imagine how unorthodox it will be, and most people will benifit from a third-party DNS service, such as some domain name providers provide.

---

### Post by Rollo Tamasi on 2005-09-08
Thanks for the replies lads, i really only want to do this for testing purposes (and maybe as a college project for my IT/Network class).

So far i'm doing fine (/me thinks so anyway), i have a netgear adsl router and i'm forwarding the port addresses to my fixed IP so that when i type the ip into a browser it will display the content in the apache directory (thats the plan), i dont mind if its slow, i'm not really concerned about the speeds tbh ( i have a 3meg connection), i just want to get more involved in server techie stuff.

The more i get into the more i'm considering building a dedicated pc instead of the crappy laptop (20GB H/D, 128mb, P3 1GhZ, YONKS!).

At this early stage i'm still open to any advice that knowlegdeble ubutunu users may provide me with. 

----------
Cormac

---

### Post by DJ_Max on 2005-09-08
[QUOTE=Rollo Tamasi]Thanks for the replies lads, i really only want to do this for testing purposes (and maybe as a college project for my IT/Network class).
[/QUOTE]
Thats all I needed to hear. With God speed then.

---

### Post by Rollo Tamasi on 2005-09-09
[QUOTE=DJ_Max]Thats all I needed to hear. With God speed then.[/QUOTE]
 Thanks DJ Max! You mentioned security in your first post, could you maybe expand on what is required to make the server water tight?

A friend recommended that i get a firewall from [www.smoothwall.org](www.smoothwall.org) , how does firewall compare to the deafult one that comes with ubuntu, firestarter?

---

### Post by DJ_Max on 2005-09-09
Firestarter is geared toward the desktop, as it's a GUI to iptables. I've used Shorewall, and it's pretty simple. But all Linux firewalls essentially do the same thing, that is, make it easier to modify iptables. There's a even simplier firewall, but can't think of the name.

Securing your server is a process. An important, part is securing your /tmp directory, especially when running things like PHP or MySQL. 

PHP isn't the most secure, so leaving things like Register Globals off is a good thing.
You want to install a RootKit hunter. For example, [http://rootkit.nl](http://rootkit.nl)

[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation) Look at Security.
You don't have to worry about viruses affecting your machine, but you can install an Anti-virus for when getting sent Windows email viruses that can affect Windows desktop users when grabbing email from your server.

On my server, I have anacron setup w/ portsentry, hostsentry to check for suspicious activity, such as failed logins, large log files, MySQL & PostgreSQL corruption, etc..

Ubuntu takes an unorthodox approach, and disables the root account, and uses [I[sudo[/I], which is very good. And I would suggest that with every distribution you do the same.

Also, for general Linux security models, take a look at grsecurity.net and PaX. You don't have to install it, just take a look at the features.

If you have any more security questions, let me know, and I'll be more than happy to help.

---

### Post by Rollo Tamasi on 2005-09-10
mmm...this morning i cant seem to access my ubuntu server from any pc's. When i type in the IP of the server into my windows pc (192.168.0.3 or [http://my.fixed.ip](http://my.fixed.ip) from non-local pc's) the connection just times out. I have checked the network connections on the ubuntu pc, and everything seems fine there (/me thinks). I can ping 192.168.0.3 with no problems.

I did switch off the ubuntu pc last night....could have something to do with it...do i need to set something up again. Any help would be greatly appriciated.

Thanks lads.

---

### Post by DJ_Max on 2005-09-10
Did you setup a firewall? If so did you allow port 80 incoming connections?

---

### Post by Rollo Tamasi on 2005-09-11
[QUOTE=DJ_Max]Did you setup a firewall? If so did you allow port 80 incoming connections?[/QUOTE]

As far as i can tell the firewall is allowing all traffic. I couldn't see anything been blocked at all. I'm using the default firestarter firewall, in the events tab there is nothing listed in the blocked connections list. (maybe i'm missing something? please advise if i am, thanks)

I'm pretty sure it has something to do with the network connections setup on the ubuntu box. I have two options for network connections, the first one is called "lo" which is the default one (/me thinks its the default one anyway), now i presume its called lo because its a local connection? is that right? The second connection i have is one called "eth0", this connection can be fully configured. It is set to DHCP ( it keeps setting itself to DHCP which i think is odd because should it not be set to a static setting?

I'm using port forwarding on my router to 192.168.0.5 (the 192.168.0.5 ip is the ubuntu box btw). When i enter in the  IP (192.168.0.5) into the connection settings and use the subnet mask 255.255.255.0 and leave the gateway address blank, i can not get an internet connection! 

What should the correct settings be, i realise there are only so many variations that can be used and i think i have tried them all. Here are two screen shots of the network connection if it helps make anything clearer? Hopefully it will!  :)
 
Thanks for your help thus far, DJ Max, really appriciate it!  :) 

[[IMG]http://img386.imageshack.us/img386/2116/dnssettings1mu.png[/IMG]](http://imageshack.us)

[[IMG]http://img386.imageshack.us/img386/8957/connectionsettings9qv.png[/IMG]](http://imageshack.us)

---

### Post by technomancy on 2005-09-13
I'd just like to chime in to say that running your own server is not a bad idea at all, as long as it's just a personal project. I do it from my DSL line with a 1GHz Dell sitting under my desk, and I've had a great time of it. Of course, the bandwidth is not fantastic, so it's a touch slow accessing it away from home, but it gives me the opportunity to play around and install software that I'd never be able to get with a hosting company.

For instance, I was able to use Rails months before it become mainstream enough to get installed on hosting companies. I can have as many Subversion repositories as I like, and I can start to use cool bleeding-edge programs like Hula before they are mainstream.

For DNS I use zoneedit since I wouldn't want to be responsible for DNS myself. They are free if you are under a certain amount of bandwidth. (You have to buy the domain name, but they will let you use their DNS servers.) The other caveat is that I wouldn't recommend running a mail server since your DSL does not have guaranteed uptime. You really don't want to lose email without knowing about it--trust me! Running a mail server is too important to learn as you go.

I'd just like to point out that those smiley icons are just ridiculous.

---

### Post by eco751 on 2005-09-13
DHCP is dynamic to get your IP from the network.

Lo is for **lo**opback.

---

### Post by Glut on 2005-09-14
The gateway should be set to the ip of the router. A better solution would be to set the router to assign the server a static ip and have the server use a dynamic (DHCP) address. This way the correct settings will always be used.

---

### Post by Rollo Tamasi on 2005-09-16
[QUOTE=Glut] A better solution would be to set the router to assign the server a static ip and have the server use a dynamic (DHCP) address. This way the correct settings will always be used.[/QUOTE]

Thanks for the reply, at the moment the router has a static IP address assinged to it, and the box is using the IP 192.168.0.5, the router is port forwarding to the 192.168.0.5 IP.....is that the correct setup so that the box goes live on the net?

---

