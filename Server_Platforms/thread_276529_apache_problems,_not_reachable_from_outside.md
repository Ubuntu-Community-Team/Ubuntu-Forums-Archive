---
title: "apache problems, not reachable from outside"
date: 2006-10-13
forum: Server Platforms
---

### Post by jamesabruce on 2006-10-13
hi. ive installed a basic LAMP setup from the ubuntu 6.06 server cd and added wedmin to control everything. 

i set it up to listen on port 78, incase my provider disallowed 80. when i type the internal ip address and port 78 into the address bar from any machine on my network, it works fine, displays the default page. 

i set up my router to forward tcp port 78 from the outisde to the ip address of the server. i did it in exactly the same way i set up a port forward for my bittorrent client on antoher machine.

however, when i get my external ip address from a site like "whatsmyipaddress.com", type that in along with the port, it fails...though it says the computer is there it cant make a connection, not just a not found error...

pls help, as im not sure what ive done wrong. im damn sure the port forwarding is setup correctly, the ip addresses are right... is apache installed by default to only work internally for security purposes or something?


[http://124.98.56.39:78/](http://124.98.56.39:78/) - 
Failed to Connect


The connection was refused when attempting to contact 124.98.56.39:78.


Though the site seems valid, the browser was unable to establish a connection.


btw, im running off a 100mb fibre optic line in japan. the router is in japanese, but its fairly simple. the inbuilt firewall is turned off, and only two port forward are setup, one to the server on 78 for web, one to windows on 56666 for torrent stuff. 

any ideas? would a clean install without webmin help me out?

---

### Post by jamesabruce on 2006-10-13
btw,  when i restart apache server it says i dont have a fully qualified domain name, and it reverts to 127.0.0.1

is this ok? i thought you didnt need a domain name just to run a server. eventually i can set up a subdomain from my paid webhost to redirect to the servers ip address cant i?

---

### Post by Parama on 2006-10-13
It's okay - and you are right - you don't need a domain name to run a server.
In your .conf file just put in **ServerName 192.168.9.9**.I prefer this pretty much in the beginning of the .conf because I keep namebased virtual hosts in the bottom.

---

### Post by jamesabruce on 2006-10-13
um, which conf file? i tried writing:

aniki-server 192.168.24.1

at the start of apache2.conf and it said invalid. also, would this stop it being reachable from teh outside world?

---

### Post by tartetatin on 2006-10-13
> aniki-server 192.168.24.1

For this line, when he says "ServerName 192.168.9.9", ServerName, is a keyword, it shouldn't be replaced by your server name.

And for the port redirection, do you redirect 78 on your router to 78 on your server, or to 80 on your server ?
In the first case you should also tell apache to listen to 78 and not 80, and in the second case it is ok.

And to finish, I am not sure, but I am wondering if you can use the port 78 for this, I thought we could only use ports in the range 1024-65535 for this, the lower ports being reserved...

---

### Post by MJN on 2006-10-13
[http://124.98.56.39:78/](http://124.98.56.39:78/) works fine from here...
 
So, unless you've changed something since posting and fixed it then the problem is likely that your router does not allow internal (LAN-based) clients to access other internal clients (server in this case) using the external (WAN) address. Many are like this and they are a pain for exactly the reasons you have suffered.
 
Mathew

---

### Post by jamesabruce on 2006-10-13
woah... its working?? Thats absolutely the first time ive ever heard that of routers, but fair enough. wow. how on earth am i supposed to go about testing? get ANOTHER internet connection or keep phoning a friend?! 

thank you everyone, you have been extremely helpful. now i know what makes ubuntu so great - the user community behind it!

thank you!

:-D

---

### Post by MJN on 2006-10-13
Just test it with either your internal LAN (or loopback for the server) address or, if you'll be wanting to utilise a domain name with it, put a local entry in your /etc/hosts file (e.g. **127.0.0.1 [www.whateveryoursiteiscalled.com]("http://www.whateveryoursiteiscalled.com")**). Of course, if you've got other local clients that you'll be testing from (I'm not sure if I picked that up from your original post) then they too will need a similar entries in their hosts files (e.g. **192.168.0.2 [www..]("http://www..")..**).
 
Mathew

---

### Post by Sievo on 2006-10-13
I'm having the same problem, apache (installed on my desktop ubuntu install) is accessible from within my home lan, but times out from outside. I've got a dynamic DNS set up at [http://sievo.kicks-***.net/](http://sievo.kicks-***.net/) (those *** are another word for "butt")

I've tried adding "ServerName localhost" to my apache2.conf file, as per the instructions on [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) (under Installing apache | Troubleshooting)

Any ideas?
P.S.  I should add that I'm also running an svn server which is working fine outside the network at that url...

---

### Post by pppetter on 2006-10-14
@Sievo --> If I were you I would actually set ServerName to sievo.kicks-***.net
And restart apache.

Maybe it will help. But I don't really know :p

---

### Post by MJN on 2006-10-14
Sievo - Be careful jumping to the conclusion that you've got the same problem as it doesn't sound to me like you have. James' issue is that he **can** access his server from outside but not from the inside using his outside address (as it were). However, you can't (nor I) access it from outside at all hence I think you're looking at something different.
 
Presumably you have your ports forwarded in your router?
 
EDIT: I've just connected to your IP and whilst there's something listening (and responding) on port 80 it's not delivering any content. Does your route have a built-in web server? If so, is that disabled (or moved off port 80)? Do your Apache logs show anything when you try to connect from the outside?
 
Mathew

---

### Post by Sievo on 2006-10-14
I do have the ports forwarded, but my router does have a built in webserver (for admin access).  So I changed apache to listen on 8080 (if someone could try it that would be great).

The apache logs only show connections from localhost

---

### Post by MJN on 2006-10-14
Yep - on port 8080 it works fine...

---

### Post by Sievo on 2006-10-14
awesome!  thanks peeps

---

