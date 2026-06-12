---
title: "Lexmark Printer and UFW"
date: 2011-09-27
forum: Security
---

### Post by jamieofm on 2011-09-27
Hi, 

I recently installed Unbuntu 11.04. No problem. 

I then got the drivers for my all in one S405 lexmark printer from the lexmark website and installed them. Printer works fine. No problem. 

I am new to Unbuntu so decided to fool around with UFW a bit. set it up to default deny all connections and the started it. However on doing a 'status' the system told me that port 5353 was open. A bit of research and i found this is required by the printer for communications etc (from lexmark). 

My question is : Is this a security risk or a problem ? 

Here is my setup of UFW

*@#:~$ sudo ufw default deny
[sudo] password for jamie: 
Default incoming policy changed to 'deny'
(be sure to update your rules accordingly)
*@#:~$ sudo ufw enable
Firewall is active and enabled on system startup
*@#:~$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
5353                       ALLOW       Anywhere


Now here is a link to the lexmark page where this is said to be normal and required. 

[http://support.lexmark.com/index?page=content&id=HO3562&locale=EN&userlocale=EN_UK](http://support.lexmark.com/index?page=content&id=HO3562&locale=EN&userlocale=EN_UK)

Any help much appreciated as i want to get setup correctly as this is the first time i have used linux in several years and so far i am liking it. 

Cheers.

---

### Post by The Cog on 2011-09-27
I don't like that. The iptables rule is allowing any device anywhere in the world to talk to any UDP port on your computer provided that the other machine calls you from its port 5353. I wonder if they have transposed the in/out src/dest pairs in those instructions. 

The ufw rule looks more like I would expect. It allows anything to talk to your mdns service, which shouldn't be particularly harmful. If your printer has a fixed IP address, then it might be better to only allow that printer in rather than allowing connections from anywhere, but I wouldn't worry too much about it.

I'd like to hear Bhodi's opinion, if he's reading this.

I'll move this to the security forum where it's more likely to be seen by the right people and less likely to get buried.

---

