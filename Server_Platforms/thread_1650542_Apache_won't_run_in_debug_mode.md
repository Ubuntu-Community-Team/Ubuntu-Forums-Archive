---
title: "Apache won't run in debug mode"
date: 2010-12-21
forum: Server Platforms
---

### Post by DirtyJohnson on 2010-12-21
Can someone tell me how to get apache to run in debug mode. I am trying to profile php/apache2 with callgrind and can't get it to work. This is in a virtual machine on my laptop. I am running 10.10 ubuntu.
 
So far I have tried
 
sudo -i . /etc/apache2/envvars; apache2 -X
sudo /usr/sbin/apache2ctl -X
sudo /etc/init.d/apache2 -X
sudo valgrind --tool=callgrind --dump-instr=yes -v --instr-atstart=no /usr/sbin/apache2 -X
 
and a few others
 
I get different results like 
 
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
Action '-X' failed.
 
(2)No such file or directory: apache2: could not open error log file /etc/apache2/${APACHE_LOG_DIR}/error.log.
Unable to open logs
 
and a few others
 
Thanks for any help

---

