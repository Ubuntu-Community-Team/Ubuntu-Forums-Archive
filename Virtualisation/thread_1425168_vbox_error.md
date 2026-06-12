---
title: "vbox error"
date: 2010-03-08
forum: Virtualisation
---

### Post by zvacet on 2010-03-08
I installed vbox-ose and after installed OS on virtual machine I can boot in and work.But after comp restart I always get this message ( see attachment).Only way is to switch user and reinstall package.But that solved problem temporary,because anfter next comp restart I get same meesage.How can I solve this?

---

### Post by Druke on 2010-03-08
have you tried

> sudo /etc/init.d/vboxdrv setup

that may resolve your issue, I was having this problem a while back as well.

---

### Post by zvacet on 2010-03-09
That command didn´t help,so I reinstalled package virtualbox-ose-source and restarted com.It is working now but I´m not convinced this is end of my problems with virtualbox.

---

### Post by Druke on 2010-03-09
let us know if you have further issues!

---

### Post by zvacet on 2010-03-10
It look like it is O.K. now.Tnx!

---

