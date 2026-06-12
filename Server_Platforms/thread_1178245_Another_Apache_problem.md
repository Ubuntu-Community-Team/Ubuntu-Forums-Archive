---
title: "Another Apache problem"
date: 2009-06-04
forum: Server Platforms
---

### Post by penguin-of-doom on 2009-06-04
Hi,
I have another apache problem. I want to open port 80, so that everybody can go onto my homepage. I will make my own webspace for me. How do I open the port 80? And is it save when I open this port? When they get onto my pc, I don't matter, but when they can get into the network, it's not so good any more. So how can I make with my PC my own webspace and that nobody can hack my computer/network. I are looking forward to your answers.

regards,
penguin-of-doom

---

### Post by jonabyte on 2009-06-04
Port 80 can be forwarded from your router/firewall.

You may need to check your firewall settings on your apache baox as well.

---

### Post by penguin-of-doom on 2009-06-04
thx for your answer.
How can I look after my firewall-settings? Sorry, but that is my first run with apache ^^

mfg

---

### Post by kellemes on 2009-06-04
> **penguin-of-doom said:**
> thx for your answer.
How can I look after my firewall-settings? Sorry, but that is my first run with apache ^^

mfg

You use a modem/router?
Can you access the router's webinterface?

---

### Post by penguin-of-doom on 2009-06-04
>  Can you access the router's webinterface?
what do you mean with this? I do not understand, sorry...
I am using a router... 

thx for your answer!

---

### Post by Celauran on 2009-06-04
> **penguin-of-doom said:**
> what do you mean with this? I do not understand, sorry...
I am using a router... 
Your router has a web-based interface; you point your browser to 192.168.0.1 or some similar address to alter the router's settings. It is in this interface that you can set port forwarding.

---

### Post by mcduck on 2009-06-04
> **penguin-of-doom said:**
> Hi,
I have another apache problem. I want to open port 80, so that everybody can go onto my homepage. I will make my own webspace for me. How do I open the port 80? And is it save when I open this port? When they get onto my pc, I don't matter, but when they can get into the network, it's not so good any more. So how can I make with my PC my own webspace and that nobody can hack my computer/network. I are looking forward to your answers.

regards,
penguin-of-doom

Unless you have installed a firewall, there's nothing in Ubuntu restricting access to this port.

If you use a router, you need to forward the port on the router's configuration, just like others have already mentioned on this thread. How that's done depends on your router model, not the operating system you are using, so you really have to check your router's manual for instructions.

---

