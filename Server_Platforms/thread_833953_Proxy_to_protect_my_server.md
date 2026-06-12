---
title: "Proxy to protect my server?"
date: 2008-06-19
forum: Server Platforms
---

### Post by gamerzedge on 2008-06-19
I don't want to rely on just my router and server settings to secure my server from threats. I want to know if there is a way to take out my servers presence from the outside using a proxy server to filter the requests made by the clients.

If there is, does anyone have an info link for setting up a proxy server in that manner?

Well I hope that makes sense to you guys because I am tired and must sleep!

---

### Post by gtdaqua on 2008-06-19
Why don't you use NAT (or PAT)? They do quite the same thing as proxy. See if your router supports Network Address Translation - most do. Even SOHO models do. If they can, then jolly good; you can also protect your entire network of hosts under NAT without having to use a proxy server.

---

### Post by tcpip4lyfe on 2008-06-19
It kind of depends on what server you want to out behind a proxy.  If it's a LAMP server you could just serve the web off one server and have it make the Mysql connections to a different server off the DMZ.  If it's just a web server,  you'd still be making connections to the proxy so that would effectively become a new web server, kind defeating the purpose. If it's a mail server, put your mail server behind a ClamAV/SpamAssassin server and just use that as a relay.  That would be the most common application.  It really depends on what router you have though.  If it's a dlink or linksys, dump it and go [www.ipcop.org](www.ipcop.org) and make a nice little router out of an old computer.  If you have a real router like a Cisco ASA or a Sonicwall, just make sure your servers are in the DMZ and only open the port you need and you really don't need a proxy.

---

### Post by gamerzedge on 2008-06-20
Thank you guys for your replies.

I was hoping a proxy would be an answer to what I was looking for. I am starting a web sever, but will be offering some services in which there will be transactions going through and I want to make sure I am providing the best security I can for that reason.

How do most people secure their servers when they start a sever like this?

Isn't putting your server on a DMZ in the router make it vulnerable to the outside world? I thought DMZ essentially opened all the ports up to that IP?

---

### Post by Kolipoki on 2008-06-20
> **gamerzedge said:**
> Thank you guys for your replies.

I was hoping a proxy would be an answer to what I was looking for. I am starting a web sever, but will be offering some services in which there will be transactions going through and I want to make sure I am providing the best security I can for that reason.

How do most people secure their servers when they start a sever like this?

Isn't putting your server on a DMZ in the router make it vulnerable to the outside world? I thought DMZ essentially opened all the ports up to that IP?

I'm also interested in knowing the answers and/or suggestions for this scenario. I got more or less the same situation. I need to publish from a server that belongs to a private network. I was actually already researching around on the DMZ possibility, but still with the same concerns that Gamerzedge expressed.

Been playing around last week with the Server Edition (first time ever) in an old Dell server (no GUI, except for Webmin, which I still haven't used). But yesterday arrived 2 brand new servers that I'll need to build in the next couple of weeks. And we will be using Ubuntu for the first time in our institution. So, I'm very excited about it.

Will greatly appreciate the community for their outputs on this. I am pretty sure this option will be used (and asked for) much more as time goes by.  :)

---

### Post by koenn on 2008-06-20
> **gamerzedge said:**
> I am starting a web sever, but will be offering some services in which there will be transactions going through and I want to make sure I am providing the best security I can for that reason.

How do most people secure their servers when they start a sever like this?


They hire  a professional to set it up for them, or they outsource the entire thing to a web hosting company that provides secure transaction services.

---

### Post by gtdaqua on 2008-06-20
> **Kolipoki said:**
> I'm also interested in knowing the answers and/or suggestions for this scenario. I got more or less the same situation. I need to publish from a server that belongs to a private network. I was actually already researching around on the DMZ possibility, but still with the same concerns that Gamerzedge expressed.

Been playing around last week with the Server Edition (first time ever) in an old Dell server (no GUI, except for Webmin, which I still haven't used). But yesterday arrived 2 brand new servers that I'll need to build in the next couple of weeks. And we will be using Ubuntu for the first time in our institution. So, I'm very excited about it.

Will greatly appreciate the community for their outputs on this. I am pretty sure this option will be used (and asked for) much more as time goes by.  :)

Welcome to the party! DMZ is demilitarized zone - so you wont put any privately accessed data there. Its a pool of resources meant to be accessed by the public or designated outsiders. 

In your case, a simple one-to-one NAT-ing would be ok to expose only HTTP services to outside clients.

---

### Post by gamerzedge on 2008-06-21
> **koenn said:**
> They hire  a professional to set it up for them, or they outsource the entire thing to a web hosting company that provides secure transaction services.

I will be using a gateway and processing service for the transactions, but wanted to save some money on hosting my own server for the actual website. That way I can customize and edit everything locally. Not to mention, it is funner learning new skills and doing it yourself, but if the risk was really that much higher by hosting it locally then it would make sense to have a company host it for me but I don't see any reason why I shouldn't be able to do it.

It seems that purchasing a new router and using the NAT built in is what I will be looking into then.

Can I ask then, if a proxy is not used to hide other machines in the network and act as the doorman then what do people generally want to use a proxy server for?

---

### Post by gtdaqua on 2008-06-21
They dont use proxy normally these days. But proxy is something that you can use on top of a NAT-ed environment. Say you have a public IP and still want to browse through some other proxy server on the internet. You could do this simply without having to configure the remote proxy server. But for NAT, the NAT-ing device (route) should know the internal and external networks specifically. 

