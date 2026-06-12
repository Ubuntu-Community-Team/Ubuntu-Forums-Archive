---
title: "Services suddenly become unresponsive"
date: 2009-06-30
forum: Server Platforms
---

### Post by mjf on 2009-06-30
I am running Ubuntu 8.10 Desktop with apache and ircd-ratbox.  This is running as a VMWare guest hosted on a Windows XP box using bridged networking.

About 2 or 3 times a day, the web server and irc server suddenly become unresponsive.  I cannot connect to them even using the host Windows XP system.

However, from the Ubuntu system, I can still connect to websites, etc.  It seems it is just unable to accept incoming connections on the ports that it is listening on.

I execute:
```
$ /etc/init.d/networking restart
```
and the problem is solved until the next sudden occurence.

There are many levels where this can be failing (the Ubuntu system, the VMWare bridge, the network) but I don't how to begin diagnosing this issue.  Any suggestions?

---

### Post by LepeKaname on 2009-07-01
I think I know what the problem is. Perhaps you have a static IP? if so,  your ip is being changed automatically, so uninstall any dhcp package you have and be sure it is not running in memory: "ps -A | grep 'dhcp'" or something similar.

---

### Post by mjf on 2009-07-01
As you suspected, I am in fact on a static IP.  Is this a known issue?  A while back, I did have to remove the package network-manager in order to get the static IP to be respected at all.

The two dhcp packages installed are dhcp3-client and dhcp3-common.  The package ubuntu-minimal depends on dhcp3-client.  Is it OK to remove these packages?

---

### Post by LepeKaname on 2009-07-01
Sure, no problem. ubuntu-minimal is just a meta-package, which means it is helpful only if you want to be sure all the packages that are part of ubuntu-minimal are installed. Besides that is useless. 

This issue happened to me once and I have seen this question around sometimes. The problem is that is not easy to detect it.

Uninstalling them will not kill the process, so don't forget to kill them manually (kill -9 PID).

I personally think that those packages should check first if you have a static IP before updating.

---

### Post by mjf on 2009-07-02
Thanks for your help.  This seems to have solved the issue.

---

