---
title: "How to access pc's of a private network?"
date: 2006-04-03
forum: Server Platforms
---

### Post by Elijah on 2006-04-03
Our main server is the only one that was a public ip address, the rest are setup via dhcp & dns with local addresses. 

How can I be able to know or use or access a specific local pc from outside? let's say I connect to our main server then the main server would then forward the request to whoever I wanted to access? 

Example. I have a local website setup via localhost on pc1, I wanted to check the webpage with the w3c validator [www.validator.w3.org](www.validator.w3.org) , I only know the address of the main server and I could'nt just input [http://localhost/newsite](http://localhost/newsite) in there... what can I do?

---

### Post by colo on 2006-04-03
I take it the box with the public IP adress is a masquerading router?

You'll just need to set up port-forwarding for the locally available machines. A HowTo on iptables will tell you how to do that.

---

### Post by Elijah on 2006-04-18
[QUOTE=colo]I take it the box with the public IP adress is a masquerading router?

You'll just need to set up port-forwarding for the locally available machines. A HowTo on iptables will tell you how to do that.[/QUOTE]

hmmm... looks like a big learning thing for me to setup iptables, I never get around to implementing one successfully yet. But thanks for showing me the right direction :-)

---

### Post by fdoving on 2006-04-18
I would recommend a VPN connection from your home computer to the office server. That would give you a encrypted tunnel to the office network. You would get a office IP address and you can use the office network as if you where there.

Take a look at:
[http://www.debian-administration.org/articles/35](http://www.debian-administration.org/articles/35)

You can use most of the commands in this article.
I doubt you have to add the repositories though. Adding them will just mess things up. And I think you will find the packages in the universe repository. Though I am not certain.

Good luck :)

- Frode

---

### Post by jinacio on 2006-04-18
[QUOTE=colo]I take it the box with the public IP adress is a masquerading router?

You'll just need to set up port-forwarding for the locally available machines. A HowTo on iptables will tell you how to do that.[/QUOTE]

I use [shorewall](http://www.shorewall.net) for all my iptables needs. 
basicly, it let's you create rules for firewall/routing/NAT in a very easy way and has good documentation too.

---

