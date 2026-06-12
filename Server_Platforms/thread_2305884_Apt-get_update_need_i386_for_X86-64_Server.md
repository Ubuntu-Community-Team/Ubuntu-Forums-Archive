---
title: "Apt-get update need i386 for X86-64 Server"
date: 2015-12-10
forum: Server Platforms
---

### Post by Nicolas_Devouge on 2015-12-10
Bonjour,


I am trying to set up a local mirror for our organization, I installed Ubuntu 14.04 server 64bit for it. I have synchronized my mirror that is up to date.

 On a server, I changed the deposits url to use my mirror, and here is the result:

```
W: Impossible de récupérer [https://mirrors.local/ubuntu/dists/trus … 6/Packages]("https://mirrors.local/ubuntu/dists/trusty-updates/multiverse/binary-i386/Packages")  HttpError404

E: Le téléchargement de quelques fichiers d'index a échoué, ils ont été ignorés, ou les anciens ont été utilisés à la place.

```

Here are some information on the server wich want to use the local repo :

```
root@watch-02:~# uname -a
Linux watch-02 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

root@watch-02:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:        14.04
Codename:       trusty

```

 
 
 My client is in x86_64, the mirror has these packages there, and yet he asks the binary-i386!

 Do you have information on this? I found nothing about this problem :(




Merci !

---

### Post by matt_symes on 2015-12-10
Hi

> I am trying to set up a local mirror for our organization, I installed Ubuntu 14.04 server 64bit for it. I have synchronized my mirror that is up to date.

What software are you using to mirror the repositories ?  apt-mirror ?

Kind regards

---

