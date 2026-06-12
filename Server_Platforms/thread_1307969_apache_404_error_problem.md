---
title: "apache 404 error problem"
date: 2009-10-31
forum: Server Platforms
---

### Post by zurek22 on 2009-10-31
Hello Everyone
 
Well im just going to cut to the point for some reason I cant view my website from the outside world, i just keep getting **Error 404 Not found - The requested URL / was not found on this server** and if i am on my home network i can get to it just fine i dont understand this at all, i set up my port forwarding correctly i checked it using an online port scaner it said 
[COLOR=red]192.***.*.*** is responding on port 8080 (webcache).[/COLOR]
[COLOR=red]192.***.*.*** is responding on port 80 (http).[/COLOR]
 
[[COLOR=blue]http://www.t1shopper.com/tools/port-scanner/[/COLOR]]("http://www.t1shopper.com/tools/port-scanner/")
 
I asked my friend to check it for me and he has the same error
 
im quite a noob at this who appache thing so can you explain things in an easy step by step thing, I only started using linux about a month ago
 
more info
- I installed lamp using the command 
**sudo tasksel install lamp**
**- **im using ubuntu 9.04 desktop
 
**note** I will add more information as it comes up thank you
 
 
Thanks for your time
zurek22

---

### Post by zemon_ on 2009-10-31
```
sudo tasksel install lamp-server 
```

Did you actually install lamp? if not try this

---

### Post by zurek22 on 2009-10-31
Yea it went to a blue screen and had me type in a password for mysql and it downloaded and installed 22 different things but I'll Reinstall ubuntu like i have been when Iess up and I'll try the code and see what happens

---

### Post by efflandt on 2009-11-01
192.x.x.x IP's are private (LAN) IP's.  So a public scanner cannot even route to "your" 192. IP.  What do you get when you when you publicly scan your public IP?  What, if anything, shows up in your apache logs when accessed from the internet by a web browser?

It helps to have a dial up (or mobile data) account so you can test it from the internet, from a PC not connected to your LAN.  Because you may not get accurate results testing it just from its LAN IP.  And many NAT routers do not do loopback [LAN2LAN via WAN (public) IP].

Note that behind NAT apache cannot really tell what (public) IP was used to access it and may try to redirect incomplete URL's (missing trailing slash if not an actual filename) to an inaccessible place, so you may need to set [URL="http://httpd.apache.org/docs/2.2/mod/core.html#usecanonicalname"]UseCanonicalName Off
[/URL]

---

### Post by Lars Noodén on 2009-11-02
As efflandt  points out, the problem is that your machine is on a LAN and the ip numbers used for that LAN (192.168.0.0/16) are not routed to the outside world.  

On your ADSL modem, you should have the option to set port forwarding of some kind.  WWW uses ports 80 and 443 for HTTP and HTTPS respectively.  Have the ADSL modem forward (aka NAT) these to your machine and they will be visible to the outside -- if that is really what you want to do.

As far as using a scanner from your friend's location, try zenmap if you want a gui.

---

### Post by zurek22 on 2009-11-02
[SIZE=3]Lars Noodén [/SIZE][SIZE=3]This is what my router is set at to allow ports I have a 2wire 1701hg router[/SIZE]

[IMG]http://i513.photobucket.com/albums/t331/zurek22/Screenshot-1.png[/IMG]

_[IMG]http://i513.photobucket.com/albums/t331/zurek22/Screenshot.png[/IMG]_

---

### Post by Lars Noodén on 2009-11-02
> **zurek22 said:**
> [SIZE=3]Lars Noodén [/SIZE][SIZE=3]This is what my router is set at to allow ports I have a 2wire 1701hg router[/SIZE]



Thanks.  The router model helps more than the picture.  

If (and only if) you want the outside to be able to access the web server, you need to follow the instructions for the 2wire 1701g:
[http://support.2wire.com/?page=view&article=21](http://support.2wire.com/?page=view&article=21)

TCP ports 80, 443 mapped to host port 80 and 443 are the ones you want, plus ICMP message type 0 and 8.

---

### Post by zurek22 on 2009-11-02
> **Lars Noodén said:**
> Thanks.  The router model helps more than the picture.  

If (and only if) you want the outside to be able to access the web server, you need to follow the instructions for the 2wire 1701g:
[http://support.2wire.com/?page=view&article=21](http://support.2wire.com/?page=view&article=21)

TCP ports 80, 443 mapped to host port 80 and 443 are the ones you want, plus ICMP message type 0 and 8.

ok let me just clear things up for me
the port range is 80-443
maped to port 80

looks like this

[IMG]http://i513.photobucket.com/albums/t331/zurek22/Screenshot-2.png[/IMG]

---

### Post by Lars Noodén on 2009-11-03
Yikes!

The comma means 'and' where as a dash means a range. 

80, 443 means port 80 and port 443 but no other ports.

80 - 443 means ports 80 through 443 inclusive.

So it looks like the modem will need two profiles.  One for port 80, the other for port 443:

TCP port 80 map to port 80
TCP port 443 map to port 443

---

### Post by zurek22 on 2009-11-03
Ok so the range would be 80-80 maped to port 80 correct and the other one would be port 443 - 443 maped to port 443 correct

---

