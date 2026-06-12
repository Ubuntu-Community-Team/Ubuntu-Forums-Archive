---
title: "How do I access server name from inside network"
date: 2009-05-18
forum: Server Platforms
---

### Post by Mtlca401 on 2009-05-18
I know many people have asked this question, but I am going crazy trying to get this to work.

I am trying to access my home server (ex: mysite.com) from within my network by using the name instead of the ip address.

I have added in the /etc/hosts:
192.168.0.100 mysite.com

I have also changed the /etc/network/interfaces to static

My server has a static ip, but I have a dynamic ip address from my isp. I don't know if that matters. I update it using ddclient and zoneedit.com

my router which is a netgear wpn824 has NAT on it. I know nothing about it.

I can ping my server name. I get 4 packets sent and 4 packets received. 

That's about all the information I can think of off the top of my head.

thanks

---

### Post by justatemptest on 2009-05-18
Perhaps it's your router that answers the ping and no your ubuntu machine.  What's the TTL shown there?
Where do you try to connect from? outside the network / inside the network?
Do you have iptables (or any other packet filtering) running?

---

### Post by Mtlca401 on 2009-05-18
> **justatemptest said:**
> Perhaps it's your router that answers the ping and no your ubuntu machine.  What's the TTL shown there?
Where do you try to connect from? outside the network / inside the network?
Do you have iptables (or any other packet filtering) running?

Perhaps, I did not think of that, but I don't know anything when it comes to networking.
The TTL number is 62. I am connecting from inside the network.
As far as the iptables or packet filtering, I have know idea how to check that.
I did notice however, when I type the address name from within the network it does not prompt me for my router login anymore. It just sits there trying to load.

---

### Post by Mtlca401 on 2009-05-18
Ok, now when I type in my website name it asks me to enter my router login. 

It's weird though, it asks me for my router login no matter if the server is turned on or not.

any ideas?

---

### Post by Iowan on 2009-05-18
> **Mtlca401 said:**
> I have added in the /etc/hosts:
192.168.0.100 mysite.comOn the server, or on the client?

---

### Post by Mtlca401 on 2009-05-18
> **Iowan said:**
> On the server, or on the client?


On the server.

---

### Post by MrWES on 2009-05-19
> **Mtlca401 said:**
> On the server.

I believe that should go in the client
/etc/hosts file.

~Bill

---

### Post by Mtlca401 on 2009-05-20
do you mean the server as in "the server I'm connecting to" and the client as in "the computer I am using to connect to the server"?

If so, the client is a vista machine which doesn't have a /etc/hosts file.

I'm confused.

---

### Post by Mtlca401 on 2009-05-20
Nevermind, vista does have this file. I added the line there and it works.

---

