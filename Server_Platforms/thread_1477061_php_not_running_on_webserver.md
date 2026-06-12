---
title: "php not running on webserver"
date: 2010-05-08
forum: Server Platforms
---

### Post by tckotb on 2010-05-08
when i go to my server's IP address, the index.php files is downloaded, not run, how can I fix this? I have php5 installed and enabled.

> root@ubuntu:~$ ls /etc/apache2/mods-enabled/
alias.conf            authz_user.load  dir.load          php5.load
alias.load            autoindex.conf   env.load          reqtimeout.conf
auth_basic.load       autoindex.load   mime.conf         reqtimeout.load
authn_file.load       cgi.load         mime.load         setenvif.conf
authz_default.load    deflate.conf     negotiation.conf  setenvif.load
authz_groupfile.load  deflate.load     negotiation.load  status.conf
authz_host.load       dir.conf         php5.conf         status.load
root@ubuntu:~$

---

### Post by Ryan Dwyer on 2010-05-08
$ cat php5.conf

You should get this: [http://paste.ubuntu.com/430291/](http://paste.ubuntu.com/430291/)

Also make sure your Apache service has been restarted since PHP5 was installed: sudo /etc/init.d/apache2 restart

And if that still doesn't work, reinstall PHP5 with: sudo apt-get install --reinstall libapache2-mod-php5

---

### Post by kevin11951 on 2010-05-08
Execute the following:
```

chown -R www-data:www-data /var/www
chmod -R 0755 /var/www

```

Clear your web browsers cache, and you should be good to go.

---

### Post by cariboo on 2010-05-09
Make sure you have libapache2-mod-php5 installed.

---

### Post by tckotb on 2010-05-09
Thanks, worked great

---

