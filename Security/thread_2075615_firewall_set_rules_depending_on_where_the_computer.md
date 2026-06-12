---
title: "firewall: set rules depending on where the computer is conecting."
date: 2012-10-24
forum: Security
---

### Post by yohannm on 2012-10-24
Hello everyone,

I m looking for a way to have a different configuration of my firewall depending if I m connecting to my home network or not.

At home, I share files between computers without password, the firewall of the router do its job correctly. The firewalll of my laptop stay activated with the ports to allow samba working correctly.

I d like to get an automatical rule which permit to close the samba's port when I m not connected to my personal network. I did not find anything using ufw.

Is it possible to configure iptables in order it detects the local network and set the firewall in consequence?

thanks in advance for your answers.

---

### Post by kevdog on 2012-10-25
I set all my iptables rules in a bash script file.  On a specific rule you might want to write a function or routine that would first grab your ipaddress (which could be done by grepping and awking the results of ifconfig) and then by using an if statement compare the results of the ip address and depending on the result execute one of two statements.  

Does this make any sense?

---

