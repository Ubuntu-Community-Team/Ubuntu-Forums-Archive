---
title: "Getting a blank screen when accessing phpymadmin"
date: 2015-07-31
forum: Server Platforms
---

### Post by carolog on 2015-07-31
I recently installed a LAMP stack on a new Ubuntu 14.04 ec2 instance. I followed [this installation guide]("https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-14-04") by Digital Ocean and [this guide]("https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-14-04") to install phpmyadmin.

After installing phpmyadmin, every time I try and access it, I get a blank screen. I've tried these solutions but it has not helped:


[LIST=1]
[*][URL="http://askubuntu.com/questions/55280/phpmyadmin-is-not-working-after-i-installed-it"]phpmyadmin is not working after I installed it
[/URL]
[*][URL="http://askubuntu.com/questions/143185/phpmyadmin-not-working"]Phpmyadmin Not Working
[/URL]
[*][Blank page when trying to access phpmyadmin]("http://askubuntu.com/questions/143185/phpmyadmin-not-working")[URL="http://askubuntu.com/questions/58748/blank-page-when-trying-to-access-phpmyadmin?rq=1"]
[/URL]
[/LIST]

The Wordpress installation works great.

Any support to resolve this would be highly appreciated. Thanks.

---

### Post by SeijiSensei on 2015-07-31
Check /var/log/apache2/error.log and see what it reports.

---

### Post by carolog on 2015-07-31
Here is what I see in the error.log. I've also tried purging and reinstalling phpmyadmin with no resolution.

```
[Fri Jul 31 06:25:02.362198 2015] [mpm_prefork:notice] [pid 17249] AH00163: Apache/2.4.12 (Ubuntu) configured -- resuming normal operations
[Fri Jul 31 06:25:02.362213 2015] [core:notice] [pid 17249] AH00094: Command line: '/usr/sbin/apache2'
[Fri Jul 31 08:52:33.142848 2015] [:error] [pid 6968] [client 117.195.40.160:20243] PHP Fatal error:  require_once(): Failed opening required './libraries/php-gettext/gettext.inc' (include_path='.$
[Fri Jul 31 09:12:37.822507 2015] [mpm_prefork:notice] [pid 17249] AH00171: Graceful restart requested, doing restart
[Fri Jul 31 09:12:37.849511 2015] [mpm_prefork:notice] [pid 17249] AH00163: Apache/2.4.12 (Ubuntu) configured -- resuming normal operations
[Fri Jul 31 09:12:37.849518 2015] [core:notice] [pid 17249] AH00094: Command line: '/usr/sbin/apache2'
[Fri Jul 31 09:12:37.915308 2015] [mpm_prefork:notice] [pid 17249] AH00171: Graceful restart requested, doing restart
[Fri Jul 31 09:12:37.939042 2015] [mpm_prefork:notice] [pid 17249] AH00163: Apache/2.4.12 (Ubuntu) configured -- resuming normal operations
[Fri Jul 31 09:12:37.939052 2015] [core:notice] [pid 17249] AH00094: Command line: '/usr/sbin/apache2'
[Fri Jul 31 09:13:17.267534 2015] [:error] [pid 9106] [client 117.195.40.160:20978] PHP Fatal error:  require_once(): Failed opening required './libraries/php-gettext/gettext.inc' (include_path='.$
[Fri Jul 31 18:18:01.394920 2015] [:error] [pid 9113] [client 117.195.32.143:17426] WordPress database error Duplicate column name 'id' for query ALTER TABLE wp_duplicator_packages ADD COLUMN `id`$
[Fri Jul 31 18:18:01.395026 2015] [:error] [pid 9113] [client 117.195.32.143:17426] WordPress database error Duplicate column name 'name' for query ALTER TABLE wp_duplicator_packages ADD COLUMN `n$
[Fri Jul 31 18:18:01.395111 2015] [:error] [pid 9113] [client 117.195.32.143:17426] WordPress database error Duplicate column name 'hash' for query ALTER TABLE wp_duplicator_packages ADD COLUMN `h$
[Fri Jul 31 18:18:01.395192 2015] [:error] [pid 9113] [client 117.195.32.143:17426] WordPress database error Duplicate column name 'status' for query ALTER TABLE wp_duplicator_packages ADD COLUMN $
[Fri Jul 31 18:18:01.395275 2015] [:error] [pid 9113] [client 117.195.32.143:17426] WordPress database error Duplicate column name 'created' for query ALTER TABLE wp_duplicator_packages ADD COLUMN$
[Fri Jul 31 18:18:01.395330 2015] [:error] [pid 9113] [client 117.195.32.143:17426] WordPress database error Duplicate column name 'owner' for query ALTER TABLE wp_duplicator_packages ADD COLUMN `$
[Fri Jul 31 18:18:01.395387 2015] [:error] [pid 9113] [client 117.195.32.143:17426] WordPress database error Duplicate column name 'package' for query ALTER TABLE wp_duplicator_packages ADD COLUMN$
[Fri Jul 31 18:18:01.395442 2015] [:error] [pid 9113] [client 117.195.32.143:17426] WordPress database error Duplicate key name 'hash' for query ALTER TABLE wp_duplicator_packages ADD KEY `hash` ($
[Fri Jul 31 18:18:05.494960 2015] [:error] [pid 9113] [client 117.195.32.143:17426] PHP Fatal error:  require_once(): Failed opening required './libraries/php-gettext/gettext.inc' (include_path='.$

```

---

### Post by SeijiSensei on 2015-07-31
>     Fri Jul 31 18:18:05.494960 2015] [:error] [pid 9113] [client 117.195.32.143:17426] PHP Fatal error:  require_once(): Failed opening required './libraries/php-gettext/gettext.inc' 
I appears you are missing some required files.  I suspect you didn't install phpmyadmin from the repositories which can lead to all sorts of problems.  You should never install software from anywhere else unless the repositories do not contain what you need.  

See if you can remove the phpmyadmin you installed already, then run
```
sudo apt-get install phpmyadmin
```
You'll see that it drags in a lot of "dependencies" including php-gettext which is probably the source of those missing libraries.

---

### Post by carolog on 2015-07-31
Thanks SeijiSensei. [This solution]("https://www.digitalocean.com/community/questions/issues-with-phpmyadmin-on-nginx-ubuntu-14-04") finally helped. 

Also I installed gettext using,

```
 sudo apt-get install gettext
```

---

