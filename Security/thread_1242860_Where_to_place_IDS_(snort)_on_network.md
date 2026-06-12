---
title: "Where to place IDS (snort) on network"
date: 2009-08-17
forum: Security
---

### Post by Tobywuk on 2009-08-17
I am thinking about installing an Intrusion detection system on my network using a dedicated box running linux and snort. 

Is it possible to place the box between my cable modem and Router, using two NIC's to relay the traffic back and forward?

If I were to do this, How would I get the traffic to be sent to/from each network card so the traffic "passes through" the box?

How would I then get snort to pick up the network traffic? From what I have read it works just by setting a NIC into promiscuous mode, but if i did this then I couldn't relay traffic?


Perhaps this is not the best way to do it and it would be better to just install a Hub (broadcasting data to all ports) and then attaching the snort box to this in promiscuous mode?

---

### Post by Rootong on 2009-08-18
I would like to recommend you try SPAN if you are using cisco. Basically, it's not a good idea to run it on the router which one is you are gonna to play with.

Then, I think you know what to do. Hope understand your question.

---

### Post by sasho_zl on 2009-08-18
You can install on the dedicated box a software like IP COP - [http://www.ipcop.org/index.php](http://www.ipcop.org/index.php) 

It's mission is:

[LIST]
[*] Provide a stable Linux Firewall Distribution.
[*] Provide a secure Linux Firewall Distribution.
[*] Provide an opensourced Linux Firewall Distribution.
[*] Provide a highly configurable Linux Firewall Distribution.
[*] Provide an easily maintained Linux Firewall Distribution.
[*] Provide an easily configured Linux Firewall Distribution.
[*] Provide reliable Support to the IPCop Linux user base.
[*] Provide an enjoyable environment for the Public to discuss and request assistance.
[*] Provide stable, secure, and easy to implement upgrades/patches for IPCop Linux.
[*] Develop an appreciation for both the Linux and Opensource movements in our user base.
[*] Develop a long lasting relationship with our userbase.
[*] Strive to adapt IPCop to meet the needs of the Internet of Tomorrow.
[*] Further develop the Linux Knowledge base of all Project Members and Users.
[/LIST]

---

