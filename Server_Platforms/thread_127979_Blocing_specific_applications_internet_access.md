---
title: "Blocing specific applications internet access"
date: 2006-02-10
forum: Server Platforms
---

### Post by dgh on 2006-02-10
I am fairly new to the linux world and I may have understood some things wrong, but please correct me if I have.

I know that linux system is very secure when installing trusted applications from repositories, but how about untrusted software? I have understood that iptables in linux kernel is unable to block specific applications from accessing the internet. If you install some untrusted application which doesn't need internet connection, it would be good to be able to block that. Now someone could suggest only allowing necessary ports and rules from iptables, but what prevents untrusted application from using port 80 (http) for example?

I thought that linux was the system which will let you do what you want, but if this is not possible I think windows is more flexible in this area. Using applications  only from repositories is not an option. They can never cover every single need, and there will always be private applications.

---

### Post by LordHunter317 on 2006-02-10
[QUOTE=dgh] I have understood that iptables in linux kernel is unable to block specific applications from accessing the internet.[/quote]It can, but not in any way I would define as useful.

> If you install some untrusted application which doesn't need internet connection, it would be good to be able to block that.If you really need to run untrusted applications, the only sane solution to limit their access is to run them in a virtual machine.  This applies to Linux and Windows.

 > I thought that linux was the system which will let you do what you want, but if this is not possible I think windows is more flexible in this area.It wasn't until XP SP2 that MS shipped any sort of firewall/filtering that could function based on application.

> They can never cover every single need, and there will always be private applications.The only software I have installed on my system that isn't from a repository is either bleeding-edge development (And will be there eventually) or commercial.

---

### Post by dgh on 2006-02-14
[QUOTE=LordHunter317]It wasn't until XP SP2 that MS shipped any sort of firewall/filtering that could function based on application.[/QUOTE]

Yes, but there has always been third party software firewalls for XP that will ask permission for internet connection with every application. I just wonder why there is not a single one firewall like that for Linux, as far as I know... I came up with one good example where you could need this kind of firewall: You can prevent your backuped (cracked, but you of course own a legal copy of it ;)) application from calling home.

---

### Post by nixclusive on 2006-02-14
*systrace*:

[http://www.citi.umich.edu/u/provos/systrace/](http://www.citi.umich.edu/u/provos/systrace/)

> Features
Confines untrusted binary applications.
Interactive Policy Generation with Graphical User Interface.
Supports different emulations: 
GNU/Linux, BSDI, etc..
System Call Argument Rewriting.
Non-interactive Policy Enforcement.
Remote Monitoring and Intrusion Detection.
Privilege Elevation: Add-on capabilities.

But this requires some sort of kernel patch. Sorry, I'm a n00b myself ;)

---

### Post by dgh on 2006-02-14
[QUOTE=nixclusive]*systrace*:
[http://www.citi.umich.edu/u/provos/systrace/](http://www.citi.umich.edu/u/provos/systrace/)
But this requires some sort of kernel patch. Sorry, I'm a n00b myself ;)[/QUOTE]

This seems very good :cool:

---

### Post by dgh on 2006-02-25
[QUOTE=www.pandasoftware.com]Firewall protection. Protection against network attacks, **application** and system rules management.[/QUOTE]

[Panda DesktopSecure for Linux]("http://www.pandasoftware.com/download/beta/empresas/info_desktopsecure.htm")

Finally!

---

### Post by moopere on 2006-03-03
[QUOTE=dgh]Yes, but there has always been third party software firewalls for XP that will ask permission for internet connection with every application. I just wonder why there is not a single one firewall like that for Linux, as far as I know... I came up with one good example where you could need this kind of firewall: You can prevent your backuped (cracked, but you of course own a legal copy of it ;)) application from calling home.[/QUOTE]

I can't see how a firewall on a machine can limit net traffic per application on that same machine in an effective way.  What if the rogue program runs a process called something like..I don't know, bash, or login, or somesuch?  How can the system tell that this process is really not a bash shell?  How about rogue programs that come with their own tcpip stack and communicate with the hardware directly (or at least with the kernel directly)?

I think that a lot of so called 'personal firewalls' on Windows give a false sense of security.

Cheers,
Craig

---

