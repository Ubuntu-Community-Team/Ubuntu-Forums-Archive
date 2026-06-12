---
title: "Doing System and Security updates"
date: 2012-02-20
forum: Server Platforms
---

### Post by TFroehlich3 on 2012-02-20
Hello Everyone,
   I was just wondering how to do the system updates and security updates. I run this command 
```
sudo apt-get update
``` 
but the next time I log into the system (even after rebooting) it says I still have updates. Am I doing something wrong? :confused:

---

### Post by cortman on 2012-02-20
Apt-get update simply updates the repository lists. To actually update your system, you need to run

```
sudo apt-get upgrade
```

Good luck!

---

### Post by TFroehlich3 on 2012-02-21
> **cortman said:**
> Apt-get update simply updates the repository lists. To actually update your system, you need to run
 
```
sudo apt-get upgrade
```
 
Good luck!
 
 Thank you! I will try this when I get out of work! :)

---

