---
title: "charm build returns unrecognised command"
date: 2017-09-22
forum: Ubuntu Cloud and Juju
---

### Post by deephack on 2017-09-22
Hi all,

I'm trying to learn charm development from the Getting Started with charm development documentation found at [http://jujucharms.com/docs/stable/developer-getting-started](http://jujucharms.com/docs/stable/developer-getting-started) however when I get to the point when it tells me to run charm build I just get an error message stating "ERROR unrecognized command: charm build". I installed juju and charm-tools via the snap packages and have the following versions of each.

juju 2.2.4
charm-tools 2.2

What am I doing wrong?

---

### Post by deephack on 2017-09-25
Okay got to the bottom of this one. It turns out that I had the apt package charm from the standard ubuntu 17.04 repo installed at the same time as the charm snap with the apt package provided one taking precedence. The apt package provides charm-tools 2.2 which appears to be the store client and not the charm tool :-(

Super confusing but I'm glad I worked it out now.

---

