---
title: "How To Install And Use Harden remoteaudit"
date: 2007-03-30
forum: Server Platforms
---

### Post by sheffrem on 2007-03-30
Hi Everyone
Sorry if my english is not correct. I'm french.
I just Recently moved from fedora core to ubuntu 6.06.
Now, a friend of mine told me about harden-remoteaudit and how we could use it to test our windows servers in our school. But i installed the package called harden-remoteaudit and dont know what to do next since i'm a bit new to linux.

---

### Post by elst on 2007-03-31
I haven't used it, but the listing implies that it is actually the "Nessus" product, which is fairly well known:

> 
$ aptitude show harden-remoteaudit
Package: harden-remoteaudit
State: not installed
Version: 0.1.22
Priority: optional
Section: universe/admin
Maintainer: Ola Lundqvist <opal@debian.org>
Uncompressed Size: 32.8k
Depends: nessusd
Suggests: nessus, satan, nagios | netsaint, dsniff, harden-nids, idswakeup, ettercap
Description: Audit your remote systems from this host
 This package helps you to install a set of tools to check remote systems, sniff for passwords and more. Observe that this kind of activity can be illegal so you have to check if you are authorized to do so in the environment where you install this package. 
 
 You can check exploits, sniff for passwords and similar things. 
 
 Nessus note: You have to have the nessus client installed on some host. The client is provided by the 'nessus' package. You can install it on the same host but that is not necessary. 
 
 NOTE! This package includes packages that can damage the system that you audit. It should ONLY be used to audit hosts, networks or systems that you are allowed to audit. I repeat: it can damage the hosts that are checked. You have been warned!


Usual caveat: security testing your servers, and especially password testing, should only be done once you have written permission from a superior to CYA, even if you are the sole administrator. Apart from the legal issues, if the results are bad then it prevents people from trying to "shoot the messenger".

---

