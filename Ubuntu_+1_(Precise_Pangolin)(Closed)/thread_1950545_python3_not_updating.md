---
title: "python3 not updating"
date: 2012-03-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by lonniehenry on 2012-03-31
I am having a problem with python3 having broken dependancies in my precise with gnome-shell.  I have tried fix broken dependancy in synaptic.  sudo apt-get -f install in terminal and no luck-  I get
 Errors were encountered while processing:
 /var/cache/apt/archives/python3_3.2.3~rc1-2ubuntu1_all.deb
in terminal  
Any ideas as this has been ongoing for about a week. Thanks in advance

---

### Post by scradock on 2012-04-01
> **lonniehenry said:**
> I am having a problem with python3 having broken dependancies in my precise with gnome-shell.  I have tried fix broken dependancy in synaptic.  sudo apt-get -f install in terminal and no luck-  I get
 Errors were encountered while processing:
 /var/cache/apt/archives/python3_3.2.3~rc1-2ubuntu1_all.deb
in terminal  
Any ideas as this has been ongoing for about a week. Thanks in advance
apt-get remove python3 and then apt-get install python3?

---

### Post by lonniehenry on 2012-04-01
tried sudo apt-get remove python3 and got the following:
dpkg: error processing python3 (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 python3

it has resisted other attempts to remove it and I can't update anything else.  Any other suggestions.  I am stumped.

---

### Post by wojox on 2012-04-01
Have you tried this approach [apt-get how to fix very broken packages]("http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/")

---

### Post by lonniehenry on 2012-04-01
I still haven't figured this out.  I must have updated at the wrong time.  Others and myself are ok on other precise installs.  I am thinking of reinstalling, unless there are other ideas out there.

---

