---
title: "Multiple maria/mysql instances"
date: 2019-01-18
forum: Server Platforms
---

### Post by silverspr on 2019-01-18
Hello
 Ubuntu 16.04.5, Mariadb 10.3.12
 
 I have installed a second instance of mariadb to use as a test platform. The instance is started with mysqld_multi start 2. From the documentation on the mariadb knowledgebase, I understand the only way to connect to the instance via tcp port is to use a host of ‘127.0.0.1’.  [https://mariadb.com/kb/en/library/mysql-command-line-client/](https://mariadb.com/kb/en/library/mysql-command-line-client/)

 How do I use this instance to test against web applications i.e. joomla using 127.0.0.1, joomla only wants to connect using localhost.

 I’m pretty much a novice with mysql and joomla, but surely I’m missing something. In the ‘real world’ businesses must use mysql instances all the time, how do they get around this?

 my.cnf:
 
# MariaDB-specific config file.
# Read by /etc/mysql/my.cnf

[client]
# Default is Latin1, if you need UTF-8 set this (also in server section)
#default-character-set = utf8 

[mysqld1]
plugin-load-add=ha_rocksdb.so
default-storage-engine = rocksdb
port=3306
#
[mysqld2]
plugin-load-add=ha_rocksdb.so
default-storage-engine = rocksdb
# TCP port to make available for clients
port=3308

#  Socket to make available for clients
socket=/mnt/RD3/mariadb/tmp/mysql.sock2
pid-file   = /mnt/RD3/mariadb/tmp/localhost.pid2
# Where MariaDB should store all its data
datadir=/mnt/RD3/mariadb/data
log-error=/mnt/RD3/mariadb/data/error-log.log

# Import all .cnf files from configuration directory
!includedir /etc/mysql/mariadb.conf.d/
 
 
 Your thoughts and help are most welcome.

---

### Post by The Cog on 2019-01-18
I think the normal thing to do would to be run each instance on a different port number. Maybe leave one listening on the default port 3306 and the next one on 3307 etc. Of course the beb  app will have to know which port to  connect to.

---

### Post by silverspr on 2019-01-18
hi, thanks for the reply.  Each instance is listening on its own port.  Joomla however won't connect to the second instance using localhost:3308.  Only 127.0.0.1:3308 works in adminer or mysql client, but joomla doesn't recognize 127.0.0.1. How to get around this?

---

### Post by Tadaen_Sylvermane on 2019-01-19
I don't mean to hijack but I have to ask why this is even a thing? A single instance can run any number of databases depending on hardware. There is zero reason for this I would think. Just seems to over-complicate a simple thing. Simply dump the database when done?

---

### Post by The Cog on 2019-01-19
We have a few machines that run two instances of sqlite at work. Both instances are installed and configured by installer scripts that come with the applications. They don't play nice together so we run them on different port numbers. Editing proprietary installers to force them to share their data, users, permissions and who knows what other customisations would be very hard, and the suppliers would almost certainly refuse to honour their support contracts (although I guess they would still take the money).

---

### Post by SeijiSensei on 2019-01-19
> **silverspr said:**
> hi, thanks for the reply.  Each instance is listening on its own port.  Joomla however won't connect to the second instance using localhost:3308.  Only 127.0.0.1:3308 works in adminer or mysql client, but joomla doesn't recognize 127.0.0.1. How to get around this?

In /etc/hosts, is there a line

```
127.0.0.1     localhost
```

which is usually inserted during installation.  If, for some reason, your server doesn't have that entry, add it and see if Joomla will use "localhost:3308".  

I haven't looked at Joomla in an age, but don't you set the server name and port from the web interface separately rather than using "[noparse]server:port[/noparse]"?

I run two different instances of PostgreSQL at different version levels on separate ports.  Easier than making sure apps I wrote in the past still work with PG 9+.

---

### Post by silverspr on 2019-01-19
hi thanks to everyone for taking the time to help me out with this 
@         SeijiSensei
Yes the virtual host file is configured correctly: I have that entry.  In Joomla you set the db connection using the configuration.php file in the root of the webpage directory.  Joomla doen't like localhost:3308, nor does the [computer name]:3308 work.  Using the mysql client or adminer, I can only connect to the second instance using 127.0.0.1:3308 or by specifying the socket.  Joomla doesn't like either of those options either, it only seems to work with localhost:[port].  It doesn't make sense to me to offer such an option i.e. the ability to have another db instance if its use is hampered by such a design?  Or maybe its just me!!

@Tadaen_Sylvermane
I don't disagree with your observation, but the product is "marketed" as supporting a second or more instance(s).  It wasn't until I put in the effort and configured the second instance that I discovered it didn't behave as the original installed version w/default port 3306.  It just seems odd to me that this would be so?  Not that I'm an IT person, but I was always told not to test in your production environment, which is why I went down this road in the first place.  In the end I will likely do as you suggest: having said that I only just discovered the database engine 'myrocks' which I wanted to test doesn't support foreign keys.  

update, even installing a second instance from binary behaves the same way....I don't get it....

---

### Post by silverspr on 2019-01-30
hello all, thanks again for your help and direction.  After many hours (probably too many!!) I have solved my original post.  I had to purge mariadb from the system including all config files.  I re-installed.  Once reinstalled the 'new' my.cnf file contained more information than from the original install.  One of the lines included an option to bind to 127.0.0.1.  I have left this untouched. Joomla DOES work configured with either localhost or 127.0.0.1.  This was my error, I didn't have a valid user trying to connect to the 127.0.0.1 instance which is why I was getting a connection 'error' when accessing the website.  This was all a result of user error, my apologies for blaming "poor design" with the applications involved.

---

