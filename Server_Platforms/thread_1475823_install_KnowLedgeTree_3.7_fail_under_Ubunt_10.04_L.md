---
title: "install KnowLedgeTree 3.7 fail under Ubunt 10.04 LTS. Zend Server problems"
date: 2010-05-07
forum: Server Platforms
---

### Post by giuliano1969 on 2010-05-07
We are using currently Knowledgetree 3.7 on ubuntu 9.10, without problems.

Today, we have tried to install knowledgetree 3.7 on a new machine, with a brand new ubuntu 10.04.

The installer fails, claiming for multiple errors.

Basically,

      the installer couldn't find the php-5.2-fileinfo-zend-server and php-5.2-xmlrpc-zend-server
      the zend-server package seems to be damaged


I enclose also a list of active repository.



-------------------------
Alcuni pacchetti non possono essere installati. Questo può voler dire
che è stata richiesta una situazione impossibile oppure, se si sta
usando una distribuzione in sviluppo, che alcuni pacchetti richiesti
non sono ancora stati creati o sono stati rimossi da Incoming.
Le seguenti informazioni possono aiutare a risolvere la situazione:

I seguenti pacchetti hanno dipendenze non soddisfatte:
knowledgetree-ce: Dipende: php-5.2-fileinfo-zend-server ma non sta per essere installato
Dipende: php-5.2-xmlrpc-zend-server ma non sta per essere installato
Dipende: zend-server
E: Pacchetto danneggiato

Installation was not completed. See output above for detailed error information.

---

### Post by FordTaunus on 2010-05-31
Hi,

I wanted to try out knowledgetree as well and got stuck at the same problem. :(

Are there any solutions yet? Do we expect an install package for Lucid Lynx? Can I fix it manually?

Actually this makes me wonder whether knowledgetree is worth a try.:confused:

Regards,

Ford

---

### Post by giuliano1969 on 2010-05-31
you can fix the problem MANUALLY
Download the lib mysqlclient15 from karmic repository (yes, from karmic also if you have the Lucid 10.04)

install it manually wit deb packager.

The zend package does require it, and can't install without. 
Installing the myslqclient  lib, KT 3.7  will install flawlessly on Ubuntu 10.04

BR

---

### Post by zhangr on 2010-06-01
We also met some problem on downloading packages. Then I found it just name resolving problem, add following to your /etc/hosts: 
```
66.114.50.48    repos.zend.com
```Hope it also works for you.:)

---

### Post by giuliano1969 on 2010-06-01
it is NOT a dns problem, it is a package dependencies problem

Eve more, the ip you gave seems not related to zend

[http://www.domaintools.com/reverse-ip/](http://www.domaintools.com/reverse-ip/)

---

### Post by zhangr on 2010-06-01
> **giuliano1969 said:**
> it is NOT a dns problem, it is a package dependencies problem

Eve more, the ip you gave seems not related to zend

[http://www.domaintools.com/reverse-ip/](http://www.domaintools.com/reverse-ip/)

Sorry for I only understand English, so I've to guess your problem via replies.
I've installed KnowledgeTree when Lucid is in Beta2, repos.zend.com is a pool, it has multiple servers inside. And I found wget can not download packages from the pool normally, then I add this line to avoid this problem. This one is the one working for me.  If you do a query to this ip address and to repos.zend.com, you'll find they are in same sub domain:
```
ubuntu@Simon:~$ host repos.zend.com
repos.zend.com is an alias for g1.panthercdn.com.
g1.panthercdn.com has address 66.114.51.84
ubuntu@Simon:~$ host 66.114.50.48
48.50.114.66.in-addr.arpa domain name pointer lax-am6-n12.panthercdn.com.
ubuntu@Simon:~$
```

---

### Post by FordTaunus on 2010-06-24
Here's a detailed explanation of and solution for this problem:

[http://forums.knowledgetree.org/viewtopic.php?f=6&t=20500](http://forums.knowledgetree.org/viewtopic.php?f=6&t=20500)

---

