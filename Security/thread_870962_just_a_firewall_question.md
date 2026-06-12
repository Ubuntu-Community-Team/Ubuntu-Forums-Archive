---
title: "just a firewall question"
date: 2008-07-26
forum: Security
---

### Post by ontherooftop on 2008-07-26
I know ubuntu has the built in firewall, so is it ok if I also use firestarter to monitor connections? does firestarter just work together 
with iptables , and basically is a log shower? because I know in windows
2 firewalls are bad. Thanks.

---

### Post by hyper_ch on 2008-07-26
firestarter is just a front-end for iptables... so those two don't interfere ;)

Are you sure you need to alter your iptables settings?

---

### Post by kevdog on 2008-07-26
iptables will only log if you set it up this way.  If doesn't have to logged dropped packets.  In fact by default, no logging of dropped packets is performed.  Firestarter is simply one GUI interface for iptables.

---

### Post by The Cog on 2008-07-28
iptables is a command-line configuration tool for configuring the firewall (netfilter) that is built into the kernel. 

You can write iptables scripts yourself (typically a few dozen to a few hundred lines) if you feel so inclined, or you can use a GUI tool like firestarter, guarddog, smoothwall etc. All the GUIs all end up using iptables commands to configure the firewall behind the scenes.

You would not want to use two competing firewall configuration tools, so if you use a GUI just use one, and don't try to write your own scripts at the same time.

---

