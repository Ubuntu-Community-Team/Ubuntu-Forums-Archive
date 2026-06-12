---
title: "GUFW firewall front-end"
date: 2009-12-10
forum: Security
---

### Post by tnvkrishna on 2009-12-10
hi all,
I have installed this GUFW.
I have kept it in the mode "deny by default".
and I have made a rule(the only rule infact) to allow tcp traffic
on port 2000(both inward and outward).

Now my doubt is since I am only allowing those ports to make
connections .. and it is in "deny by default" ..
how come I browse the internet?
does my browser know that it should open that port no. 2000?..

please enlighten me.

---

### Post by cariboo on 2009-12-10
Iptables, the firewall, doesn't block outgoing ports, so you should still be able to connect to the internet.

---

### Post by tnvkrishna on 2009-12-10
hmm..
how about simultaneous http connections to different servers? 
or let us take ftp connections which
need atleast 2 ports to listen to..
one for data connection and one for control connection..

and one more ..
if I make a rule to listen on port 2000
it does not mean that a foreign host can initiate connection
on that port right?

---

### Post by lovinglinux on 2009-12-10
> **cariboo907 said:**
> Iptables, the firewall, doesn't block outgoing ports, so you should still be able to connect to the internet.

Just to clarify for the OP, in fact is UFW/GUFW that doesn't have rules to block outgoing connections. If you know iptables commands you can block outgoing, without using UFW/GUFW.

> **tnvkrishna said:**
> hmm..
how about simultaneous http connections to different servers? 
or let us take ftp connections which
need atleast 2 ports to listen to..
one for data connection and one for control connection..

Outgoing connections will choose random ports for leaving your system and since outgoing is not blocked, it isn't an issue. 

> **tnvkrishna said:**
> and one more ..
if I make a rule to listen on port 2000
it does not mean that a foreign host can initiate connection
on that port right?

Only if you have server listening to that port, otherwise it will be rejected. Ports opened in the firewall and the router that does not have a listening server are in fact closed. That's why a firewall is usually unnecessary. Ubuntu does not come with any server listening to any ports by default. So unless you install and start a server (like ssh, apache or even a torrent client),  your ports will all be closed and all unrequested connections will be rejected.

---

### Post by bodhi.zazen on 2009-12-10
> **cariboo907 said:**
> Iptables, the firewall, doesn't block outgoing ports, so you should still be able to connect to the internet.

> **lovinglinux said:**
> Just to clarify for the OP, in fact is UFW/GUFW that doesn't have rules to block outgoing connections. If you know iptables commands you can block outgoing, without using UFW/GUFW.

This is not true, ufw will block outgoing traffic.

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

> Outgoing connections will choose random ports for leaving your system and since outgoing is not blocked, it isn't an issue. 

Only if you have server listening to that port, otherwise it will be rejected. Ports opened in the firewall and the router that does not have a listening server are in fact closed. That's why a firewall is usually unnecessary. Ubuntu does not come with any server listening to any ports by default. So unless you install and start a server (like ssh, apache or even a torrent client),  your ports will all be closed and all unrequested connections will be rejected.@tnvkrishna :

You misunderstand how clients connect to servers and therefore how to configure your firewall.

Servers listen on dedicated ports, each service has a default. http is port 80, ssh is 22, https is 443, etc.

Ports below 1024 are "privilaged" meaning you need to have root or admin access to start a server listening on them.

Clients, such as firefox, gftp, etc use pseudorandom ports to connect.

So say you start firefox to connect to the ubuntu fourms, you, as a client, use a random port, say 2000, to connect to port 80 on the ubuntuforums server.

If you understand that, then you can configure your firewall.

If you need assistance, see :

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

---

### Post by tnvkrishna on 2009-12-10
hi ,
I was asking about the "incoming" connections in case
of ftp (from a client point of view). If the incoming connection is not to port 2000
(as i only made a rule to allow port 2000 incoming connections)
they should be rejected..(by the way i understand it)
but it not infact the case .. could you reason it?

---

### Post by lovinglinux on 2009-12-10
> **bodhi.zazen said:**
> This is not true, ufw will block outgoing traffic.

This is a new feature, isn't it? As far as I knew, you had to edit some configuration files manually to block outgoing connections on early versions of UFW.

---

### Post by bodhi.zazen on 2009-12-10
> **lovinglinux said:**
> This is a new feature, isn't it? As far as I knew, you had to edit some configuration files manually to block outgoing connections on early versions of UFW.

Yes, shiny new with 9.10, but I thought you would be interested in the info nonetheless ;)

---

### Post by bodhi.zazen on 2009-12-10
> **tnvkrishna said:**
> hi ,
I was asking about the "incoming" connections in case
of ftp (from a client point of view). If the incoming connection is not to port 2000
(as i only made a rule to allow port 2000 incoming connections)
they should be rejected..(by the way i understand it)
but it not infact the case .. could you reason it?

Because ufw / gufw is blocking only **NEW** incoming connections, not established connections or outgoing traffic.

If you initiate contact to a web server, and the web serer replies, it is not a new connection, and is allowed through your firewall.

You are not understanding how it works =)

[http://en.wikipedia.org/wiki/Transmission_Control_Protocol](http://en.wikipedia.org/wiki/Transmission_Control_Protocol)

[http://www.inetdaemon.com/tutorials/internet/tcp/3-way_handshake.shtml](http://www.inetdaemon.com/tutorials/internet/tcp/3-way_handshake.shtml)

Again, ufw blocks new tcp packets, not ack or established.

---

### Post by lovinglinux on 2009-12-10
> **bodhi.zazen said:**
> Yes, shiny new with 9.10, but I thought you would be interested in the info nonetheless ;)

Oh yes, that's really good news. Thanks. Lots of newcomers complained about the lack of this feature in the past. Do you know if you can set it up through gufw? I don't want to install it just to check it out.

---

### Post by bodhi.zazen on 2009-12-10
> **lovinglinux said:**
> Oh yes, that's really good news. Thanks. Lots of newcomers complained about the lack of this feature in the past. Do you know if you can set it up through gufw? I don't want to install it just to check it out.

Not gufw yet, gui always lag behind command line tools and as you know outgoing traffic is not considered as critical to limit.

---

### Post by tnvkrishna on 2009-12-11
> **bodhi.zazen said:**
> Because ufw / gufw is blocking only **NEW** incoming connections, not established connections or outgoing traffic.

So it blocks the incoming packets on NEW connections.
I was under the impression that ,if no rule were made ,the
incoming tcp packet would be blocked ,whether it is on new 
connection or previously existing one.

thanks for the clarification.

looks like linuxdc++ asks a remote computer to initiate a connection to my computer to a specific port .. as i need to
put a port number in linuxdc++ preferences
and i need to allow that same port in gufw.

---

