---
title: "File system error?"
date: 2008-01-08
forum: Server Platforms
---

### Post by dongthao on 2008-01-08
I'm using Ubuntu 7.04 Server, and one day I met a problem with SSHD. 
[LIST]
[*] When make a ssh connection to the server from remote machine, it says server refuses. Trying make a connection from the server locally, it throws "Segmentation fault".
[*]I restart sshd with "/etc/init.d/ssh restart", it says "Segmentation fault", too.
[*]Then I try to remove the openssh-server for reinstalling but couldn't because system can't stop sshd with the init script. I debugged in /etc/init.d/ssh script and found problem at "log_messageXXX" functions. After commenting out all "log" functions, sshd can be stopped and removed but the **/usr/sbin/sshd** file can't be deleted!
[*]After that, I decided to delete it manually, but I can't because, it said " Operation not permitted" (I'm being root).
[*]When I restart server, many "Segmentation fault" messages appear in shutdown and startup process!
[*]**Now I don't know how to delete the /usr/sbin/sshd file. I tried with single mode, livecd. Other files in /usr/sbin/ can be modify normally.**[/LIST]Anyone show me the way to solve this case? Thanks.

---

### Post by gaten on 2008-01-09
OK, if you can't delete the file from a live CD, something is seriously wrong. Try checking the filesystem from the liveCD and see if any errors pop out.   Also, I assume ```
sudo apt-get remove openssh-server
``` doesn't work?

---

