---
title: "The best firewall, with ip and mac blocks?"
date: 2009-03-18
forum: Security
---

### Post by rowebil on 2009-03-18
I have linux mint, which is Ubuntu but with all the drivers installed.

I want to know what is the best firewall for linux. I use litespeed web server enterprise. 
I want it to prevent intrusion attacks. DoS attacks.

I also want the option to maybe have online management, but will probably not happen because I don't have apache.


I want the option to block IP and MAC addresses.
What does everyone think is the best firewall?

---

### Post by bodhi.zazen on 2009-03-18
best is a matter of opinion.

you can do it all with the command line and perhaps a script with

iptables : [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

Or you can try any of the gui interfaces. I my experience, I advise starting with ufw and if you want a gui gufw.

If you want something ufw does not do , it takes as long to learn iptables as anything else.

[Uncomplicated Firewall - UFW - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw")

---

### Post by lovinglinux on 2009-03-18
To block ip you can use [moblock]("http://moblock-deb.sourceforge.net/"). It also has built in iptables scripts, for regular rules. So if you learn iptables commands you can use moblock for IP blocking and regular firewall.

You can change settings remotely using ssh.

---

### Post by cariboo on 2009-03-19
I would also suggest fwbuilder, from what I've seen of the latest version, it looks pretty customizable. Fwbuilder is in the repositories.

Jim

---

### Post by Nxion on 2009-03-19
+1 for UFW

For beginners, I would say start out with ufw. This reall helped me understand how to use and how iptables worked. It is simple, fast, and the syntax is cake to pickup!

---

### Post by hyper_ch on 2009-03-19
if you're behind a router then rather configure that one.

---

