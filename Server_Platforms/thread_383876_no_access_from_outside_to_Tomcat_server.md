---
title: "no access from outside to Tomcat server"
date: 2007-03-13
forum: Server Platforms
---

### Post by kemalcakmak on 2007-03-13
I installed **tomcat server** (5.5.23) on my ubuntu (6.10) manually.

After start there is the welcome page. so the server is running.

My **problem** is, even the router port **8080** is open. there is no way to reach the index from outside my local network!? 


I tried following (dont know if there was a need?)  

[LIST]
[*]tried to open port by "sudo iptables -A OUTPUT -p tcp --dport 8080 -j ACCEPT"
[*]install the tomcat via synaptic, started as root
[*]install the tomcat manually, started as not root
[/LIST]

without success....
:confused: 
Any hint?

---

### Post by Mr. C. on 2007-03-14
Are your router and your IP tables separate, or are they one and the same?

Your "A OUTPUT -p tcp --dport 8080 -j ACCEPT" allows packets to flow OUT of the system.  What rule allows the packet IN to your port 8080 ?  Users's connect via INBOUND connections to 8080, right ?

MrC

---

### Post by kemalcakmak on 2007-03-14
I opened the router port 8080 and it forwards the requests to my web server in the LAN (192.168.2.2). 

A dyndns repeater on my server provides an easy access to my server. Ping works. 

Both of  
[LIST]
[*]sudo iptables -A OUTPUT -p tcp --dport 8080 -j ACCEPT 
[*]sudo iptables -A INPUT -p tcp --dport 8080 -j ACCEPT
[/LIST] 

commands are executed. 

But what can 'block' the transfer? No firewall is active, execution over the port 1024 is allowed also for 'not root' users... hmm...

---

### Post by Mr. C. on 2007-03-14
The packets going OUT of your network will not have destination port of 8080.  The port will be a randomly chosen (high) port, created by the client when it established its connection.

The server will not tie up port 8080, as other's could not then access it.  It will select a new port in which to establish the return path.

Client:34500 -> Server:8080
...
Server:2039 -> Client:34500

You need to check for state ESTABLISHED if you are blocking OUTBOUND traffic.

I would suggest disabling your iptables while you are trying to get your remote connection working, and then configure iptables.

MrC

---

### Post by kemalcakmak on 2007-03-14
why nobody mention about the ip tables and ports on the tomcat installation?

what would you suggesst to open/close ports (disable iptables).

---

### Post by Mr. C. on 2007-03-14
Show me where on the Tomcat site they *did* mention to install and configure a firewall ?  That was your own undertaking.

There are lots of mentions of firewall issues regarding Tomcat:

[http://tinyurl.com/2bosym](http://tinyurl.com/2bosym)

If you are going to use iptables, you have to learn about the connections that your services require to run properly.  Start with iptables disabled on your system, and watch the network connections made via netstat or tcpdump.  You have to know and understand the basics of incoming, outgoing, and established connections to properly configure iptables for your services.

MrC

---

### Post by kemalcakmak on 2007-03-15
thx.

I started the Thread after a long while struggle with ports and tomcat. I know how to search in Google about ports and tomcat. Unfortunately I don't share your thoughts about a knowledge about ports, incomming,outcomming etc. These are working principals of a product. I only want to use this product to do something with it.

---

