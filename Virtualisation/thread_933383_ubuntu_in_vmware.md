---
title: "ubuntu in vmware"
date: 2008-09-29
forum: Virtualisation
---

### Post by gangwan on 2008-09-29
how to connect internet using ubuntu in vmware....?

---

### Post by jigsaws on 2008-09-29
Configure NAT interface in vmvare and then it should work out of the box.

---

### Post by darco on 2008-09-29
Just go to Settings for the Ubuntu Guest...You need to setup the network in vmware to either use Bridge Network which VMWare will assign its on IP to the Guest,  or NAT which will piggy-back off the Host IP....


good luck

darco

---

### Post by bodhi.zazen on 2008-09-29
If you are having problems we need more information ...

Host OS ?
Version of VMWare ? Server ? Player ? Workstation ????
Hardware ? Wired or wireless ??

Version of Ubuntu.

Are you using NAT or Bridged connection ?

---

### Post by gangwan on 2008-09-29
how to configure nat... sorry... i'm beginner

---

### Post by bodhi.zazen on 2008-09-29
> **gangwan said:**
> how to configure nat... sorry... i'm beginner

When you install VMWare it asks you to configure your network settings, it asks if you wish to configure a NAT interface and / or a bridged interface.

It should work out of the box, if it does not, do you have a firewall ?

---

