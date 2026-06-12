---
title: "How to rename linux host permanently ?"
date: 2010-12-03
forum: Server Platforms
---

### Post by albertwt on 2010-12-03
Hi All,

I got one problem with my linux webserver where I deployed from Virtual Machine template, usually i go to the console and then issue the command **hostname NEWSERVERNAME** to make it happens and then followed by editing the** /etc/hosts** file 

and its done, but how come this time after the reboot it reverts back to the old template name ?

i want it to be "wordpress" as the hostname but instead it reverts back to SSV as the name ?

any suggestion and comments is appreciated here.

Thanks.

---

### Post by soulresin on 2010-12-03
> **albertwt said:**
> Hi All,

I got one problem with my linux webserver where I deployed from Virtual Machine template, usually i go to the console and then issue the command **hostname NEWSERVERNAME** to make it happens and then followed by editing the** /etc/hosts** file 

and its done, but how come this time after the reboot it reverts back to the old template name ?

i want it to be "wordpress" as the hostname but instead it reverts back to SSV as the name ?

any suggestion and comments is appreciated here.

Thanks.

Change /etc/hostname.  Running "hostname NEWSERVERNAME" does not change it permanently.

---

### Post by sisco311 on 2010-12-03
The hosts file should look like:
```
...
127.0.0.1    localhost
127.0.1.1    **hostname-here**
...

```

---

### Post by albertwt on 2010-12-03
> **soulresin said:**
> Change /etc/hostname.  Running "hostname NEWSERVERNAME" does not change it permanently.

ah... thanks man for the tips.

---

### Post by albertwt on 2010-12-03
> **sisco311 said:**
> The hosts file should look like:
```
...
127.0.0.1    localhost
127.0.1.1    **hostname-here**
...

```

127.0.1.1 --> what is that used for ?

---

### Post by sisco311 on 2010-12-03
From [Debian Reference - Chapter 10 - Network configuration]("http://qref.sourceforge.net/quick/ch-gateway.en.html")

> Some software (e.g., GNOME) expects the system hostname to be resolvable to an IP address with a canonical fully qualified domain name. This is really improper because system hostnames and domain names are two very different things; but there you have it. In order to support that software, it is necessary to ensure that the system hostname can be resolved. Most often this is done by putting a line in /etc/hosts containing some IP address and the system hostname. If your system has a permanent IP address then use that; otherwise use the address 127.0.1.1.

---

### Post by albertwt on 2010-12-03
> **sisco311 said:**
> From [Debian Reference - Chapter 10 - Network configuration]("http://qref.sourceforge.net/quick/ch-gateway.en.html")

cool, now I understand the meaning behind :-)
Thanks man.

---

### Post by doccpu on 2010-12-03
ubuntu manuals and others say in gui go to system/preferences ( or admin) networkinng. Well there is network connections and network proxy and network tools but no networking  option. Do people that write the docs actually use ubuntu? Seems 90% of the time the docs say do this do that but that doesnt exist on a fresh ubuntu install.

---

