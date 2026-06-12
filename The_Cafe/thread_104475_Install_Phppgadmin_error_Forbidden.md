---
title: "Install Phppgadmin error Forbidden"
date: 2005-12-16
forum: The Cafe
---

### Post by shahMK on 2005-12-16
Hi, 

I successfully install phppgadmin and access using [http://localhost/phppgadmin](http://localhost/phppgadmin) got no problem.
But access using IP address from another PC [http://10.1.16.26/phppgadmin](http://10.1.16.26/phppgadmin) getting below error.

Forbidden
You don't have permission to access /phppgadmin on this server.

Pls help.

--shahMK

---

### Post by shahMK on 2005-12-18
I managed to solve it myself as below

sudo /etc/apache2/apache2.conf

unmark "allow from all" under the <DirectoryMatch /usr/share/phppgadmin/>

restart apache2 using /etc/init.d/apache2 restart


Thanks.

---

### Post by Tookie on 2008-03-28
Hello,

I had exactly the same error and I only found the answer here. Many thanks !!
But there's just a little mistake : the file to change is (now)

/etc/apache2/conf.d/phppgadmin.conf

And if you do not want to "allow from all" you just have to enter a new line :

allow from yourIP/mask

Thanks !

---

### Post by carlos22 on 2008-12-14
Thanks a lot.
this is valid for Debian lenny (apache2).

keep on guys.

---

### Post by hellblazer on 2012-02-29
still works ;-)

---

### Post by overdrank on 2012-02-29
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]

---

