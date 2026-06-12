---
title: "Nginx + PHP + Mysql"
date: 2012-02-20
forum: Server Platforms
---

### Post by rodrane on 2012-02-20
hey guys I've install Nginx Php and Mysql.

actually Mysql was already installed which is working perfect with mysql workbench.

in Nginx Localhost

when i create index.php 

as 

<?php 

mysql_connect("localhost","root","password") or die(mysql_error());
phpinfo();

?>

it gives me internal server error 500 

then i commentout line mysql_connect and it actually works.

from yakuake i write 

mysql -u root -ppassword and i connect mysql...

well my question is what can be the problem ? 



Ps:I am using Ubuntu 11.10

---

### Post by memilanuk on 2012-02-21
No experience with nginx, but curious...

You're saying a basic phpinfo() call by itself does work, so php is installed correctly and nginx is parsing php files properly.

Have you tried using commands with the mysqli_ prefix instead of just mysqli_?

---

### Post by SeijiSensei on 2012-02-21
You nedd to have installed the php5-mysql and php5-mysqli packages to use any MySQL commands.  Run "sudo apt-get install php5-mysql*" to download them if they are missing.

---

