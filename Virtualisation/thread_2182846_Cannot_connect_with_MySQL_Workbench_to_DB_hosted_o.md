---
title: "Cannot connect with MySQL Workbench to DB hosted on Vbox"
date: 2013-10-22
forum: Virtualisation
---

### Post by U2XS on 2013-10-22
I got a vanilla installation of Ubuntu 13.04 server edition from [Virtualboxes.com]("http://virtualboxes.org/images/ubuntu/").  I've set that virtual machine to bridged mode so it has it's own IP address.  I then added Apache/MySQL/PHP by running

```
Sudo apt-get install PHPMyAdmin
```

I'm able to login to PHPMyAdmin by going to the URL on the Windows 7 host.  (So far so good!)  However that host also has MySQL Workbench.  When I attempt to add my database, I get the following error.  The only thing I can figure is that I missed a step somewhere with permissions or by opening the port 3306. Does anyone know what to do next?

[IMG]http://imageshack.com/a/img855/1574/m6v9.png[/IMG]

---

### Post by SeijiSensei on 2013-10-22
First, it is likely that MySQL is restricted to listening on the localhost interface.  Find the "bind-address" line in my.cnf.  If it reads "bind-address = 127.0.0.1" replace the "127.0.0.1" with "0.0.0.0" and restart MySQL.  I think "ALL" is an acceptable alias the all-zeroes address. Commenting out the bind-address directive with a hash mark ("#") may also work.

Second, remember that MySQL manages permissions by using the 'user'@'host' style of accounts.  If you want to be able to connect as the root user from a remote machine, add a MySQL user called 'root'@'%' which matches any remote hostname and IP address.  Any other remote users must have entries of the 'user'@'%' or 'user'@'ip_address' form as well.

---

### Post by U2XS on 2013-10-23
> **SeijiSensei said:**
> First, it is likely that MySQL is restricted to listening on the localhost interface.  Find the "bind-address" line in my.cnf.  If it reads "bind-address = 127.0.0.1" replace the "127.0.0.1" with "0.0.0.0" and restart MySQL.  I think "ALL" is an acceptable alias the all-zeroes address. Commenting out the bind-address directive with a hash mark ("#") may also work.

Second, remember that MySQL manages permissions by using the 'user'@'host' style of accounts.  If you want to be able to connect as the root user from a remote machine, add a MySQL user called 'root'@'%' which matches any remote hostname and IP address.  Any other remote users must have entries of the 'user'@'%' or 'user'@'ip_address' form as well.
Thanks!  We're definitely getting closer.  Now the error message is that the privileges are not set, which is, of course a step up.

[IMG]http://imageshack.com/scaled/large/692/5m3p.png[/IMG]

I assume you meant a MySQL user, not a Linux user. [ Following pretty basic instructions]("https://www.digitalocean.com/community/articles/how-to-create-a-new-user-and-grant-permissions-in-mysql"), I added one which has full permissions.  I tried with both root & remote (the new name) with the same results.

Also, I wasn't sure if I understood the format correctly, so I tried everything:

'root'@'%'
'remote'@'%'
root'@'%
remote'@'%

---

### Post by Habitual on 2013-10-23
Connect as root with out all that other stuff.

Host: 10.1.10.201
username: root
password: <you know this>

if that fails, then login as root to 10.1.10.201 and run

 ```

mysql 
grant all on *.* to 'root'@'10.1.10.101' ; flush privileges; exit; 
```

and back at your computer with workbench connect as:
Host: 10.1.10.201
username: root
password:<you know this>

Edit: Wed Oct 23, 2013 - 5:06:44 PM EDT
Provided you've followed the advice about the edit to my.conf.

---

