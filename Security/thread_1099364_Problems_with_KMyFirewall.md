---
title: "Problems with KMyFirewall"
date: 2009-03-18
forum: Security
---

### Post by Masterofpsi on 2009-03-18
I've decided to set up a firewall. I basically want to hide all ports and stop ping replies. I installed KMyFirewall and created a setup that looks like it does that. However, whenever I try to run the firewall, nothing happens. Visiting a test website confirms that my ports are the same as they were. Additionally, clicking the "install firewall" button does nothing. I know, because when I check the files that it said it would create, they're not there. I am running it as root.

I think this problem is probably related (perhaps the cause): when I type in "sudo service iptables start", I get "$iptables: unrecognized service."

Does anyone know what's happening?

---

### Post by iamkrazee on 2009-03-18
'iptables' service is of RedHat family, I wonder if it works here.

---

### Post by bodhi.zazen on 2009-03-18
> **Masterofpsi said:**
> I've decided to set up a firewall. I basically want to hide all ports and stop ping replies. I installed KMyFirewall and created a setup that looks like it does that. However, whenever I try to run the firewall, nothing happens. Visiting a test website confirms that my ports are the same as they were. Additionally, clicking the "install firewall" button does nothing. I know, because when I check the files that it said it would create, they're not there. I am running it as root.

I think this problem is probably related (perhaps the cause): when I type in "sudo service iptables start", I get "$iptables: unrecognized service."

Does anyone know what's happening?

Unless you are connected directly to the internet you are scanning your router when you do this.

See [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

> **iamkrazee said:**
> 'iptables' service is of RedHat family, I wonder if it works here.

I do not mean to be rude iamkrazee, but iptables is on every modern distro. See the link above and please, if you do not know, do not guess at security.

---

### Post by Masterofpsi on 2009-03-18
OK, so I'll have to connect directly after my family has gone to sleep. But that doesn't explain why iptables isn't listed in /etc/services, or why I can't install it.

---

### Post by bodhi.zazen on 2009-03-19
> **Masterofpsi said:**
> OK, so I'll have to connect directly after my family has gone to sleep. But that doesn't explain why iptables isn't listed in /etc/services, or why I can't install it.

Ah, yes, that explains your confusion.

It sounds as if you come from a rpm system.

Ubuntu does not list iptables as a service that way, it is not in /etc/init.d the way it is on a rpm system.

iptables is compiled into the kernel and if you look at /etc/init.d on a rpm system it is "simply" a script to configure iptables.

Ubuntu uses ufw and , by default, iptables is permissive, so it allows all traffic.

It does not need to be installed either.

Simply :

```
sudo iptables -L
``` and you will see.

See also : [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

