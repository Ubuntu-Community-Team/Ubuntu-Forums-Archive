---
title: "Beta-2 user now not in sudoers file"
date: 2016-04-04
forum: Ubuntu Development Version
---

### Post by Nick Payne on 2016-04-04
I installed 16.04 beta-2 amd64 into a Virtualbox VM last week, and was subsequently able to run activities that required sudo, such as using apt-get to install additional apps or to update without any problem. However, when I startup the VM this morning, login, run sudo apt-get update in a terminal, and supply my password, I get the response "nick is not in the sudoers file.  This incident will be reported." I haven't edited sudoers, and when I check /etc the sudoers file is still there, and has a date of September last year:

```
-r--r----- 1 root root  745 Sep 23  2015 sudoers
```

but with the present state of things I can't view or edit it. If I boot the VM off the live CD, am I just going to get the same sudoers file if I copy the version across from the live CD?

---

### Post by cariboo on 2016-04-04
That date of the file isn't the problem, as mine has the same date. Make sure you are in the the adm and sudo groups:

```
cariboo@skynet:/etc$ groups
cariboo adm cdrom sudo dip plugdev lpadmin sambashare
```

---

