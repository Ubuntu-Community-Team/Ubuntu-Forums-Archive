---
title: "fireHOL failing"
date: 2009-09-10
forum: Server Platforms
---

### Post by [pl]ice on 2009-09-10
Hello,

I've been using fireHOL to manage the firewall(since i'm lazy)
remotly.

It has crashed once. One cannot flush the ip tables, while the firehol is running. it will crash the system.

2) just got locked out of remote server, while changing firehol config, and restarting it. Locked out my ssh. Now have to call the company to get me back in.
 I guess its my fault, should have build the firewall correctly :(

---

### Post by recentcoin on 2009-09-10
First off, love the icon!  Secondly, it's not that hard to manage iptables from the command line.  Google around to find the command you want, run it and then type in

iptables-save > /etc/iptables-save

This will save the iptables output for the rules without you really having to do much and it will re-add them on reboot.

---

