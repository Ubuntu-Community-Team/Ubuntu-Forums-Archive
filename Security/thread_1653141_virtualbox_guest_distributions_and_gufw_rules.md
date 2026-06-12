---
title: "virtualbox guest distributions and gufw rules"
date: 2010-12-26
forum: Security
---

### Post by arapaho on 2010-12-26
I test new distributions and new releases on virtualbox. And I try every solution on virtual system before making any changes to my host system. And sometimes instead of burning live cd I test iso's on Vbox as live cd without installing them on virtual disks, so I don't always know if there is any risk involved because I don't know so good other distributions.
On host I use Gufw and only block incoming connections. Usually I don't use strong passwords for guest distributions. I wonder if I have to make any additional rules for my host or/and guest distributions to safely use Vbox. Should I worry about any potential vulnerabilities coming from guest and possibility of a kind of breaking from inside, it means from guest to host? Should I use also very strong password on guest distributions?

---

### Post by bodhi.zazen on 2010-12-26
You should treat your guests the same as a physical machine, the security settings of the guest (password, firewall, etc) are the same as if you were using a physical machine.

It is extremely unlikely the guest could directly affect the host, but it could if it were compromised have access to your LAN via network protocols (ftp, http, etc).

---

### Post by Razor338 on 2010-12-27
dude,there's a strong bond between host and the guest operating systems.cuz both of them use same hardwares which are available in your pc.if you keep your guest os unsecured,it will directly affect the host too.so get this simple,pay same attention to both host and the guest!

---

### Post by bodhi.zazen on 2010-12-27
> **Razor338 said:**
> dude,there's a strong bond between host and the guest operating systems.cuz both of them use same hardwares which are available in your pc.if you keep your guest os unsecured,it will directly affect the host too.so get this simple,pay same attention to both host and the guest!

Almost none of that statement is true. Virtual machines are isolated from the host and it would be difficult to directly affect the host.

It is true you need to secure them, but they would affect the host most easily via network protocols.

Here is a nice overview:

[http://www.windowsecurity.com/articles/Security-Virtualization.html](http://www.windowsecurity.com/articles/Security-Virtualization.html)

Notice:

1. None of the threats cited are compromise of guest -> direct compromise of host.

2. Most of the threats are to the host. This is why people use a minimal (server or ESX)) install on server farms. The remainder are networks protocols.

3. They advise you secure your guests as you would a physical machine.

From the bottom, a nice summary is :

> These technologies are superior from a security stand point and from a performance stand point so it makes sense to favour such implementations.

Google search if you want further information (this citation was given as it seemed a nice overview).

---

