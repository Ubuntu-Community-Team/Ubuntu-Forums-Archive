---
title: "IPCHAINS with ubuntu howto"
date: 2005-05-08
forum: Server Platforms
---

### Post by alred on 2005-05-08
hi , 
i managed to setup ipchains in redhat9
but i can't do that in ubuntu , i can't insert ipchains into the kernel in the first place ,
does anybody know how to insert ipchains in the ubuntu kernel ,
where can i get the ipchains.ko(?) inorder to insert ipchains in the ubuntu kernel ?
any pointers to documentions or successful experience in this issue are badly needed ...
thanks in advance ......

---

### Post by LordHunter317 on 2005-05-08
IPCHAINS is deprecated as of 2.4 and 2.6 and should only be used in specific situations (which if you knew, you wouldn't be posting).  RH keeps it around for legacy reasons.

Use iptables, it's superior replacement.  I should also point out that Ubuntu as shipped doesn't require a firewall as it has no services running that are Internet accessible.  Documentation for iptables is at netfilter.org

---

### Post by alred on 2005-05-11
ok ....... done writing my ipchains into iptables
ubuntu with it damn new kernel 2.6 , no choice ....
iptables more or less same with ipchains , the only problem is the logging switch .......

by the way is there any way to install xinted in ubuntu , 
what is the status of xinted in ubuntu  ?
dose ubuntu comes with xinted package ?

i need xinted to work with my firewall . thanks in advance

---

### Post by LordHunter317 on 2005-05-11
[QUOTE=alred]ok ....... done writing my ipchains into iptables
ubuntu with it damn new kernel 2.6 , no choice ....[/quote]This isn't true.    2.6 supports ipchains, becuase there are still a few legacy things iptables cannot do yet.

However, you **do not want to use ipchains** so stop complaining.  A properly written iptables ruleset is both faster and more secure then it's nearest equivalent in ipchains.

> iptables more or less same with ipchains , the only problem is the logging switch .......Umm, you can log just fine with iptables, but I rarely bother as the logging is mostly useless for anything but debugging.

> by the way is there any way to install xinted in ubuntu ,Yes, sudo apt-get install xinetd.  It may be in universe, which would require editing your /etc/apt/sources.list first.

---

### Post by alred on 2005-05-11
> This isn't true. 2.6 supports ipchains, becuase there are still a few legacy things iptables cannot do yet. 
so ubuntu do supports ipchains afterall , how to ?
do i need to re-compile the kernel or some other ?
or am i missing something obviously simple ?
somehow i really love ipchains although i don't mind using iptables ...........

thanks for the method for install xinted ,
i really have to learn a lot about ubuntu and debain style .......

thanks again

---

