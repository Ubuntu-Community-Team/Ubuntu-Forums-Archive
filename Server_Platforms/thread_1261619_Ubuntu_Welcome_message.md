---
title: "Ubuntu Welcome message"
date: 2009-09-08
forum: Server Platforms
---

### Post by Cardale on 2009-09-08
When you login to Ubuntu server it displays some information.  I have 2 questions regarding this.

1. Where is this located and what can I do with it?
2. Is the update information accurate?
   The reason I ask is I did a 
```
sudo apt-get update
```
and
```
sudo apt-get upgrade
```
and the update information in the welcome message stayed the same.

You know the message "60 updates available with 40 being security updates" or what ever.  It didn't change.

---

### Post by ainsworth_t on 2009-09-09
That information should be contained within */etc/issue*. Couldn't tell you how accurate it is though.

---

