---
title: "broadcasting ip via email"
date: 2010-04-11
forum: Server Platforms
---

### Post by bbqau on 2010-04-11
Just wondering if there is a method of achieving the problem outlined below.

I am running a home server on my local network, everything is working fine and it serves well to backup information and work to. 

Now i am going away for a few days and want to be able to access my home network server. I am able to port forward and access from the web, all that is fine, the main problem i am having is the fact i have a dynamic IP and subsequently cannot determine the servers IP from a remote location once it has changed.

I was thinking that there might be a way to send an email hourly with the web ip ( not internal ip ) from my server to an email account of my choosing, this email would contain the relevant IP address of the server. How would i go about setting this sort of thing up.

If there is a simpler solution or tools already available please let me know.

**more**
I have setup my SSL and that is working fine, just wondering how to setup a password to access the server... eg [https://192.168.2.2](https://192.168.2.2) is my lan ip and i can easily browse my gitweb repositories that i work to, also i use Samba and also use FTP and also use webadmin which runs on port 10000 and phpMyAdmin so is there a way to protect my home server from some random who might stumble apon it for all these web services available ?

---

### Post by fang0654 on 2010-04-11
What type of router do you have?  

A lot of decent routers support DynDNS.  You register a free domain name like myserver.dyndns.com, and whenever your external ip changes your router updates DynDNS.

As far as security, either put a username/password in .htaccess, or set up a VPN.  If you have a router that supports DD-WRT, you can easily set up an OpenVPN to connect into your network from anywhere without opening it up to the outside.

---

### Post by KB1JWQ on 2010-04-12
+1 to the dyndns suggestion.

---

### Post by bbqau on 2010-04-12
Thanks for the information, i registered a DnyDNS account and got the server running, my router is crap tbh and i had a look through all the settings but cannot seem to find anything you mentioned. The model is

Belkin Wireless G
Model :: F5D7230-4

[http://www.belkin.com/support/product/?lid=en&pid=F5D7230-4&scid=221](http://www.belkin.com/support/product/?lid=en&pid=F5D7230-4&scid=221)

So my guess is that it does not support DnyDNS, so i might have to write a program to do the mail thing i mentioned and simply rely on that :/

Thanks for the help, if you have anymore suggestions i am open ears :)

---

### Post by lisati on 2010-04-12
[NOIP]("http://noip.com") has a program you can download and set up to automatically update the relevant DNS records. If memory serves correctly, DynDNS has a similar facility.

---

### Post by Ryan Dwyer on 2010-04-12
sudo apt-get install ddclient

Then edit /etc/ddclient.conf

---

### Post by bbqau on 2010-05-01
Thanks for the information, got it all working now :)

---

