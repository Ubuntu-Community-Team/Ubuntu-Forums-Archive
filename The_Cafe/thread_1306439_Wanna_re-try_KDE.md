---
title: "Wanna re-try KDE"
date: 2009-10-30
forum: The Cafe
---

### Post by TheNessus on 2009-10-30
But I want to install it without all the K clutter... all those endless useless bloateware programs that come with Kubuntu. So how do I get KDE on Ubuntu cleanly without making it Kubuntu? Coz once I installed KDE and even in Ubuntu I still got left with all those hundreds of useless K programs cluttering my menus and running in the background.

spanks, sorry I didn't find a useful existing thread.

---

### Post by praveesh on 2009-10-30
You can install kde-minimal package . Or kde-standard or kde-full packages according to your requirements  

Cheers

---

### Post by hoppipolla on 2009-10-30
what he said :)

---

### Post by TheNessus on 2009-10-30
thanks, will do :)

---

### Post by lovinglinux on 2009-10-30
I recommend **kde-minimal** if you are running Karmic. It just installs the basic stuff. You might also want **kdeplasma-addons**, to get the full fancy desktop. 

The package **kde-full** will install more stuff than the regular Kubuntu installation. To get all the packages of Kubuntu, then the necessary package is **kubuntu-desktop**.

If you are running Jaunty, then equivalent package for **kde-minimal** should be **kde-core**.

Take a look at [http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core) for more info.

---

### Post by TheNessus on 2009-11-01
Somehow I don't seem to have a network manager installed on KDE-minimal, i.e. no wireless, specifically.

---

### Post by lovinglinux on 2009-11-01
> **TheNessus said:**
> Somehow I don't seem to have a network manager installed on KDE-minimal, i.e. no wireless, specifically.

```
sudo apt-get install network-manager
```

Nevertheless, some users cannot use wireless with that and need to install wicd.

---

### Post by TheNessus on 2009-11-03
thanks yet again

---

