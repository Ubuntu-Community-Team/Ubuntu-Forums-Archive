---
title: "Unable to Install JUJU, Which guide to follow"
date: 2014-08-25
forum: Ubuntu Cloud and Juju
---

### Post by atifzia.81 on 2014-08-25
I have 2 machines i7 and Xeon 8GB ram each. Xeon working as a node and I can access that node from my controller through ssh everything seems fine. I am trying to install juju on these two machines but I don't know which following guide is written properly?

Install 1
[http://askubuntu.com/questions/65359/how-do-i-configure-juju-for-local-usage](http://askubuntu.com/questions/65359/how-do-i-configure-juju-for-local-usage)
 
Install 2
[http://people.canonical.com/~gavin/maas/building-packages/juju-quick-start.html](http://people.canonical.com/~gavin/maas/building-packages/juju-quick-start.html)

Install 3
[https://wiki.edubuntu.org/SecurityTeam/TestingMAAS](https://wiki.edubuntu.org/SecurityTeam/TestingMAAS)

Every guide is very poorly writen including above so I don't know must I need to edit ~/.*juju*/environments.*yaml *or not and what must I write in admin-secret: '<any-arbitrary-string>' because I tried my local root password and MAAS root admin password and still cluster unable to find environment.

Which guide to follow?

---

### Post by peterwilson-69 on 2014-10-09
What's worse is official MAAS documentation says one thing about installing JUJU, but the official JUJU documentation says something slightly different - its hard to know which guide to follow, especially when things go wrong because then it appears that both guides are wrong and then we hit the forums looking for guidance on poorly tested documentation. It's times like this I remember this software is free, and thus you get what you pay for. I'm not complaining, just realistic.

---

