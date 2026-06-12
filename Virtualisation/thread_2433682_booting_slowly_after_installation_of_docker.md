---
title: "booting slowly after installation of docker"
date: 2019-12-23
forum: Virtualisation
---

### Post by blainedeyoung on 2019-12-23
I recently installed ubuntu in a virtualbox on my pc.  Then I installed docker.  Virtualbox ceased working.  So I uninstalled docker, disabled the hypervisor, and did a repair installation of virtualbox.  Now ubuntu works, but it always boots very, very slowly.  I was wondering if anyone has any ideas about how to fix this short of reinstalling.

Thank you for your consideration.

---

### Post by digikin on 2020-01-19
Your attempting to do nested virtualization.  You definitely need to make sure that you have enough resources for consumption when doing this.

---

