---
title: "Getting an error an AppStream cache?"
date: 2016-11-25
forum: Server Platforms
---

### Post by andreadixon825 on 2016-11-25
Hello , I cant install stuff and cant even update because of this error, Here is what it looks like.

```
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
```

What does that mean and how do I fixes this? Thank you for your time. Oh and I'm using 16.04, I have never encountered this error before.

---

### Post by slickymaster on 2016-11-25
*Thread moved to **Server Platforms**.*

---

### Post by cariboo on 2016-11-26
Just rename the file to 50unattended-upgrades:

```
sudo mv /etc/apt/apt.conf.d/50unattended-upgrades.ucf-dist /etc/apt/apt.conf.d/50unattended-upgrades
```

---

### Post by mc4man on 2016-11-27
There are 2 bug reports similar though reported from desktop, not server users, one  fixed, the other open

[https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1575248](https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1575248)
[https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1644498](https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1644498)

---

