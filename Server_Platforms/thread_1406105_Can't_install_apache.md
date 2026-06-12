---
title: "Can't install apache"
date: 2010-02-13
forum: Server Platforms
---

### Post by MicroBoy on 2010-02-13
I have a problem while I want to install Apache, it give me the following error:

> The following packages have unmet dependencies:
  apache2: Depends: apache2-mpm-worker (>= 2.2.11-2ubuntu2) but it is not going to be installed or
                    apache2-mpm-prefork (>= 2.2.11-2ubuntu2) but it is not going to be installed or
                    apache2-mpm-event (>= 2.2.11-2ubuntu2) but it is not going to be installed
E: Broken packages

---

### Post by Satoru-san on 2010-02-13
try this

```
apt-get update
 apt-get upgrade
 apt-get dist-upgrade
dpkg --reconfigure -a


```
If one of those fails try the next one. Maybe do the last one first, been a while since I used ubuntu.

---

### Post by ksudbury on 2012-02-18
For any other users finding this post via Google here is a guide on [install apache ubuntu]("http://techspotting.org/install-apache-ubuntu-all-versions") for all versions.

---

### Post by Iowan on 2012-02-18
Closed:
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

