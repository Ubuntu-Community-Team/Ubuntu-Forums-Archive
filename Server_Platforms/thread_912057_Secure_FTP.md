---
title: "Secure FTP"
date: 2008-09-06
forum: Server Platforms
---

### Post by Vegan on 2008-09-06
Finally figured out why Secure FTP was not working.

sudo apt-get install open-ssh

does not install the tools to enhance FTP.

sudo apt-get install sftp

will permit the desired functionality. Now you can connect with WinSCP and move files back and forth easily.

:guitar:

---

