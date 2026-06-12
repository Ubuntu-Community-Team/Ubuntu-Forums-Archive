---
title: "Install ajenti"
date: 2013-07-10
forum: Server Platforms
---

### Post by alfirdaous on 2013-07-10
Hello everybody

I tried to install [agenti]("http://www.tecmint.com/install-ajenti-a-web-based-control-panel-for-managing-linux-server/"), but it is given this error:

```

ubuntu:/etc/apt/sources.list.d# apt-get install ajenti
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 ajenti : Depends: python-requests but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

and then:

```

ubuntu:/etc/apt/sources.list.d# apt-get install python-requests
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 python-requests : Depends: python2.6 but it is not installable
                   Depends: python (< 2.7) but 2.7.3-0ubuntu2.2 is to be installed
                   Recommends: python-gevent but it is not going to be installed
                   Recommends: python-oauthlib but it is not installable
E: Unable to correct problems, you have held broken packages.

```

Thanks in advance

---

### Post by alfirdaous on 2013-07-18
is there anybody that have any clou about this?

---

### Post by Mr.Gosh on 2013-11-07
Why is this marked as solved?
The Problem still persists - or does anyone have an idea how to upgrade python-requests (>= 0.12.0) ?

---

