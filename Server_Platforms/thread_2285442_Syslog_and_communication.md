---
title: "Syslog and communication"
date: 2015-07-06
forum: Server Platforms
---

### Post by killerbee8 on 2015-07-06
Hi everyone, I'm new at this forum, and not sure that I've postet this text right, so sorry.
I got an quest to cofigure a syslog on a Ubuntu Server 14.04. The main problem is that it doesn't gather logs.
I am using webmin form this page [http://askubuntu.com/questions/78627/problem-connecting-to-webmin](http://askubuntu.com/questions/78627/problem-connecting-to-webmin) and the configuration of it from a polish page [http://linuxblog.com.pl/?p=26](http://linuxblog.com.pl/?p=26)
Rhe syslog is working, the firewall for port 514 is down and i can see the computer with ubuntu by the ping command, but when I send debug or other logs, the ubuntu computer, where syslog is doesn't gather the logs. I've made specified folders for testing and the are empty.

Hope you can help me with this problem and hope hearing from you soon.

---

### Post by ajgreeny on 2015-07-06
Hi killerbee8, and welcome to the forum.

I have moved this thread from Other OSs where you put it to Server platforms as you may get more assistance in this section.

---

### Post by nerdtron on 2015-07-06
Have you opened port 514 on both UDP and TCP connections? Also, see options here: [http://askubuntu.com/questions/53910/how-can-i-receive-syslog-logs-from-a-networked-system](http://askubuntu.com/questions/53910/how-can-i-receive-syslog-logs-from-a-networked-system)

---

### Post by killerbee8 on 2015-07-07
Yes, I've opened them in the config

---

### Post by killerbee8 on 2015-07-08
I've solved the problem. Found it on: [http://community.spiceworks.com/how_to/65683-configure-ubuntu-server-12-04-lts-as-a-syslog-server](http://community.spiceworks.com/how_to/65683-configure-ubuntu-server-12-04-lts-as-a-syslog-server)

---

