---
title: "Samba requires manual restart to function"
date: 2007-06-15
forum: Server Platforms
---

### Post by vairoj on 2007-06-15
I'm running Ubuntu 6.06 Server. Currently Samba does not function after the server boot up. When trying to access the server share directory from other computers, the following dialog box appears:

```

\\myserver is not accessible
There are currently no logon servers available to service the logon request.

```

However, if I manually restart the daemon (/etc/init.d/samba restart), everything will works fine after that.
Samba daemon has entry in rc.d and from /var/log/samba/log.smbd it does get started.

Could you help me identify what is the cause of the problem and how can I fix it?

---

### Post by Reugen on 2007-06-17
I'd install sysv-rc-conf (aptitude install sysv-rc-conf) and see if it is being kept on at all stages.  It will show which daemons etc are started up and at what stages.  You can change which ones start at what stages by perssing space.  I wouldn't mess around other stuff in it too myuch though, you could really end up screwing up your system.  Anyways i hope this solves your problem

---

### Post by vairoj on 2007-06-18
According to sysv-rc-conf, samba service is run on all level (2-5). I also try the same configuration (same smb.conf file, same installation procedure) in VMware and it works there. However, it does not work with the my server (Dell PowerEdge 750).

Some more background information: There was one other problem with my PowerEdge 750, initially the network does not obtain IP when started, I need to restart networking service in order to get an ip. I fixed that problem by adding "pre-up sleep 5" to /etc/network/interfaces to delay it for 5 sec before trying to obtain an IP and it did solve the problem. Note that this problem does not happen on my VMware setup also. Therefore, I don't know whether these two problems are correlated or not. However, while I fixed the DHCP problem on my Dell server, the samba problem still persist.

---

### Post by Reugen on 2007-06-18
I think your right about the problems being interrelated.  If tehre isn't a network for samba to bind to when it starts up -which would be about the same time networking services start- then it wouldn't connect  to any network/device as far as in know.  so  you probably need to have samba start after networking.  Theres a sleep option in  /etc/init.d/samba i believe.  It should be in the start and restart cases.  It typcially says sleep 1.   you could change this to five or six to get it to start after the networking, adn see if that helps.

---

### Post by vairoj on 2007-07-02
Your hypothesis seems to be right. I fixed the problem by changing the sys-v order to 99 (executed last) and  Samba is started up correctly now.

---

