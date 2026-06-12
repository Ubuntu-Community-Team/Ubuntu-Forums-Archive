---
title: "iptables vs. ufw ?"
date: 2011-05-11
forum: Security
---

### Post by nbrochu on 2011-05-11
Is one better than the other in terms of security and or ease of set up? im currently using iptables but whenever i read something about a firewall it points to ufw.

---

### Post by Frogs Hair on 2011-05-11
UFW is a GUI for iptables , you can work with iptables via the command line or a GUI .

---

### Post by nbrochu on 2011-05-11
Thanks for the clarity.

---

### Post by Dave_L on 2011-05-11
Actually, ufw is a command line front-end for iptables. gufw is a GUI for ufw.

---

### Post by bodhi.zazen on 2011-05-11
Depends on your needs and familiarity with iptables , network protocols (tcp/ip), and iptables.

If you are new, ufw is nice as the syntax of ufw is very similar to iptables, thus once you learn to use ufw, and you wish to transition to iptables, it is easy.

The problem is that ufw does not offer all the options to iptables so if you have complex needs iptables (or a different front end such as shorewall) is probably better.

The advantage of iptables is that the syntax is easy to understand (assuming you know networking protocols), it is easy to use, and quite versatile.

---

### Post by resting on 2012-05-07
> **bodhi.zazen said:**
> Depends on your needs and familiarity with iptables , network protocols (tcp/ip), and iptables.

If you are new, ufw is nice as the syntax of ufw is very similar to iptables, thus once you learn to use ufw, and you wish to transition to iptables, it is easy.

The problem is that ufw does not offer all the options to iptables so if you have complex needs iptables (or a different front end such as shorewall) is probably better.

The advantage of iptables is that the syntax is easy to understand (assuming you know networking protocols), it is easy to use, and quite versatile.

i have this problem. i had disabled ufw.
my ftp connection to a custom doesn't work.
i flush iptables.
the connection works.

i'm bluffed.  are the 2 different things or not?

---

### Post by Ms. Daisy on 2012-05-07
You cannot modify both iptables and ufw.  If you want to use iptables exclusively then you should uninstall ufw.  If you want to use ufw, then if you have any existing iptables scripts you will want to disable them.

---

