---
title: "PhpMyAdmin on Ubuntu Server 10.04: Strange configuration issues"
date: 2011-01-26
forum: Server Platforms
---

### Post by blackdragon5040 on 2011-01-26
Hello!

***My situation***

I recently installed Ubuntu 10.04 LTS Server on a virtual machine. I installed apache2, php and mysql-server. Several vhosts I sat up are running fine and I can also connect to the MySQL server using the mysql command-line client.

I now want to setup PhpMyAdmin to allow the vhosts owners to administrate their DBs. I installed the package using:

```
apt-get install phpmyadmin
```

I answered the questions and accepted the creation of the phpmyadmin database. The install finished successfully.

I did a small modification to the main website vhost to access it easily:

```
Alias /phpmyadmin /usr/share/phpmyadmin
```

I can now access the interface and login with my root user.

***My problem***

The problem is that on the bottom it says that I need to add a blowfish_secret to the server configuration. I've done it once in Fedora but here it's different. I tried to add it at the end of the **/etc/phpmyadmin/config.inc.php** and to reload apache and clear the browser cache but it had absolutely no effect (the message is still here). I also noticed several other files :

[LIST]
[*]**/etc/phpmyadmin/config-db.php** (apparently contains config needed to access the phpmyadmin database)
[*]**/var/lib/phpmyadmin/config.inc.php** (empty!?)
[*]**/var/lib/phpmyadmin/blowfish_secret.inc.php** (contains a correct blowfish_secret config line and was already there from the beginning)
[/LIST]

I don't know where to do the blowfish configuration. Could someone explain in details or give a link about the configuration layout of phpmyadmin on Ubuntu 10.04 ?

I also have a second problem which is probably related. It says on the bottom that some features are disabled. I read somewhere that this line should be added:

```
$cfg['Servers'][$i]['tracking'] = 'pma_tracking';
```

but I don't know where to put it. Again, it has no effect when put in **/etc/phpmyadmin/config.inc.php**.

I can provide the files if needed. Please just ask what you need.

PS: The default installation works like a charm on my Ubuntu Desktop 10.10 laptop. No error messages and warning on the web interface.

Thanks!

---

### Post by ricbax on 2011-03-06
Same issues on Ubuntu Server 10.10. I have been at this all weekend.

---

