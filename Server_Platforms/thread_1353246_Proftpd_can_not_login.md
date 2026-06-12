---
title: "Proftpd can not login"
date: 2009-12-12
forum: Server Platforms
---

### Post by daddysmonsters on 2009-12-12
I have some issues with my proftpd server. I am not running it as standalone as I would rather start the service only for needed ftp sessions. I navigate to /etc and run init.d/proftpd start and get no errors. Then I open filezilla locally and attempt to connect to my server (server is vps running ubuntu 8.06 ) I am attempting to use the username of root and the root pwd. I get a connection so I know the service is running but it gives me a 530 login incorrect. I believe I need to edit groups and users but am leery of diving in without some guidance. Any one care to give a budding admin a hand?

---

### Post by JonRohan on 2009-12-12
IIRC root cannot login by default on Proftpd. Try another user.

---

### Post by daddysmonsters on 2009-12-13
Not by default no, but I thought that I had it enabled, I reverted back to defaults and attempted a different user on the system and still can not login. Same errors, I think this is something with groups but I'm in need of some guidance before I wreck my permissions scheme.

EDIT: friggin server, Nevermind guys the issue was not with the username at all. I tried logging in with the domain before having is setup properly, needless to say it was trying to log in to my second server (dns hasn't changed or anything yet) i used the ip of the correct server and presto im in. thanks.

---

