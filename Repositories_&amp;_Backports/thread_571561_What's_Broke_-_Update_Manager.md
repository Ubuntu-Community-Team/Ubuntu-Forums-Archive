---
title: "What's Broke - Update Manager"
date: 2007-10-09
forum: Repositories &amp; Backports
---

### Post by dhoffman on 2007-10-09
Update Manager, Add/Remove , and the Synaptic Package Manager are unable to down load from the Repositories. I have redone the sources.list and have run sudo apt-get update several times and get the same errors.  Connections fail in all attempts.  I have done what the other posts have suggested but the same errors occur - "Connection failed" .

The strange thing is that I can open Firefox, type in the URL and connect to the repos.  So what is broke.  If I can connect from Firefox on the same box, why won't the other programs connect? 

I am running dapper with gnome desktop.  Any help would be appreciated.
Thanks in advance

---

### Post by dhoffman on 2007-10-09
Figured out the problem. Was not a problem with Ubuntu.  We have a Sonicwall firewall and it downloaded new Intrusion Prevention signatures and was blocking HTTP Proxy Access 2 traffic which evidently Ubuntu uses to connect to the repos. Unblocked that and everything works again.

Hopefully this will help someone else if they are having problems.

---

