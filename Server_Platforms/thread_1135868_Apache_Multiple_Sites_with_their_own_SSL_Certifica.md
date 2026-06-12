---
title: "Apache: Multiple Sites with their own SSL Certificates"
date: 2009-04-24
forum: Server Platforms
---

### Post by terazen on 2009-04-24
How can I set this up to work?  Earlier today I had 2 secure sites using 2 seperate ssl certs and everything worked.

After lunch I setup a new virtualhost on port 80 and restarted apache only to get this error:
You should not use name-based virtual hosts in conjunction with SSL!!

Only 1 of the ssl sites is working now.  It is very slow unless I disable the other ssl site with a2dissite.  

The new ssl site was moved off of a windows box and now I'm thinking it has to move back unless I can get this working very quickly.  From what I've read earlier today apache wants multiple ip addresses for this to work, but I don't have that.

Is it possible for this to work on 1 ip address?

The server is Ubuntu Hardy.

---

### Post by HermanAB on 2009-04-24
Howdy,

You need a static IP address for each SSL web site.

---

### Post by BkkBonanza on 2009-04-24
The general answer is that you do need an separate ip for each ssl certificate used. That's by the very nature of the way the ssl protocol works.

There are complicated workarounds and tutorials out there but they involve compiling apache and patches etc. Googling will find them but I think overall you're probbably better not to go that way unless you have no choice. I don't think this is specific to Linux though so if you have multiple ssl on windows you should be able to move the relevant ips over to the linux box and use them there. Unless you're moving from one isp/data center to another at the same time.

---

### Post by terazen on 2009-04-27
Thanks for the information.  I got a 2nd ip but still getting the firewall rules changed.

There has been a problem with the virtual hosts though.  Maybe someone can help me figure this out.

I have an /etc/apache2/conf.d/virtual.conf file with this:
NameVirtualHost *:80
NameVirtualHost *:443

In /etc/apache2/sites-available/ I have various files like this:
#First website
<VirtualHost *:443>
<VirtualHost *:80>

#Second website
<VirtualHost 2nd.ip.address.here:443>
<VirtualHost 2nd.ip.address.here:80>

#9 other sites
<VirtualHost *:80>

When I used the ip address for VirtualHost on the 1st website ALL SITES on that ip address pointed to it.  When I changed it back to *:80 for the first site everything works as expected.  Is there a better way to organize this?

---

