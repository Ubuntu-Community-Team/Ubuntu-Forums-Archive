---
title: "Web Server"
date: 2006-10-21
forum: Server Platforms
---

### Post by mzracer360 on 2006-10-21
I installed the Ubuntu Dapper LAMP Server on our extra pc. I setup a static IP, and have port 80 opened in our router to that ip. I also setup an account with dyndns. When i give people the URL that i setup, they tell me they get a "page cannot be displayed", but the computers in our network can see it. I have a CS:S server installed on the server with the necessary ports opened, but people are able to join it. My external IP is 24.255.223.134, which is what dyndns is set to.  Am i missing something? Why can't people out of our network see it? 

I have 3 pages to test:
[http://mzracer360.game-host.org/testphp.php](http://mzracer360.game-host.org/testphp.php)
[http://mzracer360.game-host.org/forum/](http://mzracer360.game-host.org/forum/)
[http://mzracer360.game-host.org/gallery/](http://mzracer360.game-host.org/gallery/)

---

### Post by az on 2006-10-21
> **mzracer360 said:**
> I installed the Ubuntu Dapper LAMP Server on our extra pc. I setup a static IP, and have port 80 opened in our router to that ip. I also setup an account with dyndns. When i give people the URL that i setup, they tell me they get a "page cannot be displayed", but the computers in our network can see it. I have a CS:S server installed on the server with the necessary ports opened, but people are able to join it. My external IP is 24.255.223.134, which is what dyndns is set to.  Am i missing something? Why can't people out of our network see it? 

I have 3 pages to test:
[http://mzracer360.game-host.org/testphp.php](http://mzracer360.game-host.org/testphp.php)
[http://mzracer360.game-host.org/forum/](http://mzracer360.game-host.org/forum/)
[http://mzracer360.game-host.org/gallery/](http://mzracer360.game-host.org/gallery/)
I cannot reach the url nor the ip address.  Do you have a firewall setting on your router?

By default, your ubuntu box should not be denying anything - if another box on the lan can reach it, someone from the outside should be able to as well.

Unless your ISP blocks port 80.  But if you have a static IP address, this should not be the case, no?

---

### Post by Ronbo on 2006-10-21
Your ISP may block port 80, I know mine does (The also block DynDNS with the supplied D-Link router somehow  Verizon FIOS).  Try editing the ports.conf file in /etc/apache2.  Change the line from 'Listen 80' to 'Listen 8080'.  Then have someone try to access your web server adding a ':8080' to the end.


[http://mzracer360.game-host.org/testphp.php:8080](http://mzracer360.game-host.org/testphp.php:8080)

or by your IP address

[http://24.255.223.134:8080](http://24.255.223.134:8080)

and see if that works.  If it does it's because they do block port 80.

Post back and let me know how you make out.

---

### Post by Ronbo on 2006-10-21
Also after you change the file make sure you chnage the router to forward port 8080 to the internal ip address of the server and you restart apache with 

mylinuxhost:~$ sudo /etc/init.d/apache2 restart

---

### Post by mzracer360 on 2006-10-22
> **Ronbo said:**
> Your ISP may block port 80, I know mine does (The also block DynDNS with the supplied D-Link router somehow  Verizon FIOS).  Try editing the ports.conf file in /etc/apache2.  Change the line from 'Listen 80' to 'Listen 8080'.  Then have someone try to access your web server adding a ':8080' to the end.


[http://mzracer360.game-host.org/testphp.php:8080](http://mzracer360.game-host.org/testphp.php:8080)

or by your IP address

[http://24.255.223.134:8080](http://24.255.223.134:8080)

and see if that works.  If it does it's because they do block port 80.

Post back and let me know how you make out.

Ok, i just did that.  

when I restarted apache2 I got this error:

apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                         [ ok ]

Now that I did that and enter :8080 at the end, I can't even see it anymore.

I go to here
[http://24.255.223.134/testphp.php:8080](http://24.255.223.134/testphp.php:8080)
and get a 
404 Not Found

and if I go here
[http://24.255.223.134:8080/](http://24.255.223.134:8080/)
I get a 
Firefox can't establish a connection to the server at 24.255.223.134:8080.

---

### Post by Ronbo on 2006-10-22
I get the same thing when I restart my apache server.

> ron@mylinuxhost:/etc/apache2$ sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server...
 apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[OK]

Now just to make sure, in you /etc/apache2/ports.conf file the only thing in there is:

> Listen 8080

And you changed your router to forward port 8080 (to the internal ip address of the server) instead of it forwarding port 80?

What happens if you use you try to check your server using the internal IP address that is assigned by your router, for example mine would be:

[http://192.168.0.102:8080](http://192.168.0.102:8080)


Does the page come up then?

---

### Post by taemo on 2006-10-23
hey bud just wanted to say that it works fine now with port 8080
[http://mzracer360.game-host.org:8080](http://mzracer360.game-host.org:8080)
[http://24.255.223.134:8080/](http://24.255.223.134:8080/)

are working links for me now.

I'm having problems with mine too:
[http://taemo.serveftp.net](http://taemo.serveftp.net)
LAN can access it, but people outside cant.
I might have to change port to 8080 aswell, but its odd because I now some other people on Shaw Cable that setup their own webserver and told me port 80 works fine. 
Could it be because I have 2 routers on my network, even tough I both set them up to forward all incoming port80 to my server?
how my network is setup:
cable modem - Linksys BEFSR41 - server
[COLOR="White"]qqqqqqqqqqqqqqqqqqqqqqqqqqq[/COLOR]- D-Link 524 - wifi

---

### Post by hkgonra on 2006-10-23
> **taemo said:**
> hey bud just wanted to say that it works fine now with port 8080
[http://mzracer360.game-host.org:8080](http://mzracer360.game-host.org:8080)
[http://24.255.223.134:8080/](http://24.255.223.134:8080/)

are working links for me now.

I'm having problems with mine too:
[http://taemo.serveftp.net](http://taemo.serveftp.net)
LAN can access it, but people outside cant.
I might have to change port to 8080 aswell, but its odd because I now some other people on Shaw Cable that setup their own webserver and told me port 80 works fine. 
Could it be because I have 2 routers on my network, even tough I both set them up to forward all incoming port80 to my server?
how my network is setup:
cable modem - Linksys BEFSR41 - server
[COLOR="White"]qqqqqqqqqqqqqqqqqqqqqqqqqqq[/COLOR]- D-Link 524 - wifi


Why do you have two routers ? 
Why not just use the d-link by itself, or use the Linksys and turn off dhcp on the D-link ?

---

### Post by taemo on 2006-10-23
> **hkgonra said:**
> Why do you have two routers ? 
Why not just use the d-link by itself, or use the Linksys and turn off dhcp on the D-link ?

Dlink DHCP is off, so just acting as switch. I have it in the kitchen as access point. whereas the Linksys is the main router with DHCP on in the basement.

question...I can access the server via SSH on port 22 from school (where currently Im at) but I cant see the site on port80.
does this mean my ISP blocked port 80?

---

### Post by Ronbo on 2006-10-24
If one is only acting as a switch it shouldn't affect it, I am running a 4 port Buffalo router with an 8 port Linksys switch and my server behind the switch with no problem.  I do know with the D-Link DI-604 provided by My ISP Verizon somehow they blocked the DynDNS setup which I found with some Googling.  You can set it up but it doesn't work, so I purchased the Buffalo router and have no problems using DynDNS using port 8080.  I wouldn't be surprised, and it sounds like they are, blocking port 80, especially if you can get through using SSH. Just to check your setup try connecting the server directly to the Linksys if it is not currently running from that and then try listening on port 8080.

---

