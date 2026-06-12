---
title: "Cherokee webserver threads problem"
date: 2009-09-01
forum: Server Platforms
---

### Post by and3k on 2009-09-01
Hi all,

I have a vServer with Ubuntu 8.04. I would like to use the cherokee webserver. I tried all version (normal hardy, backports, launchpad) and I always get this error:

```
root@rivendell:~# cherokee
[01/08/2009 12:49:22.390] (critical) server.c:631 - cherokee_thread_new() failed -1
```

Manual compiling with --disable-pthread would "solve" this problem but would like to use the packages from launchpad...

Is there something that I have to install to use pthreads or is it a "kernel feature" (which I couldn't change, since I have a virtual server).

I'm not really familiar with threads, so I don't even know if it's a good idea to enable/disable threads on an 300MB-RAM-vServer ...

Thanks,
Greetings from Vienna,
and3k

---

### Post by and3k on 2009-09-01
I installed it now completely without threads, that's what i did:

```
# emacs /etc/apt/sources.list
added:
deb http://ppa.launchpad.net/cherokee-webserver/ppa/ubuntu hardy main
deb-src http://ppa.launchpad.net/cherokee-webserver/ppa/ubuntu hardy main
# apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EBA7BD49
# apt-get update
# apt-get build-dep cherokee
# cd /usr/local/src/
# apt-get source cherokee
# emacs cherokee-0.99.24/debian/rules
changed configure option ---enable-pthreads to --disable-pthread
# apt-get --build source cherokee
# cd cherokee-0.99.24/
# debi
```Some links which helped:

[LIST]
[*][https://launchpad.net/~cherokee-webserver/+archive/ppa]("https://launchpad.net/%7Echerokee-webserver/+archive/ppa")
[*][https://help.ubuntu.com/community/UpdatingADeb](https://help.ubuntu.com/community/UpdatingADeb)
[*][https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)
[/LIST]
Would be nice if anyone could tell me if that's the right way to do this? :)

UPDATE: debchange -i before building is needed so cherokee is not overwritten by the "original"
UPDATE 2: rrdtool needs to be installed or libcherokee-mod-rrd will not work

Greetings,
and3k

---