Also, proxy is application specific and NAT is network specific. Meaning, you can choose to use proxy under IE but not under Firefox on the same machine. But NAT works at the network level and your gateway will do the NAT-ing irresepect of browser or service you use.

---

### Post by koenn on 2008-06-21
> **gamerzedge said:**
> I will be using a gateway and processing service for the transactions, but wanted to save some money on hosting my own server for the actual website. That way I can customize and edit everything locally. Not to mention, it is funner learning new skills and doing it yourself, but if the risk was really that much higher by hosting it locally then it would make sense to have a company host it for me but I don't see any reason why I shouldn't be able to do it.

There's a lot of assumption in this, but : You sound as if you're quite new to web servers, security, and networks in general. You'll focus on getting things working. Getting things working and having things set up securely are not the same thing. Chances are you'll leave some loopholes or make a silly mistake that leads to a possible compromise of your server. Depending on how your network is laid out, a compromised web server my give access to your LAN hosts and the data they contain, or leave your transaction  mechanism exploitable. 

Learning new skills and figuring things out hands-on is great, but it's not something you should be doing in a production environment, i.e in a real life environment with real people's data at stake. 
I don't know how serious your project is or what sort of transactions you have in mind. Trial and error might be acceptable if its just fun and games for friends and relatives. If it's real business with real money, real privacy issues, confidential data, ... , I'd think twice about DYI and learn as you go. 

> **gamerzedge said:**
> 
It seems that purchasing a new router and using the NAT built in is what I will be looking into then.

Can I ask then, if a proxy is not used to hide other machines in the network and act as the doorman then what do people generally want to use a proxy server for?
I suppose you're talking about a 'reverse proxy' that sits in front of one or more web servers. It can be used for load balancing, caching, some forms of access control, to hide the network behind it, as a gateway to provide access to servers on a secure network, etc. It all depends on your problem, and the solution you designed. 
That's actually the point I'm trying to make : it's not so much about putting some appliances (a NAT router, a proxy server, ...) in place, it's about designing a a solution, and implementing it correctly.  

An example : you can hide everything behind a NAT router. Easy to setup,  and secure as long as you only connect from inside out. But you need to allow incoming connections to your web server. So you export ("forward" ) port 80. Easy. However, as your web server is on your secure LAN, this means the LAN is accessible (from the web server) as soon as the web server is compromised : a bug in the web server software, a mistake in its configuration, or a small oversight in the scripts it runs may be enough, and all your security goes down the drain. 


The right way to approach this is to think about the functionality you want to provide (web access to an application, using data managed by a database system, ...), figure out how to secure this (who needs access to what, and from which computer ? if one host gets compromised, how do I contain it, what's my next line of defense, ...) and then design  a network layout that supports this. This may or may not involve NAT routers or routers with Access Control Lists, a DMZ, one or more web servers, firewalls between different parts of your network, port forwarding,  web proxies, user authentication  ... but those are just building blocks. You still have to know what to build before you can put them to good use.

---

### Post by windependence on 2008-06-21
> **gamerzedge said:**
> Thank you guys for your replies.

I was hoping a proxy would be an answer to what I was looking for. I am starting a web sever, but will be offering some services in which there will be transactions going through and I want to make sure I am providing the best security I can for that reason.

How do most people secure their servers when they start a sever like this?

Isn't putting your server on a DMZ in the router make it vulnerable to the outside world? I thought DMZ essentially opened all the ports up to that IP?

The way this is normally set up is:

LAN==>FIREWALL==>DMZ==>FIREWALL==>ROUTER==>OUTSIDE INTERNET

The DMZ is usually set up on a different VLAN so that if it is compromized, they will still have trouble getting to you private network. For the home user, this is a bit much, but this is how the pros do it.

-Tim

---

### Post by koenn on 2008-06-21
> **windependence said:**
> The way this is normally set up is:

LAN==>FIREWALL==>DMZ==>FIREWALL==>ROUTER==>OUTSIDE INTERNET

The DMZ is usually set up on a different VLAN so that if it is compromized, they will still have trouble getting to you private network. For the home user, this is a bit much, but this is how the pros do it.

-Tim

OK, so if I have  just a simple web server, it would go in DMZ so I can allow incoming connections to it while the LAN remains inaccessible.

Now, what if that web server needs access to something secure, eg a database or some data-processing middleware. These should be secure so they'd preferably be on the LAN, not in DMZ. Yet the web server in DMZ needs access to them (to retreive data, or to trigger a process) so you need to allow connections from the webserver into the LAN. If the webserver is compromized, the intruder might gain access to the secure servers, which we dont want. But putting all your data in DMZ sounds just as bad. How do you deal with something like that ?  
I never figured out exactly how that is done

---

### Post by windependence on 2008-06-21
Well at the end of the day, the only true secure machine is one with the power turned off. :)

That being said, in a large data center there would be maybe even yet another layer of hardware protection but in this case, you only allow the webserver to access the backend databases just like you said. If you really want to get fanatical about it then you would put your dtatbase servers on yet another VLAN, that doesn't have access to the private LAN. You can never get 100%, but you sure can make it hard for them. Usually, they will go after an easier target once they see what you have done, unless you are a CC company or something that has very valuable data on it.

-Tim

---

