---
title: "Do I need firewall and antivirus software"
date: 2008-04-02
forum: Virtualisation
---

### Post by explorer716 on 2008-04-02
I am running Ubuntu 7.10 and have installed VMware-Server.  Within VMware I have installed Windows XP.  Do I need to install firewall and antivirus software on the virtual Windows XP?

---

### Post by zvacet on 2008-04-02
Even they are virtual they are still Windows.So if you plan go online with them then yes.

---

### Post by alexandermimix on 2008-05-19
I had the same question. 

I understand the need for antivirus on the geust, however wanted to know why a guest XP install would need firewall given that the internet connection comes via the host ubuntu? Shouldn't ubuntu be sort of acting as the guest OS's firewall?

---

### Post by mijanous on 2008-05-19
i think if you set the network setting to bridged than you need firewall and antivirus...if your're using NAT then it's up to you if you trust ubuntu that he firewall it or install another firewall....and if you're using host only you don't need firewall at all because only network you will get is between host and guest

---

