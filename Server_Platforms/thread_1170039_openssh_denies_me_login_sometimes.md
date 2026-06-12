---
title: "openssh denies me login sometimes"
date: 2009-05-25
forum: Server Platforms
---

### Post by lockmac on 2009-05-25
Hi. I have installed openssh on ubuntu. Havn't changed any config files, but sometimes it wont let me login. Most times it will, but sometimes it wont (guarantee its the right password and user). Resetting the server will let me log back in. This is on the local network. I forward my ports in the firewall and tryed from another network and it wouldnt let me log in at all.

Any ideas why?

---

### Post by gombadi on 2009-05-25
Have a look in the log files.

For logins via ssh look in /var/log/auth.log

Show the output here and someone will help you decode it.

---

### Post by lockmac on 2009-05-27
Hi their. Their is absolutely nothing in that log. Just a cron job that runs every half hour from i see. It only sees to be happening from outside networks (e.g. from my work place)- I get the login prompt but it says the user or password is denied, where if I come home with the same computer (laptop) and connect, it works fine.

Any ideas?

---

### Post by gombadi on 2009-05-27
> 
Hi their. Their is absolutely nothing in that log. Just a cron job that runs every half hour from i see. It only sees to be happening from outside networks (e.g. from my work place)- I get the login prompt but it says the user or password is denied, where if I come home with the same computer (laptop) and connect, it works fine.

Any ideas? 


Have you changed the way syslog logs files? If not then anything that ssh logs will go to the /var/log/auth.log file. You can test it by restarting ssh - it will log the restart event to the log file.

If that file has no ssh entries then my guess is that you are not connecting to the server you are thinking you are connecting to.

Use the -v option for ssh to see more information and also what machine you are connecting to.
```
ssh -v user@server
```

---

### Post by lockmac on 2009-05-27
Thanks for the reply. Well when you said i might not be connecting to the right server, I connected using my external address (vpn-gw.xxxx.com, the address i try when im on a diferent network, and it did connect to ssh and i could see this in the log). I did a restart at that was in the log as well as well as it showing that i connected to it through the external IP, yet nothing at all from it denying my login from antoher network....

OK now I am thinking when im on a different netork, it wants me to connect to my routers SSH (3rd party firmware) even though I have port 22 forwarded. Might have to turn this off and try again..

---

