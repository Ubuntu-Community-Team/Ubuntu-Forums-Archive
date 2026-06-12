---
title: "apt-get issues"
date: 2005-12-10
forum: Server Platforms
---

### Post by iwalmsley on 2005-12-10
I have ran two commands that I am having issues with. The first is for ftpd
" apt-get install ftpd "  I get:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ftpd

Also
" apt-get install request-tracker"
I get:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package request-tracker

Both packages exsist: [http://packages.ubuntu.com/breezy/misc/request-tracker3.4](http://packages.ubuntu.com/breezy/misc/request-tracker3.4)

Anyone provide information? I wish to use the apt-get function because request-tracker requires lots of dep. 

Thanks.

---

### Post by Leif on 2005-12-10
have you enabled universe and multiverse ? open your sources file (sudo gedit /etc/apt/sources.list) and remove then #s in front of the relevant lines. save & close, then "sudo apt-get update" and try again

---

### Post by iwalmsley on 2005-12-10
Thanks. That did the trick!!!

---

