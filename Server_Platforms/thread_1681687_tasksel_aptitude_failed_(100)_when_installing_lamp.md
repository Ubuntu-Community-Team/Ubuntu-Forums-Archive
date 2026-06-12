---
title: "tasksel: aptitude failed (100) when installing lamp on EC2"
date: 2011-02-04
forum: Server Platforms
---

### Post by JJJollyjim on 2011-02-04
I have an ec2 instance, with ubuntu server edition 10.10, and I am trying to install lamp. When I run sudo tasksel --section server, select lamp, and select ok, I get: tasksel: aptitude failed (100). Help?

---

### Post by yuvals on 2011-02-04
did you try 
sudo apt-get update
?

---

### Post by nlsn on 2011-05-11
> **yuvals said:**
> did you try 
sudo apt-get update
?

This worked for me.

---

