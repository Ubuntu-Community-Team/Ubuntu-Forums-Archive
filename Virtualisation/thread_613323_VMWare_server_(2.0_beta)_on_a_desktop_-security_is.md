---
title: "VMWare server (2.0 beta) on a desktop -security issues?"
date: 2007-11-14
forum: Virtualisation
---

### Post by rliegh on 2007-11-14
Hi, all

I have just downloaded, installed and appropriately edited /etc/vmware/hostd/authorization.xml and now everything's running.

**BUT** I'm worried because you have to use a 'web ui' to interface with the bloody thing! :evil: This means that it's running a web server and listening on at least port 80 ([http://127.0.0.1](http://127.0.0.1) gets me the login screen). This is a **hella bad thing** when it comes to security!!

So what I am wondering is this:
1)what ports are being used? (I think the installer said 80,443 and 902 -but I can't find the file I saved that info to so I don't know if that's right).
2)are these ports visible from the internet?
3)how can I make them ***INACCESSIBLE*** from the internet?

Thanks for all of your help.

---

### Post by veloce on 2007-11-15
> **rliegh said:**
> Hi, all

I have just downloaded, installed and appropriately edited /etc/vmware/hostd/authorization.xml and now everything's running.

**BUT** I'm worried because you have to use a 'web ui' to interface with the bloody thing! :evil: This means that it's running a web server and listening on at least port 80 ([http://127.0.0.1](http://127.0.0.1) gets me the login screen). This is a **hella bad thing** when it comes to security!!

So what I am wondering is this:
1)what ports are being used? (I think the installer said 80,443 and 902 -but I can't find the file I saved that info to so I don't know if that's right).
2)are these ports visible from the internet?
3)how can I make them ***INACCESSIBLE*** from the internet?

Thanks for all of your help.

you DO have a firewall between you and the internet don't you?  If not vmware is the least of your problems.

---

### Post by Lem on 2007-11-15
If your running a router (even a combined modem/router) then unless you specifically forward port 80 to your machine, it will not be accessible from the internet.

---

### Post by rliegh on 2007-11-15
> **veloce said:**
> you DO have a firewall between you and the internet don't you?  If not vmware is the least of your problems.
Does running iptables count, or do you mean a seperate machine?

---

### Post by Delvien on 2007-11-15
> **rliegh said:**
> Does running iptables count, or do you mean a seperate machine?

iptables are running wheither you know it or not, Unless you disable the damned thing.

You will have to use your router to port forward to the VM box in order to have the webUI interface to work properly.

If you dont port forward, you should be fine.

---

### Post by veloce on 2007-11-15
> **rliegh said:**
> Does running iptables count, or do you mean a seperate machine?

Yes, iptables does count as a firewall (by definition I suppose).  

As others have stated, unless you have specifically opened a hole in your firewall, additional services (like a webserver) running on your computer make no difference to its security wrt the internet connection.

---

### Post by bodhi.zazen on 2007-11-15
You can easily limit access to :80 the local host via iptables.

---

### Post by rliegh on 2007-11-15
I was wondering about iptables based on the comment about my having a firewall between me and the internet (I know iptables comes by default, I was wondering if that comment was implying that iptables wouldn't cut it). 

I haven't done anything grant access to the outside world, no forwarding, nothing like that. What I have done is installed firestarter and used that to configure/run iptables. 

Firestarter doesn't run automatically, and it's easy to forget; I'm hoping that the iptables rules it set up still are in force at boot up time wether I run it or not. :confused:

---

### Post by bodhi.zazen on 2007-11-15
> **rliegh said:**
> Firestarter doesn't run automatically, and it's easy to forget; I'm hoping that the iptables rules it set up still are in force at boot up time wether I run it or not. :confused:

This is a common misconception.

Firestarter is NOT a firewall, it is a configuration tool for IPTables.

AND, Firestarter runs as root ...

So, you should only run firestarter when you need to configure IPTables, then shut it down / off.

Once IP Tables is configured it is active at boot and you do NOT need to run Firstarter.

---

