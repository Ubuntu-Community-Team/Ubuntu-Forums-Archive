---
title: "Latest update from Canonical breaks 18.04LTS on VMWare"
date: 2019-06-12
forum: Virtualisation
---

### Post by jive2 on 2019-06-12
Latest updates breaks video driver on VMware making images unusable. 

Appears to be limited to Windows 10 with NVidia graphics. My own setup is W10 Enterprise with Quadro M2200 running VMware WS Pro 15. Issue is detailed here [https://superuser.com/questions/1446521/ubuntu-on-vmware-freezes-on-startup](https://superuser.com/questions/1446521/ubuntu-on-vmware-freezes-on-startup)
It also breaks things when using remote desktop to ESXi hosted images. Seems that there is a workaround already [https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1832138](https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1832138). It would be nice to not break things in the first place though.

---

### Post by coffeecat on 2019-06-12
Did you have a question? Were you needing help? This is a forum for support whose membership consists of end-users such as yourself.

---

### Post by jive2 on 2019-06-12
Sorry about not adding the question, it was sort of implicit, how to recover from this. There are at least three ways to go around until somebody comes up with a proper fix. My post was intended to be heads up for any user encountering the same issue and I have a feeling there might be quite many.

And as I state in the bug report comment the workaround presented is not fixing things for me.

---

