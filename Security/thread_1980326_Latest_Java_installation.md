---
title: "Latest Java installation"
date: 2012-05-15
forum: Security
---

### Post by OpenSourceRules on 2012-05-15
On the first time I tried OpenJRE 7, I got the "latest version" of java for a few days.
Then, it becomes obsolete when Java update 7.4 was out, but uninstalling OpenJRE and IcedTea will get you back to OpenJRE 6.0, which is even more dated.
That's what I did:

sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer

This at least solve the problem of older Java for the moment.  Afterward, it is better to uninstall OpenJRE just to avoid potential conflicts.

---

### Post by woxuxow on 2012-05-15
openJRE or openJDK

don`t forget why we use GNU 
openjdk is open source and free

---

### Post by OpenSourceRules on 2012-05-15
> **MustafaJF said:**
> openJRE or openJDK

don`t forget why we use GNU 
openjdk is open source and free

The unfortunate fact is that OpenJDK often lags behind in development, and occasionally we need the last java to run things.

---

