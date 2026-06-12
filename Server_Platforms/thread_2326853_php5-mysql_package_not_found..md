---
title: "php5-mysql package not found."
date: 2016-06-05
forum: Server Platforms
---

### Post by Abdullah_Khalid on 2016-06-05
Hi, I'm trying to install a LAMP server. I looked at search to find the answer however the fix is not there.

Ran the following command:
```
sudo apt-get install php5-mysql
```
And got This:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package php5-mysql is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'php5-mysql' has no installation candidate
```

Where can I find this or solve the problem?
 Thank You.

---

### Post by howefield on 2016-06-05
Thread moved to the "*Server Platforms*" forum.

Is this for 16.04 ?

Looks like it might just be php-mysql now.

---

### Post by Abdullah_Khalid on 2016-06-05
Yeh bro its 16.04. and removing the "5" worked. Can you tell me how you knew that? For further references if something changed how can I figure it out myself?
Thanks.

---

### Post by howefield on 2016-06-07
> **Abdullah_Khalid said:**
> ... Can you tell me how you knew that? For further references if something changed how can I figure it out myself?

Personal experience setting up an owncloud server, general experience of how these things can change and following the links from packages.ubuntu.com

---

