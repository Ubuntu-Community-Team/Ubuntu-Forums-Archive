---
title: "service in init.d not starting on boot"
date: 2012-06-29
forum: Server Platforms
---

### Post by manokaran on 2012-06-29
Hi,

Am trying to get a service (couchdb-lucene) in init.d start on boot up but it is not working. 

I installed the service using update-rc.d couchdb-lucene defaults and it installed without errors. In fact when I do a 'service couchdb-lucene start' later it is starting up properly. But it does not start during the boot process. I also tried to run 'service couchdb-lucene start' in rc.local. Even that will not work.

I echoed some messages into a file from inside the couchdb-lucene script and noticed that the 'case' of $1 is 'stop'. So, instead of a 'start' argument, its receiving a 'stop argument!!

I also checked boot.log and in it I see couchdb being started, next nginx is started but after that I see "* Stopping System V runlevel compatibilityESC[164G[ OK ]" and no mention of couchdb-lucene. 

What am I doing wrong?!! 

UPDATE: I forgot to mention that the couchdb-lucene executable is in my home dir!! Do not know if it matters. But the fact that service couchdb-lucene start works makes me think it matters!

UPDATE2: That really was the issue. Moved couchdb-lucene dir to /opt and changed the script in init.d accordingly and now it works. 

Thanks in advance,
mano

---

