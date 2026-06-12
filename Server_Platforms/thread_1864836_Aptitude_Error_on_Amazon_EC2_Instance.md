---
title: "Aptitude Error on Amazon EC2 Instance"
date: 2011-10-19
forum: Server Platforms
---

### Post by alexlafreniere on 2011-10-19
I am running Ubuntu on an Amazon EC2 instance, I tried running
```
sudo tasksel --section server
```
and selecting LAMP server but the installer errors out saying
```
tasksel: aptitude failed (100)
```
Could anyone help me out with this? Thanks in advance.

---

### Post by Jonathan L on 2011-10-19
> **alexlafreniere said:**
> ```
tasksel: aptitude failed (100)
```.

Hi

I just repeated this and get the same error.  First update the database of where the packages are: 
```
 sudo apt-get update
```Then do the tasksel and it works fine.

Tested on ami-311f2b45, which is 32-bit Ubuntu 10.04.

Kind regards,
Jonathan

---

