---
title: "Migrating an intranet PC from 98se to Ubuntu"
date: 2006-02-27
forum: Server Platforms
---

### Post by DaBruGo on 2006-02-27
HI folks,

I have a simple intranet PC at work (old 98SE machine) that currently has Apache,MySQL,PHP installed and running fairly well on it. Folks from various locations are able to connect to it for company news/info etc.

Here is my question. Can anyone point me to a good HOWTO on getting this similar setup going on a PC running Ubuntu. (I would like to migrate my intranet site over to it.) I am sure there are quite a number of guides out there, but I was wondering if anyone has come across a few that really stand out. 

I have been playing with Ubuntu for a few months now and have been very impressed.

Any information greatly appreciated.


Thanks in advance,
DAVE

---

### Post by colo on 2006-02-27
Well, that's not that much of a hassle, I guess. just install ubuntu on the box (preferably without X11, you won't need it anyway), install apache, mysql, php, openssh and whatever else you might want to have via apt-get, configure the installed services to your needs and add them to the default-runlevel.

Since you#re already running those daemons, I presume you already have a clue about how to set them up (except openssh, which works flawlessly ootb). I suggest you do a full backup of said machine - just in case you happen to f*ck up somehow - and give it a shot :)

---

