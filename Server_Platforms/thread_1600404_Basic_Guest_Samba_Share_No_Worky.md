---
title: "Basic Guest Samba Share No Worky"
date: 2010-10-18
forum: Server Platforms
---

### Post by Lucky. on 2010-10-18
I've been running Samba for a couple of years now.  Bumped up from 9.04 to 10.10 server (64 bit), and nothing wants to work.  I have a really simple share that I want to be accessible by all Windows clients without a login (guest access).  Here is my config:

```

[global]
security = share

[public]
path = /srv/public
writeable = yes
create mask = 660
directory mask = 770
guest ok = yes

```

For some reason this doesn't work (cannot connect to share).  Used to work great in 9.04, but not in 10.10.  I've tried a ton of tutorials & blog posts, but all of them involve setting up a samba user, not allowing guest access.  Those seem to work, but I'm having problems with this guest access share.  Any ideas?

---

### Post by E-call on 2010-10-19
I may be wrong here, but you may want to change your create mask to 777 to allow all users to change or modify files.
 
My public share settings are set to for the directory mask 2777
 
again i could be wrong but maybe check it out
 
also you may want to pop a 0 in front so it looks like this
 
create mask = 0660
directory mask = 0770

---

### Post by sikander3786 on 2010-10-19
Are you sure, firewall is not causing a problem? Did you reconfigure it after upgrade?

---

### Post by Lucky. on 2010-10-19
My bad.

The "/srv/public" folder had 777 on it while I was testing, but the "/srv" folder had 770 on it.  This was preventing things from working.

Thanks anyway!

---

