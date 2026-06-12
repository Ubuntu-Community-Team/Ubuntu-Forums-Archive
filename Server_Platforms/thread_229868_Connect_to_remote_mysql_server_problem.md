---
title: "Connect to remote mysql server problem"
date: 2006-08-05
forum: Server Platforms
---

### Post by acheun on 2006-08-05
I have a problem to connect to a remote mysql server, which is in my local network.  Here's my command

mysql -h jupiter -u root -p

jupiter is host name that mysql server resided.  After I entered my password, I got this message:

ERROR 2003 (HY000): Can't connect to MySQL server on 'jupiter' (111)

It is the same when I enter the IP address instead of jupiter.  Also, there is no firewall between the local network, and I can see the jupiter as it also my nfs server as well.

It's important for me to connect it remotely, as I want to separate apache server and mysql server in different box.  And I'm planning to install Drupal in apache server to host my home page.  Appreciate any idea can help.  Thanks.

---

### Post by Sam on 2006-08-05
Can you connect through telnet ??
```
$ telnet <host> 3306
```

---

### Post by lamego on 2006-08-05
Have you configured mysql on the remote server to bind to the network address ? 
The default mysql configuration on Ubuntu is to bind only to localhost making it unreachable to the network interface.

---

### Post by acheun on 2006-08-06
I tried using telnet and got this result.

telnet: Unable to connect to remote host: Connection refused

It seems I need to do some binding as lamego advice.  Is there any doc or link that can help me on this?

---

### Post by lamego on 2006-08-06
Read this how-to: [http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4)
Look at the mysql config section.

---

### Post by acheun on 2006-08-07
Thank lamego, the link helps.  I can connect to mysql server now.

---

