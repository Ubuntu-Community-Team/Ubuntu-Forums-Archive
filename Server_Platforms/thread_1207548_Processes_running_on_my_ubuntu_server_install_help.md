---
title: "Processes running on my ubuntu server install help"
date: 2009-07-08
forum: Server Platforms
---

### Post by dinonet on 2009-07-08
Hi I just installed ubuntu server with a LAMP setup to run some simple things on the web server and ssh. I don't have any plans for doing anything heavy on it and I was wondering if I can view and turn of any of these 85+ processes that show up when I log in. Is there a resource somewhere that can help me take a look at how to keep this thing from hogging too many resources? Any info would be greatly appreciated. Thanks

System load: 1.09              Memory usage: 34%   Processes:       89

---

### Post by slugmax on 2009-07-09
You can install and run the package 'sysv-rc-conf' to display and selectively enable/disable services in individual runlevels (with the spacebar).  To just see what is running, use 'ps ax' or 'top'.

Some of your processes are duplicates, so you might have six apache processes, and two mysql-related processes, for example. This is normal. They won't be using much load if the system is idle. In the case of apache, you can configure the number of running child processes in /etc/apache2/apache2.conf.

---

