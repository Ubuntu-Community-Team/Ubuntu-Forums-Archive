---
title: "haproxy or barracuda for load balancing?"
date: 2011-08-18
forum: Server Platforms
---

### Post by skrite on 2011-08-18
Hey all, I am about to build a server cluster with mysql-cluster and a couple of apache webservers. I have found lots of tutorials regarding the setup of haproxy, but i have the option to get a pretty affordable barracuda load balancer. Now, i am kinda new at this. But my main questions are.. Can the load balancer also serve for the database?  Is it a straightforward configuration? What might be the advantage / disadvantage with going for a hardware solution instead of a software solution?

thanks for any advice

---

### Post by dinu90 on 2011-08-18
There's a mysql proxy designed especially for mysql clusters. You can find it here:
[http://forge.mysql.com/wiki/MySQL_Proxy](http://forge.mysql.com/wiki/MySQL_Proxy)
[**java tutorials**]("http://www.java-forums.org/java-tutorial/")

---

