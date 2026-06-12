---
title: "how to set up gufw?"
date: 2011-02-20
forum: Security
---

### Post by werty2010 on 2011-02-20
[CENTER]( i started an another thread on the begginers but i was told to start one here )

[/CENTER]
im accessing internet through a lot of public hotspots so im a litle concerned about my "privacy".
so i installed gufw and tried to set it up.
i set incoming/outgoing to deny and added some exceptions to outgoing, but despite the latter,the moment i set outgoing to deny nothing seems to "move".

could someone please guide me step to step on how to set it up?
ive also heard about firestarter, should i try this one?

---

### Post by gdiloren on 2011-02-20
> **werty2010 said:**
> [CENTER]( i started an another thread on the begginers but i was told to start one here )

[/CENTER]
im accessing internet through a lot of public hotspots so im a litle concerned about my "privacy".
so i installed gufw and tried to set it up.
i set incoming/outgoing to deny and added some exceptions to outgoing, but despite the latter,the moment i set outgoing to deny nothing seems to "move".

could someone please guide me step to step on how to set it up?
ive also heard about firestarter, should i try this one?
You set it right to first deny in and out, but you then have to allow "out" ports like 80 for htpp or 25 for pop. All this is automatically done by clicking add and clicking the predefined tab where you select to allow out http, pop etc... Please see the link for the last sticky in particular [http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

---

### Post by mikewhatever on 2011-02-20
The real danger of public hotspots is unencrypted wireless connection which can be sniffed. As you probably know, firewalls don't protect from sniffing. Is there a reason for gufw? Do you run any servers on the machine?

---

### Post by Frogs Hair on 2011-02-20
You may have seen this already. [http://www.cs.wcupa.edu/~rkline/Ubuntu/firewall.html](http://www.cs.wcupa.edu/~rkline/Ubuntu/firewall.html)

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by werty2010 on 2011-02-21
> **gdiloren said:**
> You set it right to first deny in and out, but you then have to allow "out" ports like 80 for htpp or 25 for pop. All this is automatically done by clicking add and clicking the predefined tab where you select to allow out http, pop etc... Please see the link for the last sticky in particular [http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

ive already done the predefined tabs after denying in and out but gufw acts like i haven't set any rules

---

### Post by uRock on 2011-02-21
I only block incoming traffic. The only reason to block outgoing would be to block a port being used for outgoing traffic, in which case I would recommend uninstalling the program that you don't want going online.

The firewall will not protect your communications from being seen on the network. It will only protect services such as file shares from being seen on public networks.

---

### Post by AbuSix on 2011-03-06
did you add the port 53 (udp) ?

[img]http://www.imgplace.com/img143/9149/69screenshot.png[/img]

---

