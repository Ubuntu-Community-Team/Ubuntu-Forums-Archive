---
title: "Upstart or Systemd"
date: 2013-12-21
forum: Ubuntu, Linux and OS Chat
---

### Post by seanmoir99 on 2013-12-21
I just want to know what the ups and downs of both are, post away :)

---

### Post by ian-weisser on 2013-12-21
Both are good.
Both are big improvements over sysvinit.
Both are moderately well documented.
Both development teams have good visions, good leadership, and great talent.
Both dev teams are easy to contact, and quick to respond.
Users won't notice the difference.

Beyond that, I think your question should be tighter.
You are inviting another useless, tedious A vs B flamewar.

---

### Post by sffvba[e0rt on 2013-12-21
> **ian-weisser said:**
> You are inviting another useless, tedious A vs B flamewar.

This is likely with a thread like this... but we are here to monitor the situation and ensure that doesn't happen ;)

---

### Post by grahammechanical on 2013-12-21
Upstart originated with Ubuntu. Systemd did not originate with Ubuntu. That alone is enough reason for some people to spit hate at Ubuntu. Perhaps it is the reason the OP started this thread. In this particular case it seems that Upstart got out of the gate first. It being in Ubuntu 6.10. Whereas, systemd is recorded as being released 30 March 2010. So, who is fragmenting the ecosystem now?

[http://en.wikipedia.org/wiki/Upstart](http://en.wikipedia.org/wiki/Upstart)

[http://en.wikipedia.org/wiki/Systemd](http://en.wikipedia.org/wiki/Systemd)

See this thread on how to bring in Ubuntu not using systemd as a means of negative publicity for Ubuntu.

[http://ubuntuforums.org/showthread.php?t=2194822](http://ubuntuforums.org/showthread.php?t=2194822)

---

### Post by 3rdalbum on 2013-12-21
> **grahammechanical said:**
> Upstart originated with Ubuntu. Systemd did not originate with Ubuntu. That alone is enough reason for some people to spit hate at Ubuntu. Perhaps it is the reason the OP started this thread. In this particular case it seems that Upstart got out of the gate first. It being in Ubuntu 6.10. Whereas, systemd is recorded as being released 30 March 2010. So, who is fragmenting the ecosystem now?

Hi Graham, I've been over that with the OP in another thread, and now I think he really wants to know the differences between Upstart and Systemd. I tried to explain, but the technical workings of Init systems are not my specialty.

---

### Post by ian-weisser on 2013-12-21
> **3rdalbum said:**
> I've been over that with the OP in another thread, and now I think he really wants to know the differences between Upstart and Systemd.

Since we don't know if he's asking about commands, config files, features, signals, etc...he might be better served to read the documentation until he know what he wants to ask. "Tell me the difference" is understandable in someone learning about it, but just way too vague to answer succinctly.

---

### Post by lykwydchykyn on 2013-12-21
Since Debian is currently debating which to use, the debian wiki contains some good "debate pages" detailing the pros and cons of each system.  See:

[https://wiki.debian.org/Debate/initsystem](https://wiki.debian.org/Debate/initsystem)

---

### Post by SantaFe on 2013-12-22
I'm confused, I'm running Xubuntu 13.10 and according to Synaptic, I've got both installed.  Wonder which one's in control? ;)

---

### Post by ian-weisser on 2013-12-22
According to [http://lists.debian.org/debian-devel/2013/05/msg01356.html](http://lists.debian.org/debian-devel/2013/05/msg01356.html) , the systemd package in Ubuntu includes the dbus libraries but not init. So Upstart is in control.

---

