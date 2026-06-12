---
title: "server usage question."
date: 2007-11-09
forum: Server Platforms
---

### Post by Methodize on 2007-11-09
Perhaps I just need to know a little more about servers but here is my question:

I have a Dell 8300 running Ubuntu 7.10 at home and an internet connection. Is it possible for me to set up a server on Ubuntu to which I can host some type of web page that I could access from anywhere?

---

### Post by p_quarles on 2007-11-09
It's fairly easy to set up a basic web server. Detailed instructions are here:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

As for accessing it from anywhere, this can be a little more complicated, depending on your ISP. If you have a static public IP address, then it's easy. If -- like most home users -- you have a dynamic IP address, you'll have to use a service like DynDNS to keep track of the IP address. 

Other compllications are less frequent, but these are two that spring to mind: 1) Some ISPs block the default web port (80). You can work around this by having the web server "listen" on a different port. 2) A few ISPs (notably satellite providers) use a connection method that doesn't give you a unique public IP address. This is anywhere from very difficult to impossible to work around.

---

### Post by reddeth on 2007-11-12
I'm trying to accomplish the same thing myself, I'd like to setup a spare computer I have to act as a small webserver and email server, the setting up of Apache and its related processes is no problem, I've found a ton of guides to facilitate it. However, the  one thing that completely eludes me, is getting the thing visible to the rest of the world, my current networking setup is:

[IMG]http://i9.photobucket.com/albums/a70/reddeth/network.jpg[/IMG]

What I'd like to figure out is: How do I set the computer up so that I type in a domain name (say, reddeth.com) and it will go to the web files on that computer? Or is there a guide somewhere that details this part of the installation? Again, I have no problem getting the computer to act as a server, but making it visible to the world is what I cannot for the life of me figure out. Any help is greatly appreciated.

---

### Post by p_quarles on 2007-11-12
That's all pretty straightforward as well. Here's a quick step by step. 

1) Configure the server so that it has a static LAN IP address. 
2) Configure the router to forward requests on port 80 (or whatever port you want to use -- 80 is standard for http) that the server's IP address. 
3) Register a domain name. [reddeth.com]("http://www.reddeth.com/") appears to be taken (unless that's you and you got it working in the last 40 minutes)
4) Get a DNS server to point that domain name at your IP address.

Step four is the one that can be tricky. A lot of home internet services use dynamic IP addresses, which means that it will change on a regular basis. Fortunately, there's a service that will keep track of it for you, and provide you with DNS:
[http://www.dyndns.com/](http://www.dyndns.com/)

They also have a bunch of freely usable third-level domain names if you don't want to bother paying for one. 

If you're not sure how to do some of these things, ask away.

---

### Post by reddeth on 2007-11-12
That actually is my site (part of a class in high school I was taking), but its hosted on GoDaddy, I hate paying for it and like the idea of controlling it myself.

So, what you're saying is forward all requests on port 80 to the server1 computer, then just point the nameservers of the domain name to the IP address of the DSL router? After that, I just act as if Apache were accepting requests from a local IP right?

I'll work on that tonight, many thanks!

---

### Post by p_quarles on 2007-11-12
Exactly. If your ISP gives you a static address, that's all there is to it. 

One other thing you probably want to do is change Apache so that it's listening on the server's LAN IP address, rather than localhost.. In /etc/apache2/ports.conf you'll need to change whatever the default is (I forget) to something like this:
```
Listen 192.168.00.3:80
```
And, of course, always practice safe serving. Make sure the server is locked down with a good password, don't use telnet or ftp, and check your service logs regularly.

---

### Post by reddeth on 2007-11-12
Alright, that makes sense, I'll work on that before the end of the night. Then I just have to work out how to set up email and whatnot, but thats the next step. Thanks very much for the help!

---

