---
title: "how to allow local computers to acess local web server."
date: 2012-06-19
forum: Server Platforms
---

### Post by Peter777 on 2012-06-19
I can view the web by localhost, by ip address and domain name from the server but cant access the same from other machines locally... or from infront of my router.  I have a domain name pointing to dyndns but my server config reveals my ignorance.  I need a puch in the right direction .  The server is an older compaq dual cpu p1 1ghz w/ 2 NIC cards.  Im almost there... i have their ddclient running but am missing something.
Please assist.
Regards,
P:popcorn:

---

### Post by darkod on 2012-06-19
1. Make sure there is no firewall on the server blocking incoming connections. Have you enabled/installed some firewall?

2. Go into the router config page and forward port 80 and 443 to the server private IP. That should allow to be accessed from the outside provided your dyndns works fine. But the clients on the LAN should be able to access using the server IP regardless of the settings on the router.

If the computers on the same LAN can't view the server by IP it would usually be a firewall issue.
If they can view it by IP but not by domain, you need a local DNS or to edit the hosts file on the local computers that would tell them where to look for that domain, on the local webserver.

---

### Post by rukiaEnix on 2012-06-19
First: Do  you have the http port open in the server?
Second: What IP are you using with dyndns?

---

### Post by Peter777 on 2012-06-19
ip from dyndns is 204.13.248.76 and suspect my ports are not set right in the server.  as newbie to ubuntu not sure what config files matter most. and how to modiy them for a basic web server setup.  just one domain for now.  I will however point 50 others to this one. That is my objective.

I do see the main dirs in play and config files but have my routing messed up i suspect my ports are not open

I found the netstat -lp button and also did this  $ netstat -lp | grep 80  i dont think anything is listening. Not sure how to resolve my port issue but it may have something to do with /etc/apache2/ports.conf or the etc/apache2/sites-enabled/config file but im not sure how to resolve.. Yes guy config needed. no fw on the server - all open.  if  knew what files pointed where in what order i could figure out my mess and where it falls apart.  can someone provide me a basic template...?

---

### Post by darkod on 2012-06-19
I haven't worked much with apache (webserver) but I believe by default it works on the standard port 80.

So I guess it should show your website right now as it is.

As already mentioned, the port forwarding on the router (the lack of it) might be stopping it from working from the outside.

But you should be able to open the website from any computer on the LAN by typing in the browser something like: [http://server_ip](http://server_ip)

By IP, it has to work, no questions asked or configuration needed. The only thing blocking this, that I can see, is a firewall on the server.

---

### Post by N0oki3 on 2012-06-19
have you edited http config ? allow all connection?

---

### Post by kennethconn on 2012-06-19
darkod has made some good points.
 
Get it working internally (LAN side) first, then work on external access (will require a port forward on your router device).
 
Are you sure your LAN is configured and cabled correctly?
I suspect the issue might have something to do with the 2 NICs you mentioned. 
 
Can you ping the server from your computer (by IP address)? That would be the first thing I would check once you have confirmed network config and cabling.

---

### Post by Peter777 on 2012-06-19
I can ping the ip address locally and ping the domain name locally.. but cant get the page to display.

---

### Post by kennethconn on 2012-06-19
That is unexpected. Seems to be pointing more towards a firewall or application issue so.
 
I think the ddclient can be installed on server and you should still be able to access locally by LAN IP (but I'm not certain of it), so I don't think that is an issue.
 
What is output of ```
sudo ufw status
```
 
> **darkod said:**
> But you should be able to open the website from any computer on the LAN by typing in the browser something like: [http://server_ip](http://server_ip)

 
What exactly is displayed here when you open a browser and type in the URL as suggested by darkod? You should be seeing the classic Apache It works! page if you made no changes.
 
Have you tried to telnet in to the webserver and see what GET / returns?

---

### Post by Peter777 on 2012-06-20
well good morning.  Turned on the boxes again this morn determined to  nail down the problem. sudo ufw status shows inactive.  When i punch in  the local address of the server into the browser it flashes quickly and  just stays completely blank like it didn't go anywhere. im doing this  from another pc on the lan.  from the server itself i did get it works,  so i proceeded to move on to adding a template web page on a designated  domain name.  from t he server itself (in the browser) i get the  template to come up from 127.0.0.1, 192.168.1.105 the ip and if i punch  in the domain name (without the www) all bring up the template index  file as i was hoping.  but from other pc's i get white browser flash and  nothing.  I can ping the ip address and domain name from the laptop but  cant see the index.html file in the browser, when i can in the server.  problem i have is im not sure if its the dyndns setup or my config or  both.   i know i changed the the original 000-default file saved it when  i shouldnt have (but i dont think that is the problem) .  i think my  ports arent opened.  config and operator error is at fault.  Any ideas  to help..?  im happy to resolve.  I never did do anything with the nic  cards..? or the network..? i think getting things going locally will  help.  but not sure how to resolve my web server dilema.  

my config is screwed somewhere. did i mention i was frustrated. i hope to break thru somewhere. oh yeah i did not try to telnet but may in 2 seconds

---

### Post by Peter777 on 2012-06-20
> **Peter777 said:**
> well good morning.  Turned on the boxes again this morn determined to  nail down the problem. sudo ufw status shows inactive.  When i punch in  the local address of the server into the browser it flashes quickly and  just stays completely blank like it didn't go anywhere. im doing this  from another pc on the lan.  from the server itself i did get it works,  so i proceeded to move on to adding a template web page on a designated  domain name.  from t he server itself (in the browser) i get the  template to come up from 127.0.0.1, 192.168.1.105 the ip and if i punch  in the domain name (without the www) all bring up the template index  file as i was hoping.  but from other pc's i get white browser flash and  nothing.  I can ping the ip address and domain name from the laptop but  cant see the index.html file in the browser, when i can in the server.  problem i have is im not sure if its the dyndns setup or my config or  both.   i know i changed the the original 000-default file saved it when  i shouldnt have (but i dont think that is the problem) .  i think my  ports arent opened.  config and operator error is at fault.  Any ideas  to help..?  im happy to resolve.  I never did do anything with the nic  cards..? or the network..? i think getting things going locally will  help.  but not sure how to resolve my web server dilema.  

my config is screwed somewhere. did i mention i was frustrated. i hope to break thru somewhere. oh yeah i did not try to telnet but may in 2 seconds

telnet localhost 80 gave me an unable to connect to remote host conection refused.

---

### Post by koenn on 2012-06-20
look in /var/log for apache access and error logs

compare  the successful attempts with the failed attempts; the difference will give you a clue about what is not working as expected

---

### Post by rukiaEnix on 2012-06-21
Please post your httpd config file.

And maybe this has already been asked but I got a little lost.

Can you access your own apache server where it is mounted using 127.0.0.1?

Can you access the apache server from other computer in the LAN using it's private IP address?

---

### Post by jsampaio57 on 2012-10-04
If you know the name of the machine in your network, say "TheServer", you can easily access the localhost of that machine from your browser typing the URL...

TheServer.local

If you want to run the web based application "theApplication" then you type...

TheServer.local/theApplication

Good Luck!... Jorge

---

