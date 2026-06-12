---
title: "virtual hosts help"
date: 2011-06-30
forum: Server Platforms
---

### Post by LaserBoi on 2011-06-30
Hi Everybody,
I know there are many posts regarding virtual hosts, I have read many of them.
I cannot get virtual hosts to work no matter what I try.
I have followed several tutorials, I have tried host file entries, I have tried the simplest conf file with <virtualhost> directive, to copying the default conf and making the directory changes. Nothing seems to work.
I have tried a fresh install and then the configs, still no go.
When I set up Ubuntu I also instal MySQL, PHP5, and phpMyAdmin.
I cannot think of anything else. I am wondering if virtual hosts need to be setup on Apache2 before installing the rest of the PHP software?
When I do a apache2 vhost dump I see my 2 virtual hosts as well as the default and I get syntax OK. All your help is greatly appreciated. 
Thanks
<M>
 
I forgot to mention I make the config files in sites-enabled and use the a2ensite command to enable them and of course restart apache2.

---

### Post by SeijiSensei on 2011-06-30
How are you handling name resolution?  What do you enter into a browser's address bar when accessing these hosts?  The name you use must match one of those in the VHost's ServerName or ServerAlias files.

That's why it's called "NameVirtualHost" :D

---

### Post by LaserBoi on 2011-06-30
for name resolution I am using an existing domain name that already has DNS entries to resolve to my public IP. I currently have a windows server running the website.
for the sake of this help lets say my domain is XYZ.com. I have entered servername as XYZ.com and serverAlias as [www.XYZ.com]("http://www.XYZ.com")
 
I have forwarded port 85 to port 80 on the ubuntu server so I can keep my original site up on port 80. I can enter the trueIP:85 and reach the default page, if I enter [www.XYZ.com:85]("http://www.XYZ.com:85") the browser just times out.
I can enter the trueIP:85/phpmyadmin and reach that ok as well but if i enter [www.XYZ.com:85/phpmyadmin]("http://www.XYZ.com:85/phpmyadmin") it times out as well
 
If I take the old server offline and and replae it with the ubuntu server so then I am just using port 80, again I can get the default page by entering the trueIP but it also shows me the default page when I enter [www.XYZ.com]("http://www.XYZ.com")
Thanks,
<M>

---

### Post by volkswagner on 2011-06-30
Is your windows server on the same LAN as your Ubuntu server (same public ip)?

Can you explain more detail about forwarding port 80 to 85, how does traffic still go to the windows server? 

What does your virtual host directive look like?

Since you want port 85 in the url I believe you will want the directive to look like this:

```
<VirtualHost *>
```

---

### Post by LaserBoi on 2011-06-30
Guys I have solved the issue, I will explain. But first to answer volkswagnr about the port forwarding.
 
Both servers are on the same LAN but with different IP's of course. The piblic IP comes into the router as you would expect. POrt 80 is open and pointed to windows server. In the router there is also port forwarding. This can bu used for example when you have multiple servers on the LAN and you want you use remote desktop to see them but you don't want to change the ports in the server. you can tell it that when the public IP with port xxx comes in I want that to be forwarded to port 3389 on this IP (192.168.1.50), then I can tell it when public IP with port xxy comes in I want that fowarded to port 3389 on a different IP (192.168.1.55) etc. This works very well for managing mutiple servers behind the firwall.
So the port forward of 85 to 80 for the Ubuntu server allows me to set it up with port 80 and not change that at all, just :85 at the end of the IP when I access from outside.
 
Ok now onto the solution for the virtual host. We have 2 domain names coming to in. The old one and the new one. the old one has DNS A records pointing to our public IP, the new one however was setup with some type of forward from one name server at a different company to the old name server. This si causing the problem. When I added Aliases for the old domain name to the virtual host config and enter the old name it goes to the correct folders and all is happy. So I have been testing with the new domain name and for wahtever reason the name is not correct when it comes into Ubuntu. Don't know what it is but it doesn't work.
I didn't buy the new domain or setup the DNS entries for it so I didn't know this was happening.
 
I expect when I correct them all will be happy.
 
I hope this makes sense to everybody.
 
Thanks allot for helping so quickly.
 
<M>

---

