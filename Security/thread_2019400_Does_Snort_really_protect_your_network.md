---
title: "Does Snort really protect your network?"
date: 2012-07-07
forum: Security
---

### Post by samiux on 2012-07-07
Hi all,

As requested by the admin of this forum, I update this thread as the following :

The official page of [Snort]("http://www.snort.org/") state the following :

> Snort® is an open source [COLOR="Red"]network intrusion prevention and detection system (IDS/IPS)[/COLOR] developed by Sourcefire. Combining the benefits of signature, protocol, and anomaly-based inspection, Snort is the most widely deployed IDS/IPS technology worldwide. With millions of downloads and nearly 400,000 registered users, Snort has become the de facto standard for IPS.

Snort can be configured as an IPS.  All the suspicious traffic will be blocked or dropped.  However, some skilled hackers can bypass the rules of the Snort.  Want to see the proof?  Yes, here you are.  Please watch this [video]("http://samiux.blogspot.hk/2011/07/does-snort-really-protect-your-network.html") for details how the Snort rules be bypassed.

Samiux

---

### Post by uRock on 2012-07-07
I've always been under the impression that Snort logs suspicious activity, not prevent it.

---

### Post by haqking on 2012-07-07
In short, NO, YOU do !

The only thing that protects a network is a knowledgeable and skilled Administrator or User, under that definition I also mean it is their responsibility to communicate to their users or line manager who should then arrange for all users to be educated into good habits.

There is no single or collection of products software or hardware which "really" protect or secure your network, security is a process not a product.

The only things that help protect and secure a network are:

Skills and Knowledge
Continuing education and proactive management and administration


but above all....LUCK ;-)

Peace

Edit: and not paying too much attention to forum users, ill informed opinions and herd following !

---

### Post by Soul-Sing on 2012-07-07
> Edit: and not paying too much attention to forum users, ill informed opinions and herd following !

Nah, go with the flow :)

---

### Post by samiux on 2012-07-08
> **uRock said:**
> I've always been under the impression that Snort logs suspicious activity, not prevent it.

The following is quote from the official site of [Snort]("http://www.snort.org/") : 

> Snort® is an open source network intrusion prevention and detection system (IDS/IPS) developed by Sourcefire. Combining the benefits of signature, protocol, and anomaly-based inspection, Snort is the most widely deployed IDS/IPS technology worldwide. With millions of downloads and nearly 400,000 registered users, Snort has become the de facto standard for IPS.

Samiux

---

### Post by uRock on 2012-07-08
Routers and switches are the primary firewalls/IPSs in the business world. Snort, and other host base detection systems, would mostly be run to see and alert to traffic not being filtered by the networking hardware.

---

### Post by samiux on 2012-07-08
> **uRock said:**
> Routers and switches are the primary firewalls/IPSs in the business world. Snort, and other host base detection systems, would mostly be run to see and alert to traffic not being filtered by the networking hardware.

Routers, switches and firewalls cannot protect your network from being attacked.  But, Snort can do something on the protection.  Unfortunately, skilled hackers can bypass the rules of the Snort.  (Please see the #1).

One of the methods to attack your network is in this [thread]("http://ubuntuforums.org/showthread.php?t=2017608").

This [video]("http://samiux.blogspot.hk/2012/04/undetectable-trojan-on-windows-7-sp1.html") is going to proof that anti-virus and firewall are useless in some occasions.

Snort can be integrated in a router/gateway.  The most famous open source IPS is [Untangle]("http://www.untangle.com/").  It is integrated in a router/gateway or standalone.

Snort also can be installed in dedicated server or host in a box to act as a NIDS/NIPS or HIDS/HIPS respectively.

Samiux

---

