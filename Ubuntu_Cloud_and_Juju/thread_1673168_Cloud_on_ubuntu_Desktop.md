---
title: "Cloud on ubuntu Desktop"
date: 2011-01-22
forum: Ubuntu Cloud and Juju
---

### Post by ashishrevar on 2011-01-22
Hello there,
I am wondering that is it possible to install cloud on ubuntu desktop?
If I have ubuntu desktop edition in my laptop and then using these commands if I install cloud then will it work properly or not?

**sudo apt-get install eucalyptus-cloud**

Installing cloud on a single machine will it make any kind of problem or what? Additionally I am avoiding to install UEC, and usign ubuntu desktop I want to work with cloud.

---

### Post by kim0 on 2011-01-22
Hi!

This is how to install from bare packages [https://help.ubuntu.com/community/UEC/PackageInstall](https://help.ubuntu.com/community/UEC/PackageInstall)

However installing UEC from CD is definitely easier, and results in a more supported configuration. Also, you'd still need at least 2 machines (CLC/CC/SC/Walrus, and NC). There are hacks to install on a single machine, but that would be an unsupported configuration

For the easiest way to play with UEC, try my blog post on running UEC on EC2
[http://foss-boss.blogspot.com/2010/10/cloud-on-cloud-uec-on-ec2.html](http://foss-boss.blogspot.com/2010/10/cloud-on-cloud-uec-on-ec2.html)

Have fun :)

---

