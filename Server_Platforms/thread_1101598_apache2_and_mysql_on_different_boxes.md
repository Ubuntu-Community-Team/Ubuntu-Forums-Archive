---
title: "apache2 and mysql on different boxes"
date: 2009-03-20
forum: Server Platforms
---

### Post by maxwas on 2009-03-20
Hi all,

I would like to experiment with a particular lamp setup and would like some advice.

Instead of running everything from one box, i would like to run mysql on a separate box from apache.

What i was going to do was have a lamp setup on both boxes, except on one box (boxB), just turn apache off and have mysql running. 
On the box that runs apache (boxA) i would turn off mysql.

Say for example i was installing wordpress on boxA, would i just point the config.php (with db details) to the ip address of boxB. 

Do you think that is the most efficient way of doing things?


Any advice would be great :)

Thanks

---

### Post by TurboRush on 2009-03-20
I tried doing this a few months ago because the my server was relatively low powered so I wanted to split some of the processing load. 

While this is probably due to my lack of experience I couldn't get around a pretty significant delay that was introduced each time a connection to the database was needed. The overall speed of the site dropped significant as a result.

Again, this was probably do to my lack of knowledge.

---

### Post by MystaMax on 2009-03-20
You wont need to disable apache on boxB because it shouldn't be installed. You should only install the packages that you need per server.

boxA
apache
php5 and php5 module for apache

boxB
mysql

You should be able to run wordpress in the way you state w/o issues.

In terms of efficiency, my first thought is it depends on how much traffic you expect the server to get. But, I'm not sever guru. I'll leave the rest to someone else.

Hope that helps.

---

### Post by cdenley on 2009-03-20
> **TurboRush said:**
> I tried doing this a few months ago because the my server was relatively low powered so I wanted to split some of the processing load. 

While this is probably due to my lack of experience I couldn't get around a pretty significant delay that was introduced each time a connection to the database was needed. The overall speed of the site dropped significant as a result.

Again, this was probably do to my lack of knowledge.

Sounds like a hostname resolution problem was causing your delay. I believe the mysql server has to resolve the hostname of the client in order to check permissions of the connecting host. You should make sure there is an entry for the client in the /etc/hosts file on your database server.

---

### Post by maxwas on 2009-03-20
> You should only install the packages that you need per server.

That's kinda what i am worried about. If i have mysql on boxB i will still need php functionality (php5-mysql) wont i?

Say i want to administer mysql with phpmyadmin, do i point phpmyadmin on boxA to boxB? 

Thanks for the replies

M

---

