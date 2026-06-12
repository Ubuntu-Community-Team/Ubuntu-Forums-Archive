---
title: "&quot;Migrating&quot; Ubuntu Server 8.04"
date: 2009-05-09
forum: Server Platforms
---

### Post by tinker312 on 2009-05-09
Hi all, 

I became interested in Linux around 2001-2002 and ever since then I've been hooked. Back then, the "right-brain" Linux OS was Mandrake (they totally sold out now.) Post slackware, I had to try out Slackware and OpenBSD. Anyways, I'll get to my question.

I assume configuration for all linux systems are located in the /etc directory. I am running Ubuntu 8.04 server, with the default lamp install, on an old desktop. This setup is mostly for educational, hobbyist, pre-professional experience purposes. My question is, can I just simply copy the /etc directory and paste it into a new installation on a different computer, with the same OS? I understand new features or bugs are patched in new releases, but isn't the config file the same?  

I guess what I'm really asking is how do I replicate a working setup to another machine?

---

### Post by cariboo on 2009-05-09
Personally I'd only backup the configuration files for the services I use. There are other services that have changed and just copying all of /etc might run into problems.

---

### Post by tinker312 on 2009-05-09
that makes sense

---

### Post by juancarlospaco on 2009-05-09
ETCKeeper package...

---

### Post by windependence on 2009-05-09
You'll get away with this IF you use exactly the same version. You may want to move your /home directory as well. Using different versions, you may get unpredictable results.

BTW, what was wrong with BSD? I find it much more simple and stable than Linux.

-Tim

---

