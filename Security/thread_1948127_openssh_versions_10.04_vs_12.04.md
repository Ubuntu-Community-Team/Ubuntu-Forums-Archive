---
title: "openssh versions 10.04 vs 12.04"
date: 2012-03-27
forum: Security
---

### Post by Trzone on 2012-03-27
I have a ubuntu 10.04 server which I SSH into, however I have recently tested ubuntu 12.04 and noticed a discrepancy: the 10.04 server runs an outdated openSSH package while 12.04 runs the most current version.

My question: Is the Ubuntu 10.04 LTS server's openSSH vulnerable, or is it patched?

---

### Post by CharlesA on 2012-03-28
It's probably patched.

Check the change log.

[https://launchpad.net/ubuntu/+source/openssh](https://launchpad.net/ubuntu/+source/openssh)

Keep in mind that 10.04 is a LTS and the versions of packages aren't usually the most current versions, but they do receive security updates.

---

### Post by Trzone on 2012-03-28
Thanks I think it is continually patched :)

---

