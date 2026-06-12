---
title: "sabnzbd problem Unbuntu 10.10"
date: 2011-04-27
forum: Server Platforms
---

### Post by idny on 2011-04-27
Hello,
I've been stuck with this for a few days now and thought it was time to open a thread.

I have set up sabnzbdplus on Ubuntu Server 10.10 using the following guide:
[http://wiki.sabnzbd.org/install-ubuntu-repo](http://wiki.sabnzbd.org/install-ubuntu-repo)

When I type 
```
sabnzbdplus
```

it read out the below and stays like this.

I have edited the file in /etc/default/sabnzbdplus to read HOST=0.0.0.0 and the Port 8090
and the user has been set to myself.

If i try and load sabnzbd with either links or w3m i get
```
Error Loading http://192.168.2.24:8090/sabnzbd/ 
Connection Refused.
```

Im guessing i missed some configuration?
Any help is much appreciated.

---

### Post by idny on 2011-05-03
Hi,
Any help? :)

---

### Post by djcla on 2011-05-04
on a fresh server install see the following sites for guidence

[http://forums.sabnzbd.org/index.php?topic=387.0](http://forums.sabnzbd.org/index.php?topic=387.0)

then run sudo nano etc/default/sabnzbdplus
port host and user need to be set as per

[http://www.usenetshack.com/install-setup-sabnzbd-plus-ubuntu-karmic-koala-jaunty-jackalope/](http://www.usenetshack.com/install-setup-sabnzbd-plus-ubuntu-karmic-koala-jaunty-jackalope/)

---

