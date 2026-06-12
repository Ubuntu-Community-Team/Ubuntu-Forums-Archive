---
title: "scalix groupware solution"
date: 2006-10-24
forum: Server Platforms
---

### Post by Mayk on 2006-10-24
Hi all,

I've become a big fan of ubuntu, and am running 2 ubuntu servers now. One of them needs to be prepped with a good strong mail/groupware solution.
My interests have been going out to scalix ([www.scalix.com)](www.scalix.com)), that provide a cool solution , opensourcing all their stuff, and have evolution connectors (yihaaaaa), and even provide free outlook connectors for the windows users among us. Great product, with lot's of development put into it (15 years of hp openmail..)..

Now comes the tricky part.. It's not supported on ubuntu. There is a comminity raw edition that you can hack into your ubuntu. And, best of all, it works. But recently there are new versions coming out, and it doesn't work that well anymore. Support for ubuntu/debian is not exactly planned as far as scalix support could tell me (awsome support, even for the community edition, and last night florian even ssh-ed into my box to fix a problem !!)..

So as you can tell, i'm excited about this product, but am kinda reserved on implementing it.

Anyone experience with this ? Or maybe some ubuntu plans on having this superb package in aptitude ?

Kind regards,

Mayk

---

### Post by parhed on 2006-10-25
I'm shure there will be a makefile for version 11 to?! Florian posted this regarding CLI install and Ubuntu on 10/4:
[http://www.scalix.com/community/viewtopic.php?p=18672](http://www.scalix.com/community/viewtopic.php?p=18672)
Cheers
Par

---

### Post by Mayk on 2006-10-25
Hi,

thanx for the reply. I'm aware of the cli install. I've taken the make file for version 11 alfa from the wiki, and bashed it around to work for the beta 1 but it's not neat coding anymore in that file. some more experienced users will have more luck on this i think.

So it's definately possible on getting it on ubuntu, but it's a bumpy road to get there, and that gives me some bad vibez. Like its running now at the moment, but without anything changing it stopped receiving emails for some strange reason, all services running and all seems fine. no clue in the logs.. 

i'm gonna reinstall to try and get the makefile a little more perfect so i can publish it.

But more thoughts on this by other ppl using it would be greatly appreciated..

gr

Mayk

---

### Post by santo on 2006-11-01
I'd love to see a solution for this as well.
Currently I run Scalix inside a vmware (vmware server) because it doesn't install (well) on my ubuntu system.

Getting rid of this vmware stuff would be just wonderfull :cool: 
(no offense to vmware, but just running a vmware server to get my mailserver running is a bit overkill in my opinion)

---

### Post by djdicbob on 2006-11-11
My expierence with scalix is a headache. The community edition install is unpredictible. My collaboration with the writer of the makefile from the scalix wiki has yeilded some answers.  Seems to me the ldap configuration doesn't always setup authentication properly.  I beleive with the support of ubuntu they could smack a big homerun of distribution of scalix.

If you have the dollars for an enterprise licsence Scalix is great choice for group ware.  Its ability to deliever a webapp that looks and feels like outlook is great.Not to mention their outlook connector is great.


In short..scalix is not for the weak hearted.  Ubuntu getting involved would put some real pressure on novell and openxchange!

---

### Post by elst on 2006-11-12
There are currently plans to offer directory services with a future release of Ubuntu Server, and third-party vendors should be able to integrate their products into the provided LDAP/Kerberos facilities.

This was discussed at the recent UDS and the work itself is only just starting. Anybody interested in contributing is welcome to join the ubuntu-directory mailing list or visit the #ubuntu-directory IRC channel.

---

### Post by reya276 on 2007-06-15
Is there a .deb package for this software, because I tried installing .tar download and could not get it done since I'm a newbie to Ubuntu/linux any help would be appreciated. Thanks!:D

---

