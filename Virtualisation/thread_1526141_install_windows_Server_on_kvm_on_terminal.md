---
title: "install windows Server on kvm on terminal"
date: 2010-07-07
forum: Virtualisation
---

### Post by Nixforce on 2010-07-07
I have a Virtual Server, and want to find out if i can setup a windows 2000, 2003, 2008 Server on a KVM on an ubuntu os.. I would like a remote desktop on my system. Which of the following is the best to do it, if its possible

Ubuntu 10.04 LAMP 32 bit
Ubuntu 10.04 LAMP 32 bit Version 	
Ubuntu 10.04 minimal 32 bit
Ubuntu 10.04 Minimal x64
Ubuntu 9.04 64 bit
Ubuntu 9.04 64 bit Version 	
Ubuntu 9.10 x86_64.

---

### Post by naelq on 2010-07-08
hi,
could you elaborate some more regarding what hardware do you have? & what loads do you expect?

---

### Post by Nixforce on 2010-07-09
The Server will only get around 1000 visitors a day, until i start marketing it. I can upgrade the virtual server as its running on a cloud, and have the option to increase the system. 

Its currently running Ubuntu 10.04 32 bit with a guaranteed 512mb Ram, burstable to 2 GB.

Thanks

---

### Post by TheFu on 2010-07-09
Probably not.  A virtual server is already using some kind of virtualization. Only 1 kind of virtualization can be active at a time on a physical machine.  If you stay with Linux clients/guests, then you could use other techniques like chroot-jails or containers to achieve similar results as full virtualization. I've never used jails or non-Solaris containers, so I don't know how well they really work.

1,000 or 100,000 visitors can easily be handled by a single server provided you don't require a DB hit for each web page load. Good system AND application design will go a long way towards scalability.

---

### Post by Nixforce on 2010-07-10
Hi TheFu,

Thanks!! I got help from the OpenBD community, and someone there got the OpenBD installed for me on ubuntu server, so im all set, now need to learn how to create subdomains, and where the default document is stored, so i can setup ftp to it.

---

### Post by TheFu on 2010-07-10
> **Nixforce said:**
> Hi TheFu,

Thanks!! I got help from the OpenBD community, and someone there got the OpenBD installed for me on ubuntu server, so im all set, now need to learn how to create subdomains, and where the default document is stored, so i can setup ftp to it.

So BSD subdomains are just logical separations, like Solaris containers?  I hope they or you are not confusing DNS domains with something related to virtualization "domains."  Sun used to call their first split servers "domains" but it was a physical way to split a physical server into multiple physical servers. Seems they have "logical domains" these days. [http://en.wikipedia.org/wiki/Logical_Domains](http://en.wikipedia.org/wiki/Logical_Domains)  Or I could be completely confused myself.

Do you check whether the VMX bios extensions are available on your virtual host?  This command [INDENT][FONT=Courier New]egrep '^flags.*(vmx|svm)' /proc/cpuinfo[/FONT]
[/INDENT][FONT=Verdana]should tell you whether VT-x or whatever AMD calls it is available. [/FONT]If that is the case, then you should be able to run any VM on that VPS under Linux, BSD, OpenSolaris, or an MS host.  I avoid MS to avoid the license costs. When you have 1 or 2 hosts, it doesn't matter much, but when you have 50-5000 OS installs, those costs add up.

Anyway, I hope what you are doing gets you what you need.

---

