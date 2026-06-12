---
title: "Shell Script To Auto Install Software and Configure"
date: 2008-07-27
forum: Server Platforms
---

### Post by viper2007 on 2008-07-27
Hi everybody,

I´m writing a shell script to auto install my server and auto configure its settings and have run into a snag and cant find the information I need.

I´m stuck on using sed, awk, etc...

For Example:

I want my script to search inside the /etc/mysql/my.cnf and find the bind-address line and comment out that line.

**Original:**

...
bind-address 127.0.0.1
...

**After Script is Run:**

...
#bind-address 127.0.0.1
...

Thanks for all your help.

---

### Post by bluefrog on 2008-07-29
sed -i 's/^bind-address.*127.0.0.1/#&/' /etc/mysql/my.cnf

---

