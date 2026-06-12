---
title: "installing nessus"
date: 2008-11-17
forum: Security
---

### Post by ozweego5 on 2008-11-17
I have got nessus installed and registered throu their site but when i got to start the deamon i get this

sudo /etc/init.d/nessusd start
Restarting Nessus daemon: nessus-libraries/libnessus/store.c: /var/lib/nessus/plugins/redhat-RHSA-2008-0957.nasl has a too long description (4396)
redhat-RHSA-2008-0957.nasl failed to load


anyone have anything to help me out??
sorry if i posted in the wrong area

---

### Post by Titan8990 on 2008-11-17
It looks like you installed the Red Hat version. Did they have .deb or .tar.gz?


Edit: Just checked and they do have .deb for Ubuntu 7.10 and 8.04. If that is not the package that you got then I would go back and download it.

---

### Post by Sarmacid on 2008-11-18
I agree with Titan8990, seems you installed the Red Hat version. To install Nessus, you can just grab it from the repos```
apt-get install nessusd
```

---

### Post by croniksoft on 2008-11-19
Don't forget the client
and to start the demon all you need to do is run  "sudo nessusd"

FYI-
you will need to setup login information on the demon side 
ex: user , password and type of account.

---

