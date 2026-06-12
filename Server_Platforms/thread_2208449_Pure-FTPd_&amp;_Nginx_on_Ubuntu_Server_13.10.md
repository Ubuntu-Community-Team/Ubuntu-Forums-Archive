---
title: "Pure-FTPd &amp; Nginx on Ubuntu Server 13.10"
date: 2014-02-28
forum: Server Platforms
---

### Post by Roswebnet on 2014-02-28
Hi everyone,
   I would like to configure Pure-FTPd to access the Nginx files on Ubuntu Server 13.10. The root webpages directory of nginx is (there all my websites):
   ```
/usr/share/nginx/
```
   Ubuntu installed on Virtualbox. Therefor, I belive is no problems with Firewall. I did following steps during installation and configuration of the Pure-FTPd:
   ```
apt-get update
   apt-get upgrade
   apt-get install pure-ftpd
   cd /etc/pure-ftpd/conf/
   echo ,21 > Bind
   echo 50100 50200 > PassivePortRange
   echo yes > BrokenClientsCompatibility
   echo 5 > MaxClientsPerIP
   echo 20 > MaxClientsNumber
   echo /etc/pure-ftpd/pureftpd.pdb > PureDB
   ln -s /etc/pure-ftpd/conf/PureDB ../auth/50pure
   groupadd -g 2001 ftpgroup
   useradd -u 2001 -s /bin/false -d /bin/null -c "pureftpd user" -g ftpgroup ftpuser
   mkdir -p /home/pureftp/pure
   ln -s /usr/share/nginx/ /home/pureftp/pure/www
   chown -R ftpuser:ftpgroup /home/pureftp
   pure-pw useradd pure -u ftpuser -g ftpgroup -d /home/pureftp/pure/www -N 10
   pure-pw mkdb
   pure-pw list
   usermod -a -G www-data ftpuser
   service pure-ftpd restart
   service nginx restart
```
    
   I can login and see files. However, I cannot create, edit, upload or delete any file (Permission denied). What is wrong?
    
   Thank you.
    
   Sources:
   [http://wiki.ggis.biz/index.php/Pure-FTPd_on_Ubuntu](http://wiki.ggis.biz/index.php/Pure-FTPd_on_Ubuntu)
   [https://help.ubuntu.com/community/PureFTP](https://help.ubuntu.com/community/PureFTP)
   [http://pastebin.com/RSnfqcF2](http://pastebin.com/RSnfqcF2)

---

### Post by bashiergui on 2014-03-02
You probably need to change the conf file to allow those actions. I haven't used Pure-ftpd but vsftp had those actions blocked by default.

---

### Post by Roswebnet on 2014-03-03
Hi 
as I understood from searching the problem is in permissions, groups and users. 
What I need precisely:

- Nginx/PHP FPM needs read/write/execute access to the php files in the
document root as various files are uploaded and moved around.
- Pure-FTPd needs read/write access to the files as well so that changes can
be made.

I've tried adding the nginx user (www-data) to the ftpgroup, as well as adding ftpuser
to the nginx group.
Neither seems to allow both nginx and my virtual ftp users to have write
access.

---

### Post by Roswebnet on 2014-03-09
I solve it like this:

```
usermod -aG ftpgroup www-data
chown -R ftpuser:ftpgroup /usr/share/nginx/
chmod -R g+ws /usr/share/nginx/

```

Don't forget to restart nginx and pure-ftpd.

---

