---
title: "Checking for Suspicious Account Use"
date: 2008-11-25
forum: Security
---

### Post by sulekha on 2008-11-25
Hi all,

the following is the recipe which i saw in Linux security cookbook

Checking for Suspicious Account Use

9.5.1 Problem
You want to discover unusual or dangerous usage of accounts on your system: dormant user accounts, recent logins to system accounts, etc. 

9.5.2 Solution
To print information about the last login for each user: 
$ lastlog [-u username]

To print the entire login history: 
$ last [username]

To print failed login attempts: 
$ lastb [username]

To enable recording of bad logins: 
# touch /var/log/btmp 
# chown --reference=/var/log/wtmp /var/log/btmp 
# chmod --reference=/var/log/wtmp /var/log/btmp

how correct is this recipe? what are the modifications/changes that needs to made so as to make it work in ubuntu 8.04.1

---

### Post by ibutho on 2008-11-25
It seems accurate to me and the only modification you may need to do is prefix individual commands with sudo. /var/log/btmp stores all the last bad logins, but in most distros its not created by default. If you run "lastb", a list of all bad logins since you created /var/log/btmp will be shown. For a specific user, its "lastb user".

---

### Post by cariboo on 2008-11-25
/var/log/btmp have been atomagically created on all the Debian based distro I have used.

Jim

---

