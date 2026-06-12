---
title: "Disk Quota with authetication server"
date: 2011-09-18
forum: Server Platforms
---

### Post by ashiq_rahman on 2011-09-18
I have 20 windows PC and 20 Ubuntu desktop PCs in a laboratory. I have a  Ubuntu 10.04 LTS server. In this laboratory there are 150 user. I want  to provide 10 MB of space in server for each user and I want to  authenticate user from any terminal and provide the space allocated for  the user. What are service I must have in server and client.

Thanks in advance
Ashiq

---

### Post by zackwasa on 2011-09-18
This is how you enable quotas on Ubuntu:
[http://www.ubuntugeek.com/how-to-setup-disk-quotas-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-disk-quotas-in-ubuntu.html)

You will then need to install a FTP server and then add the users as system accounts.

---

