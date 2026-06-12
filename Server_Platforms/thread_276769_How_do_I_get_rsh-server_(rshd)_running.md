---
title: "How do I get rsh-server (rshd) running?"
date: 2006-10-13
forum: Server Platforms
---

### Post by spiderman59 on 2006-10-13
It does not seem like rshd, the rsh server is running on my
system.  I entered the following command, "sudo apt-get install rsh-server".  I have the /etc/hosts.equiv and /$HOME/.rhosts
files set-up properly.  I have done this before on Redhat V9
with no problem.  However, I see no rshd files (except in.rshd)
on my system and the ps command does not show rshd running.
Also, under System/Administration/Services, I don't see rshd as
a listed service.

To test the server, I'm using a command as follows:
>rsh  hostname(of localhost) 'ls -l'
but I always get the message:  rsh: could not make a connection.

Which means the local rsh client could not connect to the local
rsh server.

Any help would be appreciated.

---

### Post by Asher Glaun on 2007-03-29
Similar problem with Kubuntu edgy. tried everything.  Installed rsh-redone-server (with ssh installed and uninstalled) ... added hosts to /etc/host.equiv and chmod 644 this file. Added hosts to /root/.rhosts and chmod 644.  Added start up lines to xinetd.conf and restarted service. Nothing.

Installed inetd, added lines to inet.conf, restarted service. From any remote machine ..
`rsh server ls` gives .. Connection refused.

Need this to run clients from an old Wyse dumb term. Worked on my old Mandrake server

---

### Post by Mr. C. on 2007-03-29
Several things need to be in place:

1) in.rshd installed
2) portmap running and enabled
3) inetd / xinetd entries enabled and inetd service reloaded

Although geared towards Redhat, review the Lab work for Week6 "Networking Basics" :

[http://cis68c1.mikecappella.com/calendar.php](http://cis68c1.mikecappella.com/calendar.php)

MrC

---

