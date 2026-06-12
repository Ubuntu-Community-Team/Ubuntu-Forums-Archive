---
title: "MySQL 5.1.30 in Ubuntu 8.04?"
date: 2009-05-21
forum: Server Platforms
---

### Post by malikp on 2009-05-21
Hi,
 I think post in correct category.
 

 I have Production Ubuntu server 9.04 with MySQL 5.1.30
 Now I have to move the data base to another server running Ubuntu 8.04 with Mysql 5.0.51.
 But we used MySQL 5.1.30 new feature partitioning, I have to upgrade MySQL server to 5.1. But look like Ubuntu 8.04  repository do not provide new MySQL version.
  

 I can think of few options.  
 
[LIST=1]
[*]Upgrade server to 9.04 and then 	Upgrade MySQL
[*]Download MySQL from MySQL site and 	install – But later stage I may have issues upgrading and applying 	patches
[*]Install MySQL from another 	repository as [this post]("http://ubuntuforums.org/showthread.php?t=1039946&highlight=mysql+5.1")  	 But I do not like to do so, since this a 3rd pary
 	  	
[/LIST]
 What do you guyed think?
 What is the best approach? Is there more options?
 

 Thank you,

---

### Post by meonkeys on 2009-07-22
malikp,

Just curious if you found a solution or a workaround ... I'm currently facing the same issue on an 8.04 server (need MySQL 5.1).

Thanks,
-Adam

---

### Post by Cheesemill on 2009-07-23
Read up on Ubuntu Backports, it may be what you're after.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by meonkeys on 2009-07-23
> **Cheesemill said:**
> Read up on Ubuntu Backports, it may be what you're after.

Cool, thank you! I always wondered what backports were. :)

Looks like mysql-server-5.1 is [not currently backported to Hardy]("http://packages.ubuntu.com/hardy-backports/"), but there is [a brand-new open issue about it]("https://bugs.launchpad.net/hardy-backports/+bug/403562/").

---

