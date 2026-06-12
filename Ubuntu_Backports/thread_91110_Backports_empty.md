---
title: "Backports empty?"
date: 2005-11-16
forum: Ubuntu Backports
---

### Post by shidai.liu on 2005-11-16
I donwload the package list of breezy-backports. It's empty. Weird?

---

### Post by Kyral on 2005-11-16
From which mirror?

---

### Post by shidai.liu on 2005-11-16
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse

Any suggestion?

---

### Post by Kyral on 2005-11-16
Hmm that IS odd..

I know Backports are out...maybe its just taking a long time to spread out to the mirror system

For the time being set that line to 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse

---

### Post by shidai.liu on 2005-11-16
Thanks, mate.

Unfortunately, there's no emacs-snapshot? Do you know where can I get it for breezy? The one in dapper will remove a lot of packages to install. Thanks.

---

### Post by Kyral on 2005-11-16
Unfortunately it doesn't appear to have been Backported yet...

Sorry

---

### Post by ubuntu_demon on 2005-11-16
the backports are open but there aren't any packages available because some server guy hasn't gottten back from UBZ yet. I hope they don't do this with Dapper. (so it's not the fault of jdong or his team)

---

### Post by shidai.liu on 2005-11-16
Ok I see.

I'll just wait a couple of days.

---

### Post by Kuolio on 2005-11-18
It's just plain silly to have "backports open" when theres nothing there actualy ported. Maybe bp's shouldn't been opened before there actualy is something there? It took me a while to realize that it's bp-repos that are empty, and that eveything is OK with my system. And it made me bit mad, there should be, at the very least, a NOTICE that clearly states "BP-repos are currently EMPTY".

---

### Post by ubuntu_demon on 2005-11-18
[QUOTE=Kuolio]It's just plain silly to have "backports open" when theres nothing there actualy ported. Maybe bp's shouldn't been opened before there actualy is something there? It took me a while to realize that it's bp-repos that are empty, and that eveything is OK with my system. And it made me bit mad, there should be, at the very least, a NOTICE that clearly states "BP-repos are currently EMPTY".[/QUOTE]
It's not the fault of the backport team. 

And if you are like me helping people around you with Ubuntu it can be frustrating to constantly have to change the sources.list ... I rather have a good one and wait.

---

### Post by shidai.liu on 2005-11-18
[QUOTE=ubuntu_demon]the backports are open but there aren't any packages available because some server guy hasn't gottten back from UBZ yet. I hope they don't do this with Dapper. (so it's not the fault of jdong or his team)[/QUOTE]


Any backup server?

---

### Post by AgenT on 2005-11-18
[quote=shidai.liu]Any backup server?[/quote]

Although this may be wrong, there is only one backports server. Then there are mirrors. What you are doing is thinking that the mirrors are somehow different from the main backports, when all they are are just copies of the main backports server. If the main backports server is empty, so are the mirrors.

---

### Post by gapplewagen on 2005-11-19
Is there any estimation of when they'll be available?  I'm still showing them as empty.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse

---

### Post by veloct on 2005-11-20
Still empty

---

### Post by joepotter on 2005-11-20
[QUOTE=veloct]Still empty[/QUOTE]


I get a "bad sig" error here. 


Perhaps the "supper stable" Dapper will work a bit better one of these days.

---

### Post by gapplewagen on 2005-11-20
I don't get any errors... they're just empty.  What are your sources?

---

### Post by joepotter on 2005-11-21
[QUOTE=gapplewagen]I don't get any errors... they're just empty.  What are your sources?[/QUOTE]


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse

---

### Post by lhtown on 2005-11-21
[QUOTE=joepotter]I get a "bad sig" error here. 


Perhaps the "supper stable" Dapper will work a bit better one of these days.[/QUOTE]

I keep getting the bad sig error too whenever I add the main backport repository. All of the other repos work fine most of the time.

---

### Post by haocheng on 2005-11-22
[QUOTE=veloct]Still empty[/QUOTE]

Hurray! I got something to upgrade this morning :smile:

---

### Post by jdong on 2005-11-22
archive.ubuntu.com has received many many backports now.

---

### Post by gapplewagen on 2005-11-22
so happy now!

---

