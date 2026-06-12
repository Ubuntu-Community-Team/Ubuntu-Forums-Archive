---
title: "Request: Gftp with SSL!"
date: 2005-05-06
forum: Ubuntu Backports
---

### Post by angrylittleman on 2005-05-06
Hello
I would like to know if it is possible to added Gftp with SSL encryption.  It seems as though the version in ubunut repositories don't have ssl complied in with it.  I would like to be able to use ssl with my vsftpd server!  Thanks.

ALM

---

### Post by blueplazma on 2005-05-06
If that support is available, you could compile it yourself through apt-get source or, you could use an sftp connection if that's feasible.

---

### Post by Axios on 2005-11-09
[QUOTE=angrylittleman]Hello
I would like to know if it is possible to added Gftp with SSL encryption.  It seems as though the version in ubunut repositories don't have ssl complied in with it.  I would like to be able to use ssl with my vsftpd server!  Thanks.

ALM[/QUOTE]


I also need this.

---

### Post by jdong on 2005-11-09
We cannot modify the functionality of Gftp... Either compile it yourself with desired options, or try to influence Ubuntu developers to make that change in Dapper so we can backport it.

---

### Post by loeppel on 2006-03-06
I know this post is a bit old.
But as its the first google result, if you search "gftp ssl ubuntu", I will solve the problem ;)

Look here: 

**[http://users.lichtsnel.nl/~seveas/dists/breezy-seveas/custom/](http://users.lichtsnel.nl/~seveas/dists/breezy-seveas/custom/)**

Great Repositroy!!

greets
loeppel

---

### Post by konungursvia on 2007-01-10
Well gftp with ssl seems impossible at best. What I did, and it works, is this: 

I installed Wine, then got WinSCP from the web, and installed it. Success with ssl connection and transfer to my server.

---

