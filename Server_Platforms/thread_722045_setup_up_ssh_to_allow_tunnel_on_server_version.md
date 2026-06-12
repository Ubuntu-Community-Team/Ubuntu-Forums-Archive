---
title: "setup up ssh to allow tunnel on server version?"
date: 2008-03-12
forum: Server Platforms
---

### Post by android6011 on 2008-03-12
I did a fresh install of ubuntu server 7.10, and I can ssh into through putty on my windows machine. but, if i set up a tunnel through putty on say port 9999, and I set firefox to proxy 127.0.0.1 on port 9999 , all I get is a blank page? what do i need to do to be able to tunnel through my server machine? thanks

---

### Post by sachins on 2008-03-12
Hello,

I dont quite get what you are trying to do. You said your tunnel has a local port of 9999, are you connecting to the remote host on a port that accepts http connections? Like say port 80? Whatever port you choose you need a webserver running on the remote comp so that you can see something thru firefox.

Sachin.
[http://www.civil.iitb.ac.in/~d3sachin](http://www.civil.iitb.ac.in/~d3sachin)

---

### Post by Sef on 2008-03-12
Moved to Server Platforms.

---

### Post by android6011 on 2008-03-12
ok this is what I have:

ubuntu server with ssh server listening on port 22

pc computer: putty connecting with tunnel dynamic on source port 9999, and firefox proxy at 127.0.0.1 9999

I thought you get setup ssh to do tcp forwarding or something and thats all you would need

---

### Post by koenn on 2008-03-12
if you want to browse through a tunnel, you dont set a proxy; 
instead you browse (i.e. enter in firefox addressbar) : 
[http://localhost:9999](http://localhost:9999)
because you've forwarded local port 9999 to ubuntu_server port 80 (web browser), you"re browser will be talking to the web server there.

This is all assuming you have a web server on that ubuntuserver, and that it is listening on localhost, port80.

[IMG]http://users.telenet.be/mydotcom/howto/linux/graph/sshtunnel.png[/IMG]
from [http://users.telenet.be/mydotcom/howto/linux/tunnel.htm](http://users.telenet.be/mydotcom/howto/linux/tunnel.htm)

---

### Post by android6011 on 2008-03-12
im not looking to setup an http proxy though, i want a tunnel for all kinds of things, email, bitorrent, etc. so an http proxy isnt what i want to go through

---

### Post by koenn on 2008-03-12
> **android6011 said:**
> im not looking to setup an http proxy though, i want a tunnel for all kinds of things, email, bitorrent, etc. so an http proxy isnt what i want to go through

> **android6011 said:**
>  ... and** I set** firefox to **proxy** 127.0.0.1 on port 9999 , all I get is a blank page? 

That's what I said : don't set a poxy.

---

### Post by android6011 on 2008-03-12
ok, i found this a minute ago, this is what i have done 

[http://kakku.wordpress.com/2007/10/24/blocked-at-workplace-setting-up-a-home-proxy/](http://kakku.wordpress.com/2007/10/24/blocked-at-workplace-setting-up-a-home-proxy/)

Grab the putty client.

There are a million things that you can do with this tool. But more on Putty in another session.

Set the following parms:

.....

2. Source port = 12345(Any)
Destination = Empty
Choose &#8220;Dynamic&#8221; among, &#8220;Local&#8221;, &#8220;Remote&#8221; and &#8220;Dynamic&#8221;.

...
What ? You are done man! Open on Firefox, rush to Network settings and use
1. HTTP Proxy - > proxyhost = localhost, port = 12345. , If you used the first kind of tunnel, i.e. you set up a home proxy as well.

---

### Post by koenn on 2008-03-12
Oh, you want to tunnel to a **proxy,** not to a web server.
Trying to avoid content filtering, or punch holes in a school/corporate firewall, are we ? 

Assuming you have a working tunnel, do you actually have a web proxy running at the far end of the tunnel ?

---

### Post by android6011 on 2008-03-12
no i dont have a proxy setup, yes essentially i am trying to bypass school blocks on bittorrent, but I also want this for when i am on unsecure wireless networks. All i have is a fresh install of ubuntu server with LAMP and ssh access. I have not installed anything else, i have side projects planned for the LAMP part, but I just want to tunnel my traffic to my home server that has the fresh ubuntu install on it.

---

### Post by koenn on 2008-03-12
so, you want to tunnel to a proxy, but you don't have a proxy, and you wonder why nothing happens when you use that tunnel.


If that's already too much of a riddle to you, I don't think it's wise to teach you how to mess with security measures such as firewalls. 
Besides, there's recipes for this sort of thing all over the web.

---

### Post by android6011 on 2008-03-12
> **koenn said:**
> so, you want to tunnel to a proxy, but you don't have a proxy, and you wonder why nothing happens when you use that tunnel.


If that's already too much of a riddle to you, I don't think it's wise to teach you how to mess with security measures such as firewalls. 
Besides, there's recipes for this sort of thing all over the web.

so are you saying that

client pc -> ssh internet -> home server -> internet

is impossible without an http proxy?

---

### Post by robert_pectol on 2008-03-12
Look into OpenVPN: [http://openvpn.net/index.php](http://openvpn.net/index.php)

With my VPN setup, I can do everything as though I were on my home LAN, from anywhere in the world.  This includes accessing file shares, printing, etc. to other PCs on my internal LAN.  And, since my VPN server is also a NAT routing firewall box, it allows me to access the Internet through it, as though I were at home on my local LAN!  All this over one single TCP or UDP port (fully configurable).

It takes a little doing to get it configured and working the way you want, but once it's done, it's rock solid reliable and very secure.  All you need is remote access to the port that the server's OpenVPN daemon is listening to.

That being said, be careful not to break any policies that your school may have in place otherwise you might end up in some trouble as this effectively circumvents any and all content limitations they may be trying to enforce on the users of their network.  They have the right to limit however and whatever they see fit, on their networks and they may not be to happy to find out that you might be circumventing their policies.  Use with care!

---

### Post by koenn on 2008-03-12
> **android6011 said:**
> so are you saying that

client pc -> ssh internet -> home server -> internet

is impossible without an http proxy?

no.

---

### Post by KCPokes on 2008-03-12
You can do what you want with just SSH.  Add the following to /etc/ssh/sshd_config:

```

AllowTcpForwarding yes

```

Of course this is assuming you have your Putty session set up correctly, which it sounds like you do.  Also be sure that you remove localhost and 127.0.0.1 from addresses that bypass the proxy, in your browser configuration.

---

### Post by android6011 on 2008-03-12
ok, so what does everyone mean by when they ask if i have a "proxy" setup. is an ssh server not considered a proxy? or does the traffic to the ssh server have to go to a proxy?

---

### Post by android6011 on 2008-03-12
> **KCPokes said:**
> You can do what you want with just SSH.  Add the following to /etc/ssh/sshd_config:

```

AllowTcpForwarding yes

```

ive tried that and rebooting and i still get a blank page

---

### Post by KCPokes on 2008-03-12
Make sure you remove localhost and 127.0.0.1 from the addresses that bypass the proxy, otherwise you will get nothing.

---

### Post by android6011 on 2008-03-12
ya i do, in firefox it automtically adds 127.0.0.1 and localhost to addresses to not use the proxy. ive used ssh shell accounts before with putty and set it up this way, im just tired of all the running around and registering etc associated with said accounts and wanted to setup a server myself to use but i guess its not working out

---

### Post by android6011 on 2008-03-12
[pic of firefox configuration]("http://www.fileden.com/files/2007/3/11/876372/pic1.bmp")

[pic of putty configuration]("http://www.fileden.com/files/2007/3/11/876372/pic2.bmp")

is there anything besides AllowTcpForwarding yes supposed to be edited in sshd_config ? any permissions needed to be edited in ubuntu server?

---

### Post by KCPokes on 2008-03-12
> **android6011 said:**
> ya i do, in firefox it automtically adds 127.0.0.1 and localhost to addresses to not use the proxy. ive used ssh shell accounts before with putty and set it up this way, im just tired of all the running around and registering etc associated with said accounts and wanted to setup a server myself to use but i guess its not working out

The point is you have to REMOVE 127.0.0.1 and localhost from the "No Proxy for:" configuration (assuming you are using Firefox).  You proxy should be SOCKS Host: 127.0.0.1 with whatever port you set up in Putty for your tunnel (dynamic port not SSH port).  

If you do not remove 127.0.0.1 and localhost, you will get either an error or a blank page, as you are experiencing now, since you are bypassing your tunnel.  

If that still does not work, then post your Putty configuration again (or the steps you took to add the tunnel).

---

### Post by KCPokes on 2008-03-12
> **android6011 said:**
> [pic of firefox configuration]("http://www.fileden.com/files/2007/3/11/876372/pic1.bmp")

[pic of putty configuration]("http://www.fileden.com/files/2007/3/11/876372/pic2.bmp")

is there anything besides AllowTcpForwarding yes supposed to be edited in sshd_config ? any permissions needed to be edited in ubuntu server?

Your Firefox configuration is wrong.  Should be a SOCKS proxy and you have to remove everything from the "No Proxy for:" box.

---

### Post by android6011 on 2008-03-12
thanks i forgot i had 2 version of firefox i was using, one i was trying to use the proxy on and the other one i wasnt and i kept getting them mixed up in the settings. i really appreciate everyones help

---

