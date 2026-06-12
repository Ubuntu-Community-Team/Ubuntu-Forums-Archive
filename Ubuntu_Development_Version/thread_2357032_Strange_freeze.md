---
title: "Strange freeze"
date: 2017-03-29
forum: Ubuntu Development Version
---

### Post by wgarcia on 2017-03-29
During these last two days I got a very strange freeze in Ubuntu 17.04.

First I noticed Firefox was frozen. I can kill it , but not reopen it, it tells me there is still an instance running. "killall firefox" tells me the contrary. "ps -ef" shows me some lines and stops, and I can't kill it with control-c, I have to kill the terminal where I opened it. Next I notice there are other applications that are not responding. If I tell the system to reboot, it just does nothing. I have to hard reboot the system, and when it is back, everything seems fine. This has happened twice during the last two days, but with 24 hours in between the two incidences. 

The only crash I noticed was because in one of these two occasions I was upgrading some packages with update-manager, and it did not complete. When I killed it, it generated the crash reported in this bug report:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1209219](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1209219)

Anybody else has seen something similar?

---

### Post by dino99 on 2017-03-29
Logs might help you to find something not expected. If the browser has to be blamed, then pay attention to the addons, maybe one is faulty. Finally check for malicious file, deactivate javascript and run tools to clean the system (gtkorphan / bleachbit (as root but carefully)).
But you does not tell us which flavor/version you are using.

---

### Post by wgarcia on 2017-03-29
Thanks dino99, as my prefix says, I'm using default Ubuntu, that is Unity.

I think the freeze is more general than just Firefox, unless Firefox is able to put the rest of the system down. Otherwise I would kill Firefox and everything else should be normal. 

In any case if I'm the only one experiencing this I will have to look at something specific in my system causing it.

---

### Post by wgarcia on 2017-03-30
I got again these freezes, and opened a bug report against the kernel:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1677491](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1677491)

but I'm quite lost if this is the kernel or what.

I also noticed that I'm getting zillions of messages in my syslog, always this line:

```
Mar 30 10:22:08 walter systemd-resolved[1947]: Using degraded feature set (UDP) for DNS server 127.0.1.1.
```

---

### Post by dino99 on 2017-03-30
i you think that the kernel cause that issue, then boot with an older kernel to find the faulty one; (the kernel team will ask to test this case)

about systemd-resolved message, its a common one found on all systems i think

---

### Post by wgarcia on 2017-03-30
Overall I'm getting strange behavior for DNS resolving. The typical behavior I get is that when log in after rebooting, I have no Internet connectivity. After a while, say 3 or 4 minutes, I get connectivity to all but subdomains of Google (I can access [www.google.com](www.google.com) but not mail.google.com for instance), I don't know if this is for all subdomains or only for Google. Then after 10 to 15 minutes I get also access to subdomains in Google. 

I have a very standard network configuration, with only network-manager managing the network, nothing else.

---

### Post by dino99 on 2017-03-30
i suppose journalctl might help you finding warning/error about DNS. Is it a wired network ? Have you some custom network/proxy/ufw rules ? If the install was made long ago, then rolling distro upgrades, think to do a deep cleaning or a fresh install.

journalct | grep network

---

### Post by wgarcia on 2017-03-30
Yes, it's wired, and yes, I like rolling the distro and trying to solve issues before reinstalling. I read a couple of bugs about the use of systemd-resolved, since Ubuntu 16.10 actually, that may cause the behavior I observe.

Thanks, dino99.

---

### Post by wgarcia on 2017-04-05
On the system freeze, I'm getting it with the current zesty 64bit kernel:

4.10.0-14-generic

I don't get it with 4.10.0-13-generic or the current upstream 4.11.0-041100rc5-generic. I've reported this in this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1677491](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1677491)

---

