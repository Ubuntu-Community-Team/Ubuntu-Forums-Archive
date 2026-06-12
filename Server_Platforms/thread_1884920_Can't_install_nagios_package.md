---
title: "Can't install nagios package"
date: 2011-11-22
forum: Server Platforms
---

### Post by dboss101 on 2011-11-22
Hi,

I run a ubuntu 10.04 LTS server, and have a small issue :

when i try to install a certain package :

```
apt-get install nagios-nrpe-server
```It fails with the following error :

```
Do you want to continue [Y/n]? y
E: Internal Error, Could not perform immediate configuration (2) on mountall

```other packages can be installed just fine.

how can i solve it ?

Thanks

---

### Post by jonobr on 2011-11-22
Hey


I am running 10:04 LTS and tried installing the package as a sanity check,  and it worked ok, 
Dumb question but did you try 
```
sudo apt-get update
sudo apt-get upgrade
```
before commencing?

---

### Post by dboss101 on 2011-11-22
Thanks,
I did try to run apt-get update, with the same results.
obviously i understand that the package itself is fine, since i have other servers running it, just cant install it on this one for some reason...

---

### Post by jonobr on 2011-11-22
I found an article [Here]("http://nerdbynature.de/s9y/index.php?/archives/173-Internal-Error,-Could-not-perform-immediate-configuration-2-on-mountall.html") which pointed to [This mountall bug in launchpad]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/504224") for 10.04

It mentions boot problems and spurious errors, which I suppose could be you?

Guy in the first link installed the package manually

---

