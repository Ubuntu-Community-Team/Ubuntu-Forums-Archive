---
title: "Upgrading to ubuntu 16.10"
date: 2016-09-22
forum: Ubuntu Development Version
---

### Post by thedoctor818772 on 2016-09-22
I am running Ubuntu 16.04 and am trying to upgrade to the final beta of Ubuntu 16.10 but cannot seem to do so. Everytime I try (even in the terminal) I get the message: there are no new upgrades available. I have tried:

```

sudo do-release-upgrade -d

```

to no avail. Please help!

Thanks.

---

### Post by T.J. on 2016-09-22
I'm not trying to be rude, but you should never expect beta software to work properly.  That is why it is beta.  That said, I would wait until after it is released before you upgrade, unless you intend to completely reinstall.  Unlike its parent version, "in place" upgrades seldom work on Ubuntu because of the release schedules.

---

### Post by oldfred on 2016-09-22
I always keep the newest LTS as my main working install. But then install any other versions like 16.10 in another 25GB / (root) partition, so I can see what has changed and that it works with my hardware & configuration.

---

### Post by howefield on 2016-09-22
Thread moved to the "*Ubuntu Development Version*" forum.

---

### Post by mc4man on 2016-09-22
Your command looks for a new(er) release to upgrade to. 16.10 has not yet been released yet so there's no release to upgrade to.

---

### Post by Frogs Hair on 2016-09-22
I used the following commands successfully a few hours ago.I first made sure 16.04 was update , all non Ubuntu software sources were disabled, and backed-up my home folder files to dropbox . All GTK 3.18 themes were broken after upgrade and clean-up had to be done manually via the command line. Good luck !

Edit: Ubuntu software had to be reinstalled after the autoremove command, synaptic was not affected.

```
sudo sed -i 's/xenial/yakkety/g' /etc/apt/sources.list 

```
```
sudo apt update && sudo apt dist-upgrade 
```

[https://wiki.ubuntu.com/U%2B1/common-problems](https://wiki.ubuntu.com/U%2B1/common-problems)

---

