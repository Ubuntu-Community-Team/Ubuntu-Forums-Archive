---
title: "Snort Install Help"
date: 2009-12-28
forum: Security
---

### Post by jasonpjohnson on 2009-12-28
I have a brand new snort setup with Ubuntu 9 Server. Here is the issue

Snort / MySQL / Base / Appache

Everything runs great if when I log in i run "/etc/init.d/snort start" or "/etc/rc2.d/snort start" I have set all permissions on the init.d file to 750, and for the life of me I can not get it to start on boot up, I can't see any errors on startup, nothing in the boot log, or messages. When I run ps -ef | grep snort I don't see my process if I run the script from either init.d or rc2.d it will return my process

If it matters I didn't do apt-get install snort-mysql I complied from the latest source on snort.org.



ANY HELP IS GREATLY APPRECIATED I AM VERY NEW TO LINUX!!

---

### Post by jasonpjohnson on 2009-12-28
FIXED!!! So proud...

in the init.d script it start snort like this "snort -c /etc/snort/snort.conf -i eth0 -D" 

I changed it to this "/usr/local/bin/snort -c /etc/snort/snort.conf -i eth0 -D" and it worked...can anyone tell me why?


Thanks!

Jason:guitar:

---

