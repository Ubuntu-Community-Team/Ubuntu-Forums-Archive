---
title: "Problem opening ports"
date: 2010-01-12
forum: Server Platforms
---

### Post by kenichiaeb on 2010-01-12
Hello all.
A few days ago, I ordered a **ubuntu server** (on ovh.com).
Everything was going well until I installed mysql:
After the install, I tried to connect throught Navicat MySQL using SSH, but it says that the user or password it's not correct, obviusly this is not true.
I've been reading and I readed that I have to open the 22 port to use MySQL in the firewall, but I don't know how to do it.
How can I do?
Thanks for your help :D

---

### Post by kenichiaeb on 2010-01-12
I selft answered my own question xD
The answer, if anywone is looking for it is:
/sbin/iptables -A INPUT -i eth0 -p tcp --dport <the port to open>
Thanks anyway ;)

---

### Post by Lars Noodén on 2010-01-13
> **kenichiaeb said:**
> I selft answered my own question xD
The answer, if anywone is looking for it is:
/sbin/iptables -A INPUT -i eth0 -p tcp --dport <the port to open>
Thanks anyway ;)

You may also want to try some advanced tricks with IP Tables.  

See examples 3 and 4 in Barry O'Donovan's  [Advanced Features of netfilter/iptables](http://linuxgazette.berlios.de/108/odonovan.html)

And see Thiemo Nagel's [Preventing brute force attacks using iptables recent matching](http://www.e18.physik.tu-muenchen.de/~tnagel/ipt_recent/)

Even if you don't use those examples, it can be useful to see what IP Tables is capable of.

---

### Post by KnottyMars on 2010-01-13
I like shorewall as well, its been very well documented and you can get as crazy with the cheese whiz as you want. 

Ive seen some very basic and some very complex setups. 

Here is home page for documentation: [http://www.shorewall.net/index.htm](http://www.shorewall.net/index.htm) 

bascially, one file to modify for firewall rules (allow ssh, www, ftp, etc...)

Hope that helps.

---

