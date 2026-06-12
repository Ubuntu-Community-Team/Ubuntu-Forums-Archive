---
title: "hit by a source destination(need help)"
date: 2009-09-07
forum: Security
---

### Post by oldboy1985 on 2009-09-07
for past few months i have been using firestarter as my firewall for ubuntu 9.04
but from past few weeks a recieved a error during booting
**starting the firewall firestarter           [fail] **

also 
i received this message for quite few times on firestarter

**hit from source <source's ip address>**

although i have blocked the sources but still i would like to find a more secure solution 

please help:(

---

### Post by sasho_zl on 2009-09-07
Remove Firestarter. It is not supported for a few years now. Install gufw.

---

### Post by __p1n__ on 2009-09-07
> **oldboy1985 said:**
> for past few months i have been using firestarter as my firewall for ubuntu 9.04
but from past few weeks a recieved a error during booting
**starting the firewall firestarter           [fail] **

also 
i received this message for quite few times on firestarter

**hit from source <source's ip address>**

although i have blocked the sources but still i would like to find a more secure solution 

please help:(

Trying running a VMM stack with NetBSD (using pf firewall) as your dom0 and ubuntu as a guest os (without firewall.)  For an opensource solution use Xen 3.4 or higher for your hypervisor.

---

### Post by SoftwareExplorer on 2009-09-07
> **__p1n__ said:**
> Trying running a VMM stack with NetBSD (using pf firewall) as your dom0 and ubuntu as a guest os (without firewall.)  For an opensource solution use Xen 3.4 or higher for your hypervisor.
Surely there's an easier way for a newer user.

---

### Post by oldboy1985 on 2009-09-07
> **sasho_zl said:**
> Remove Firestarter. It is not supported for a few years now. Install gufw.


i have installed Gufw 9.04.2

but how do i know that it is secure or not its interface is too simple
and there is no option for blocked connections

---

### Post by sasho_zl on 2009-09-08
Gufw is just a tool for configuring the real powerfull firewall - the Linux kernel Netfilter. You dont need anything more complex for that configuration. Once turned on it is very secure. 
Firestarter is doing the same job but because it is not supported any more and it's run with root privileges is a potential security risk.

---

### Post by oldboy1985 on 2009-09-08
> **sasho_zl said:**
> Gufw is just a tool for configuring the real powerfull firewall - the Linux kernel Netfilter. You dont need anything more complex for that configuration. Once turned on it is very secure. 
Firestarter is doing the same job but because it is not supported any more and it's run with root privileges is a potential security risk.

thanks for that 

but how will i know that there is a hit from any source or not 
like where is its log created??
since i m new to the ubuntu i dont know much about this

---

### Post by sasho_zl on 2009-09-08
The part of the logs you need is in /var/log/messages
Have in mind that Linux is very secure by default and you don't need to worry about those things. :)

---

### Post by oldboy1985 on 2009-09-09
> **sasho_zl said:**
> The part of the logs you need is in /var/log/messages
Have in mind that Linux is very secure by default and you don't need to worry about those things. :)

thanks =D>

---

