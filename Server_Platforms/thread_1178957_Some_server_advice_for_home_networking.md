---
title: "Some server advice for home networking"
date: 2009-06-05
forum: Server Platforms
---

### Post by styleruk on 2009-06-05
I'm using ubuntu 64bit desktop on my pc that is left on all the time.  I have a few pcs in my house such...

Mine
Ubuntu 64bit desktop 8.10

Son's
PC: Ubuntu 32bit 8.10
Laptop: Vista

Daughter's
PC: Ubuntu 32bit 8.10
Laptop: Vista

Wife's
Laptop: Ubuntu 32bit 8.10


What I want to do is upgrade to 9.10 64bit server and turn the every user into a proper...log in and share network environment:

- Ability to have login account held on my pc (which is permantly on)
- Ability for me to control their internet access.
- Ability for them to use my printer etc... 
(having problems with that at the moment)
- I have an external drive that stores all shared docs that I would like them all to use as a central storage area for docs etc..

Now I posted this the other day and I think it got deleted, maybe it's because if I read everything here I would find out most.  What I'm actually after is some helpful advice on how to go about doing this before I make the jump.  On my PC I use and would still want to use:

Wine; for games mainly
Vmware; XP, for CAD, Adobe CS3
Sun virtualpc: XP mainly to sync my iPhone, but would like to use this instead of vmware.

Can anyone throw me some helpful advice?

Regards
Simon

---

### Post by Iowan on 2009-06-05
Although you can use a server as a workstation, it seems best to let a server be a server.  The server, by default, comes with only CLI - although this can be changed.  You can also install the server components you need to a desktop install.

---

### Post by cariboo on 2009-06-06
> - Ability to have login account held on my pc (which is permantly on)

You will need to install Samba, I suggest using [Samba3 by example]("http://www.samba.org/samba/docs/Samba3-ByExample.pdf") to set up samba

> - Ability for me to control their internet access.

You will need to setup dansgaurdian, it is in the repositories

> - Ability for them to use my printer etc... 

Use either samba or cups, cups is probably easier to setup, as all you have to do is access the cups web interface and click a checkbox, see screenshot.
to access the cups web interface in Firefox's url bar type:

```
http://localhost:631
```

> - I have an external drive that stores all shared docs that I would like them all to use as a central storage area for docs etc..

again you will need samba for what you need.

If you still plan on using your desktop as you stated, just install the services you need instead of installing the server version, then installing everything else you need.

---

### Post by styleruk on 2009-06-08
OK, I'll give the above a go and stick with desktop 64bit.  I'm assuming a clean install to upgrade from 8.10 to 9.04 would be best suited as opposed to just an upgrade.

Si

---

### Post by Bucky Ball on 2009-06-08
Just wondering ... why do you want to upgrade?

---

### Post by styleruk on 2009-06-08
A damned fine question.  I wanted to have the latest, that's all.  I suppose I could try out the server additions on what I have not, but I will always want to have the latest.

Si

---

