---
title: "Back up remote server"
date: 2010-05-04
forum: Server Platforms
---

### Post by si907 on 2010-05-04
Hi 

I'm new here.

Can you help me please :P need to know how to back up remote server using ubuntu server(via ftp or similar) and is it good (ubuntu) to work with tape storage ???

regards

Simon

---

### Post by si907 on 2010-05-04
i want to back up other dedicated server to be more specific :)

---

### Post by ghost_ryder35 on 2010-05-04
> **si907 said:**
> Hi 

I'm new here.

Can you help me please :P need to know how to back up remote server using ubuntu server(via ftp or similar) and is it good (ubuntu) to work with tape storage ???

regards

Simon

you could rsync the directories you care off of the server, or make tar balls on the server itself and then rsync them off.

or you could install 'bacula' one of my favs
sudo aptitude install bacula

---

### Post by Bob P on 2010-05-05
I've been using scripted RSYNC in cron jobs to perform that kind of remote disk synchronization task for more years than I care to count.   I've just been too lazy to set up a "proper" backup system, just because I'm always to busy to change things.  RSYNC scripts with RSA authenticated passkeys and SSH logons is very reliable.

---

### Post by si907 on 2010-05-05
thx guys will try last option

---

