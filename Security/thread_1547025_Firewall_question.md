---
title: "Firewall question"
date: 2010-08-06
forum: Security
---

### Post by epos85 on 2010-08-06
Hello.

I want to know if ubuntu netbook remix have a built-in firewall, and how does this firewall work when i install applications like Valknut? Do i have to change firewall, or does it make the changes automatically?

If i need to manually change open ports in firewall, then i want a easy to understand gui, if there is one. I want to add port-ranges, with options [tcp],[udp],[both] or single ports with same options..


Im looking at Guarddog, since i installed all deps for Guidedog. Dont know how Guarddog would behave with ubuntu's config. 

Thanks :-)

---

### Post by kerry_s on 2010-08-06
ubuntu has ufw, install gufw if you want a gui manager.

---

### Post by cdenley on 2010-08-06
> **kerry_s said:**
> ubuntu has ufw, install gufw if you want a gui manager.

Ubuntu comes with UFW, but it is disabled by default. There is no point in filtering traffic that no process is listening for. If you install and start a listening process (Valknut?), then you probably wouldn't want to filter it.

---

### Post by kerry_s on 2010-08-06
yes, for got to mention that. you can enable it with the gui.

the gui is very basic & simple. see pics

---

### Post by utilitytrack on 2010-08-06
to **cdenley**

> There is no point in filtering traffic that no process is listening for.

Cool declaration. But might be some rootkit or trojan that send out traffic, for example, on 80 port. I'm don't right?

to **epos85**

Linux kernel has built-in firewall, it's called "Netfilter" and it represents a number of kernel modules. For manage and setting up the Netfilter a front-end "iptables" exist. Look into web for further info.

---

### Post by wacky_sung on 2010-08-06
The best firewall i personally feel and think is iptables which is so customize but it take time to learn.It is by default disable in Ubuntu.

---

### Post by surfer on 2010-08-06
ufw is just a frontend to iptables.

---

### Post by cdenley on 2010-08-06
> **utilitytrack said:**
> 
Cool declaration. But might be some rootkit or trojan that send out traffic, for example, on 80 port. I'm don't right?


Yes, anything the user installs can send traffic. Even malware. UFW doesn't filter outgoing traffic. Any malware which listens on port 80 already has root privileges, so it can create an iptables rule to allow connections easily.

---

### Post by bodhi.zazen on 2010-08-06
> **cdenley said:**
> Yes, anything the user installs can send traffic. Even malware. UFW doesn't filter outgoing traffic. Any malware which listens on port 80 already has root privileges, so it can create an iptables rule to allow connections easily.

UFW can be configured to filter outbound traffic.

At any rate :

First, Linux does not suffer from viruses / malware the way other OS do.

Second, you should read the security sticky at the top of these forums.

If you have a rootkit installed, your system has already been cracked, nothing is going to help you except fixing the hole that allowed unauthorized access in the first place or reinstalling the OS, depending on if you have more or less skill then the intruder.

---

### Post by utilitytrack on 2010-08-06
> **wacky_sung said:**
> ...iptables...by default disable in Ubuntu.

I'm not a experienced Ubuntu user :) and I don't understand this phrase. How so - it disabled? It's true?

---

### Post by bodhi.zazen on 2010-08-06
> **utilitytrack said:**
> I'm not a experienced Ubuntu user :) and I don't understand this phrase. How so - it disabled? It's true?

That statement is not true. Iptables is enabled by default, but the default settings are permissive.

That means all traffic in and out is allowed by default. This is acceptable as by default there are not listening services.

See the security sticky at the top of these forums.

If you wish to enable a firewall, take a look at ufw. If you want a graphical interface, use gufw.

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

---

### Post by utilitytrack on 2010-08-06
> **bodhi.zazen said:**
> If you wish to enable a firewall, take a look at ufw. If you want a graphical interface, use gufw.

Thanks, but I don't use any other fw except iptables. Also I don't have any GUI to it :))

In attachment if you interested you can see template (not finished) of iptables config based on Easy Firewall Generator script and adapted to 2.6 kernels and also adapted to launch as System V style script (from [FONT="Courier New"]/etc/init.d/[/FONT]).

---

### Post by wacky_sung on 2010-08-07
> **bodhi.zazen said:**
> That statement is not true. Iptables is enabled by default, but the default settings are permissive.

That means all traffic in and out is allowed by default. This is acceptable as by default there are not listening services.

See the security sticky at the top of these forums.

If you wish to enable a firewall, take a look at ufw. If you want a graphical interface, use gufw.

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
LOL...i have a good laugh over it due to the way how each of us interprets my statement.Probably i am poor in expressing my words.:D

---

### Post by bodhi.zazen on 2010-08-08
> **wacky_sung said:**
> LOL...i have a good laugh over it due to the way how each of us interprets my statement.Probably i am poor in expressing my words.:D

Ays I understand what you intended with that statement, in this case it simply needed a little (minor) clarification.

---

