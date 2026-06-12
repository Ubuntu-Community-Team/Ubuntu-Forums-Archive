---
title: "IPTState questions"
date: 2008-10-26
forum: Security
---

### Post by lovinglinux on 2008-10-26
I have decided to uninstall Firestarter and create my own iptables rules. One thing I miss is the Firestarter "Active Connections" feature, so I'm using IPTState application to replace this feature.

My concern is that a lot of people say that Firestarter main issue is due to the root requirements for running the gui, which is necessary to monitor active connections. But IPState also requires root privileges to run. Is this also a security risk? If yes, how my machine security could be compromised?

Another question I have related to IPTstate is due to some connections that stay listed as ESTABLISHED even after disconnection the network. This occurs in Firestarter and IPTState, so I guess is a problem in the netfilter. Nevertheless, IPTState allows to delete a state. What does this really means? When I delete a state the connection is no longer considered as ESTABLISHED if the other machine tries to connect again or it just remove the entry from IPTState log?

---

### Post by kevdog on 2008-10-26
Where do I find this IPTState application or a link for its documentation?  I've never heard of the application.

---

### Post by lovinglinux on 2008-10-26
> **kevdog said:**
> Where do I find this IPTState application or a link for its documentation?  I've never heard of the application.

[http://www.phildev.net/iptstate/](http://www.phildev.net/iptstate/)

---

### Post by lovinglinux on 2008-10-26
and this one [http://packages.ubuntu.com/hardy/iptstate](http://packages.ubuntu.com/hardy/iptstate)

---

### Post by lovinglinux on 2008-11-04
> **lovinglinux said:**
> Another question I have related to IPTstate is due to some connections that stay listed as ESTABLISHED even after disconnection the network. This occurs in Firestarter and IPTState, so I guess is a problem in the netfilter. Nevertheless, IPTState allows to delete a state. What does this really means? When I delete a state the connection is no longer considered as ESTABLISHED if the other machine tries to connect again or it just remove the entry from IPTState log?

This one I figured out myself. When you delete a state from iptstate list you actually delete the connection state. So if the iptables has rules that accept only ESTABLISHED, RELATED incoming connections for example, this will make the iptables refuse connections that where deleted.

---

