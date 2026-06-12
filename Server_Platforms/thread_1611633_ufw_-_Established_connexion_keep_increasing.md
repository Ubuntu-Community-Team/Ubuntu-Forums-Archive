---
title: "ufw - Established connexion keep increasing"
date: 2010-11-02
forum: Server Platforms
---

### Post by bactisme on 2010-11-02
Hello, 

I migrate a server on a new machine. This server is installed on Lucid Lynx. 

The server is runing Apache, myslq (IP.Board).

I configured Munin and the firewall is ufw. And after few days (3), i get the following graph in Munin. The ipconntrack keep increasing also. 

I don't have other data to compare, but i suppose this is not really normal. What is happening? What can I do to understand the problem? Of course, after reboot everything is ok (not shown on the graph)

Here is my UFW configuration (not finished I suppose - but i am not so skilled)

-----------------------------------------------------
root@ns25943:~# ufw status
Status: active
To                         Action      From
--                         ------      ----
25/tcp                     ALLOW       Anywhere
80                         ALLOW       Anywhere
53                         ALLOW       Anywhere
22                         ALLOW       Anywhere
143                        ALLOW       Anywhere
110                        ALLOW       Anywhere
443                        ALLOW       Anywhere
-----------------------------------------------------

Thank you very much, 

Baptiste M

---

