---
title: "Breezy LAMP server not visible to rest of network"
date: 2006-08-02
forum: Server Platforms
---

### Post by greymoose58 on 2006-08-02
Up until a few hours ago I had a perfectly good web server/proxy running at home on Breezy. It was running Apache2, MySQL, TinyProxy and Dan's Guardian. The only problem I had was that the users going through the proxy couldn't access their pop3 and SMTP mail services from our ISP. 

I tried setting up a mail server (I don't know if that was the best approach to solving the problem) and when it didn't work I turned off all of the extra services. Now I can ping the rest of the network from the Breezy box but not vice-versa. I have turned off Apache2, MySQL, TinyProxy and Dan's Guardian and still have the same problem.](*,) 

This being my first foray into server land I am at a loss as to where to look for a problem. Does anyone have any suggestions?

Thanks in advance.

---

### Post by apjone on 2006-08-02
is iptables  or ip6tables running?

---

### Post by heisters on 2006-08-02
> Now I can ping the rest of the network from the Breezy box but not vice-versa.

Sounds like your network configuration got borked. Without knowing more about your network, it's impossible to troubleshoot. How are IP addresses assigned on your LAN? Are you running DNS?

---

### Post by greymoose58 on 2006-08-02
> **apjone said:**
> is iptables  or ip6tables running?

Um,  dunno. What is the default for Breezy?

> **heisters said:**
> Sounds like your network configuration got borked. Without knowing more about your network, it's impossible to troubleshoot. How are IP addresses assigned on your LAN? Are you running DNS?

I'm using static IP adresses. DNS is running on my router but the addresses start above the ones I have allocated manually.

---

### Post by greymoose58 on 2006-08-03
Thanks for your input people. In the course of taking the server off the network I discovered that the e-mail problem was with the client so I didn't need to install a mail server after all. I decided to do a clean install of the whole server.

Cheers.

---

