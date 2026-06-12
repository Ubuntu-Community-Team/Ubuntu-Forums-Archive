---
title: "IPv6 and Firestarter"
date: 2007-09-26
forum: Server Platforms
---

### Post by stmurray on 2007-09-26
I am a new user of Ubuntu and I have sucessfully installed Gutsy on a new computer I built.  I installed Firestarter (appears to be the firewall of choice) and vnc4server (which I use over an ssh tunnel).  In testing Firestarter, it appears that it does not stop native IPv6 traffic and even worse, vnc4server (and vino the "remote desktop" tool, for that matter) actually opens a IPv6 service at the appropriate port (5900,5901,etc) that is completely unfiltered by Firestarter.  iptables has quite a few rules that i assume Firestarter put in but ip6tables has no rules.  Does Firestarter support native IPv6?  

This default installation is a little scary, because people would believe they are protected especially those with a laptop in a public WAN) and they have an open port that anyone can attmpt to connect to and attack.  The risk probably isn't huge for most home PCs, as very few people have IPv6 routing to and from the Internet, but anyone on the local-link (local subnet on an ethernet connection) will be able to connect to the port.

Are people aware of this issue?  What are they doing to protect-- disabling IPv6?, manually configuring ip6tables (ouch!)?, or using another firewall?

Sean T Murray

---

### Post by steve.horsley on 2007-09-27
That's a very good question. I haven't seen or heard of any IPv6 firewall GUIs yet, and I don't think I'm good enough to write one. For really simple stuff you could hand-roll ip6tables scripts, but surely, eventually, someone must do a GUI. I look forward to hearing of one.

You could always copy the iptables script that firestarter generates and hand-substitute the address strings.

---

### Post by ruibernardo on 2007-09-27
Firestarter is the firewall of choice for many users, but it isn't the officially recommended one by Ubuntu. That would be Shorewall. 

Anyway, even Shorewall doesn't support ipv6, nor does the other popular firewalls (iptables scripts/frontends): firestarter, firehol, guarddog, fwbuilder. None of them use ipv6. 

How to get rid if this problem? Easy, just blacklist the ipv6 module. It's one of the first things I do in a fresh install. Edit the file /etc/modprobe.d/blacklist and add "blacklist ipv6" and reboot.

But if need ipv6, you can search ipv6 in synaptic. You will find some firewalls that support it.

---

### Post by stmurray on 2007-09-28
I looked at the iptables rules created by Firestarter.  My understanding of iptables is limited (my knowledge of other firewalls is  greater) and my understanding of necessary "holes" needed for Ubuntu to operate properly is even less.  However, the rules look like they allow more than they should.  (for example there is an ACCEPT on all UDP traffic from my  gateway router.  I assume this is because the gateway is also my DCHP server, but this still seems too much....)  The logging also seems incomplete (it doesn't log "ACK" scans, for example)

I wanted to compare it to shoregate, so I uninstalled Firestarter and installed shoregate.  I copied the example config for a single interface machine and this is too restrictive (I haven't tested it, but looking at the "polices" and "rules" it looks like things like DCHP aren't going to work. ) 

Shoregate seems to be designed as a network firewall rather than a personal firewall, but it certainly can be used as a personal firewall with some tweaking to create rules and policies for a semi-trusted local network.  Does anyone know of an example Shoregate config for a workstation-type ("personal") firewall?  If not, I can try to create one.

Sean T Murray

---

### Post by ruibernardo on 2007-10-01
Shoregate? You mean shorewall, right? 

To use shorewall with only one interface (personal firewall?) just copy the configuration files from /usr/share/doc/shorewall/examples/one-interface/* to /etc/shorewall/. 

Add your rules to the rules file. You can use the macros defined for many protocols. Search them in /usr/share/shorewall/macro.* and use them using their extension as the protocol you want to accept. An example:

```
SSH/ACCEPT           net              $FW
```SSH is defined in the file macro.SSH. HTTP is defined in macro.Web (Web/ACCEPT), etc. Take a look at the comments in the example files, at the man pages and at their [website]("http://www.shorewall.net/3.0/Documentation_Index.html"). Shorewall is the most complete and powerful "firewall". It can setup almost everything that iptables can do. The example configuration works out of the box for eth0. Add additional rules as needed and enable shorewall in shorewall.conf and /etc/default/shorewall to run shorewall).

[SIZE=3]**About IPV6**[/SIZE]
Just a note about IPV6. I've found this [bug report]("https://bugs.launchpad.net/ubuntu/+source/netcfg/+bug/24828") about IPV6 being enabled in Ubuntu by default. Apparently it has a bug fix released in Feisty (in the update to  glibc_2.5-0ubuntu13, not the fresh install. Actually an updated Feisty system has  glibc_2.5-0ubuntu14).

Can somebody confirm that this solves the ipv6 problem and makes "blacklist ipv6" not necessary?

---

