---
title: "[SOLVED] Install fail2ban, but no config files present"
date: 2007-09-28
forum: Server Platforms
---

### Post by tr333 on 2007-09-28
I just installed fail2ban on a Ubuntu 7.04 Server, but there is nothing in /etc/fail2ban/, only two empty directories: action.d/ and filter.d/

Did I miss out something in the install step?  I've tried doing a "sudo apt-get install --reinstall fail2ban" and also "sudo dpkg-reconfigure fail2ban".

EDIT:  Why is Ubuntu shipping a development version of fail2ban?  The version from the universe repository is 0.7.6-3ubuntu1, and the fail2ban website says odd numbers are development while even numbers are stable.

---

### Post by Braino on 2007-09-29
The config file is in /etc/fail2ban.conf (tab-completion is your friend)

---

### Post by Braino on 2007-09-29
Oops, didn't see your edit. The version you downloaded from the Ubuntu repositories is 0.7.6-3ubuntu1. This corresponds to fail2ban's version 0.7.6. The other numbers have to do with the Ubuntu package versions. However, in the fail2ban changelog, it says 0.7.6 is beta and 0.7.7 is a release candidate, so your point is still somewhat valid.

---

### Post by tr333 on 2007-09-30
I solved the problem by doing a "sudo dpkg --purge fail2ban" and removing the folders listed as not being empty.  Installing after doing that seemed to put things back to normal.

FYI, the /etc/fail2ban.conf file is for versions < 7. Versions 7+ seem to put the configs in the /etc/fail2ban/ folder.

---

