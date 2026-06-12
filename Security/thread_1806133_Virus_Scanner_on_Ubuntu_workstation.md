---
title: "Virus Scanner on Ubuntu workstation"
date: 2011-07-17
forum: Security
---

### Post by cccc on 2011-07-17
Hi

We are using Ubuntu 10.04 Desktops as a productive workstations at our company.
Is it a good idea to install Virus Scanner, for example clamav on these ubuntu workstations?
We have VS rootkit scanner are already installed on all our servers.
BTW are you using VS on your Ubnutu Desktop?

---

### Post by HellesAngel on 2011-07-17
The simple answer is: It depends.  Security is not simply a matter of installing stuff on a PC and thinking you're done.  How does this fit in alongside everything else you do to secure your sensitive data?

---

### Post by Chayak on 2011-07-18
How much will it improve your security?: Very little.

It's a common misconception that installing some sort of antivirus makes you *safe* from malware like it's some kind of magical shield.  The vast majority of malware detection, aside from some behavioral based systems, relies on signatures that have to be created by analysts like myself.  If no one has created a signature for a piece of malware then it's not likely going to be detected unless heuristics flags is for some reason, which is hit and miss.

So why doesn't it work?  Well the biggest reason I can point out is that it's easy to change the signature of a file by using tools or changing compilers, etc.  That piece of malware won't be detected until another researcher creates a new signature.  In addition there is quite a bit of malware that's not widely distributed that goes totally undetected.

I say it will be of little improvement because the vast majority of its signatures are focused on windows malware.  It won't impact the security of your systems directly but it may catch something someone downloads before they send it on to a windows user.

You'd get a far greater benefit by having someone learn and configure Apparmor profiles for your standard applications.

---

### Post by inobe on 2011-07-18
all the information can be found here [https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)

---

