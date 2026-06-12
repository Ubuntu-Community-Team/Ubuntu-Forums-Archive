---
title: "apache2 fails to start"
date: 2010-01-17
forum: Server Platforms
---

### Post by husskii on 2010-01-17
Hi Im hoping someone can help me figure how to resolve this apache2 problem I keep getting, I have installed a debian LAMP server with ispconfig3 and everytime I reboot apache fails to start, I don't know and I have done some research but nothing seems to work, which leads me to reinstall everything from scratch again, which is starting to be a pain, I think I have reinstalled at least 10x or more, and would really love a solution pls...

when ever I reboot I get the following error
```
Starting web server: apache2apache2: Syntax error on line 281 of /etc/apache2/apache2.conf: Syntax error on line 66 of /etc/apache2/sites-enabled/monsterhost.co.cc.vhost: Expected </VirtualHost> but saw </Directory>
 failed!
```
 
I have tried stopping and restarting apache with no success have also creating ```
/etc/apache2/sites-available/www.monsterhost.co.cc
```

with the following text 
```
#
#  Example.com (/etc/apache2/sites-available/www.monsterhost.co.cc)
#
<VirtualHost *>
        ServerAdmin webmaster@monsterhost.co.cc
        ServerName  www.monsterhost.co.cc
        ServerAlias monsterhost.co.cc

        # Indexes + Directory Root.
        DirectoryIndex index.html
        DocumentRoot /home/www/www.monsterhost.co.cc/htdocs/

        # CGI Directory
        ScriptAlias /cgi-bin/ /home/www/www.monsterhost.co.cc/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>


        # Logfiles
        ErrorLog  /home/www/www.monsterhost.co.cc/logs/error.log
        CustomLog /home/www/www.monsterhost.co.cc/logs/access.log combined
</VirtualHost>
```

then I ran ```
a2ensite www.monsterhost.co.cc
```
which said ```
Site www.monsterhost.co.cc already enabled
```

so i tried ```
 /etc/apache2/sites-enabled/www.monsterhost.co.cc
```
and i got a permission denied error
```
-bash: /etc/apache2/sites-enabled/www.monsterhost.co.cc: Permission denied
```

I really hope there is something to fix apache and get it to start, otherwise the setup is a waste of time, and Im hoping it isnt because Ive put a lot of work into it.


if anyone knows how to fix this error
```
Starting web server: apache2apache2: Syntax error on line 281 of /etc/apache2/apache2.conf: Syntax error on line 66 of /etc/apache2/sites-enabled/monsterhost.co.cc.vhost: Expected </VirtualHost> but saw </Directory>
 failed!
```

and get apache to start that would be so great...


Thanks
Husskii

---

### Post by husskii on 2010-01-17
the lines 275-285 in /etc/apache2/apache2.conf  are
```

# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
```

for ```
/etc/apache2/apache2.conf
``` it only goes as far as 282.

and lines 60-70 of /etc/apache2/sites-enabled/monsterhost.co.cc.vhost
is
```
    php_admin_value upload_tmp_dir /var/www/clients/client0/web9/tmp
    php_admin_value session.save_path /var/www/clients/client0/web9/tmp
    php_admin_value open_basedir /var/www/clients/client0/web9/web:/var/www/clients/client0/$

[<Directory /var/www/monsterhost.co.cc/web>
  AllowOverride All
</Directory>
</VirtualHost>



```

also this only goes as far as 67 and the rest of the lines to 71 are blank.

If u like I can post the whole thing if it helps, but ye I have no idea on where to go from here...
could really use the help please..

thanks:confused:

---

### Post by Charlietje on 2010-01-17
start apache by
```
sudo /etc/init.d/apache2 start
```


after that, look in the log files
```
/var/log/syslog
/var/log/apache2/error.log
```

you probably get more info

---

### Post by husskii on 2010-01-17
hi Charlietje

I tried starting apache and again it failed, when I try run the commands to view my error logs I get permission denied.

am I ment to use nano or just run the command on its own...
I am root so not sure why I get permission denied..

Thanks heaps

---

### Post by husskii on 2010-01-17
ok I tried viewing through webmin and this is what I got for ```
/var/log/apache2/error.log
```

```
Fri Jan 15 13:04:04 2010] [error] [client 72.20.40.51] File does not exist: /var/www/proxycheck.txt
[Fri Jan 15 13:04:05 2010] [error] [client 72.20.40.51] client denied by server configuration: /htdocs
[Fri Jan 15 16:15:53 2010] [error] [client 85.190.0.3] client denied by server configuration: /htdocs
[Fri Jan 15 19:31:56 2010] [error] [client 72.20.40.51] File does not exist: /var/www/proxycheck.txt
[Fri Jan 15 19:31:56 2010] [error] [client 72.20.40.51] File does not exist: /usr/local/ispconfig/interface/web/proxycheck.txt
[Fri Jan 15 19:31:56 2010] [error] [client 72.20.40.51] client denied by server configuration: /htdocs
[Fri Jan 15 19:31:56 2010] [error] [client 72.20.40.51] client denied by server configuration: /htdocs
[Fri Jan 15 19:32:00 2010] [error] [client 72.20.40.51] File does not exist: /var/www/proxycheck.txt
[Fri Jan 15 19:32:00 2010] [error] [client 72.20.40.51] File does not exist: /usr/local/ispconfig/interface/web/proxycheck.txt
[Sun Jan 17 14:46:32 2010] [error] [client 10.1.1.1] File does not exist: /var/www/favicon.ico
[Sun Jan 17 14:46:35 2010] [error] [client 10.1.1.1] File does not exist: /var/www/favicon.ico
[Sun Jan 17 14:46:35 2010] [error] [client 10.1.1.1] File does not exist: /var/www/favicon.ico
[Sun Jan 17 23:03:51 2010] [error] [client 72.20.40.51] client denied by server configuration: /htdocs
[Sun Jan 17 23:03:51 2010] [error] [client 72.20.40.51] File does not exist: /usr/local/ispconfig/interface/web/proxycheck.txt
[Sun Jan 17 23:03:52 2010] [error] [client 72.20.40.51] File does not exist: /var/www/proxycheck.txt
[Mon Jan 18 02:02:39 2010] [error] [client 121.55.236.139] client denied by server configuration: /htdocs
[Mon Jan 18 04:37:25 2010] [error] [client 10.1.1.1] File does not exist: /var/www/favicon.ico
[Mon Jan 18 04:37:25 2010] [error] [client 10.1.1.1] File does not exist: /var/www/favicon.ico
[Mon Jan 18 04:37:59 2010] [error] [client 67.218.116.134] File does not exist: /var/www/robots.txt
[Mon Jan 18 04:57:10 2010] [notice] caught SIGTERM, shutting down
```

and for ```
/var/log/syslog
```

```
Jan 18 06:45:01 server1 postfix/smtpd[18677]: disconnect from localhost.localdomain[127.0.0.1]
Jan 18 06:46:01 server1 /USR/SBIN/CRON[18695]: (root) CMD (/usr/local/ispconfig/server/server.sh > /dev/null 2>> /var/log/ispconfig/cron.log)
Jan 18 06:47:01 server1 /USR/SBIN/CRON[18702]: (root) CMD (/usr/local/ispconfig/server/server.sh > /dev/null 2>> /var/log/ispconfig/cron.log)
Jan 18 06:48:01 server1 /USR/SBIN/CRON[18726]: (root) CMD (/usr/local/ispconfig/server/server.sh > /dev/null 2>> /var/log/ispconfig/cron.log)
Jan 18 06:49:01 server1 /USR/SBIN/CRON[18733]: (root) CMD (/usr/local/ispconfig/server/server.sh > /dev/null 2>> /var/log/ispconfig/cron.log)
Jan 18 06:50:01 server1 /USR/SBIN/CRON[18740]: (getmail) CMD (/usr/local/bin/run-getmail.sh > /dev/null 2>> /var/log/ispconfig/cron.log)
Jan 18 06:50:01 server1 /USR/SBIN/CRON[18743]: (root) CMD (/usr/local/ispconfig/server/server.sh > /dev/null 2>> /var/log/ispconfig/cron.log)
Jan 18 06:50:02 server1 pure-ftpd: (?@localhost.localdomain) [INFO] New connection from localhost.localdomain
Jan 18 06:50:02 server1 pure-ftpd: (?@localhost.localdomain) [INFO] Logout.
Jan 18 06:50:02 server1 pop3d: Connection, ip=[::ffff:127.0.0.1]
Jan 18 06:50:02 server1 pop3d: Disconnected, ip=[::ffff:127.0.0.1]
Jan 18 06:50:02 server1 imapd: Connection, ip=[::ffff:127.0.0.1]
Jan 18 06:50:02 server1 imapd: Disconnected, ip=[::ffff:127.0.0.1], time=0
Jan 18 06:50:02 server1 postfix/smtpd[18758]: connect from localhost.localdomain[127.0.0.1]
Jan 18 06:50:02 server1 postfix/smtpd[18758]: lost connection after CONNECT from localhost.localdomain[127.0.0.1]
Jan 18 06:50:02 server1 postfix/smtpd[18758]: disconnect from localhost.localdomain[127.0.0.1]
Jan 18 06:51:01 server1 /USR/SBIN/CRON[18800]: (root) CMD (/usr/local/ispconfig/server/server.sh > /dev/null 2>> /var/log/ispconfig/cron.log)
Jan 18 06:52:01 server1 /USR/SBIN/CRON[18830]: (root) CMD (/usr/local/ispconfig/server/server.sh > /dev/null 2>> /var/log/ispconfig/cron.log)
Jan 18 06:53:01 server1 /USR/SBIN/CRON[18842]: (root) CMD (/usr/local/ispconfig/server/server.sh > /dev/null 2>> /var/log/ispconfig/cron.log)
Jan 18 06:54:01 server1 /USR/SBIN/CRON[18849]: (root) CMD (/usr/local/ispconfig/server/server.sh > /dev/null 2>> /var/log/ispconfig/cron.log)
```


but they don't make much sense to me, Im only new to apache.
I haven't had much of a chance to explore it because after 2 or 3 days when I reboot for any reason, this happens.

---

### Post by husskii on 2010-01-17
I know a whole bunch of files dnt exist but what I dnt know is how that came to be, because then I could try prevent it wen I reinstall next time round.

---

### Post by phrostbyte on 2010-01-17
obviously 

```

[Mon Jan 18 04:57:10 2010] [notice] caught SIGTERM, shutting down

```

Is why apache is failing to start. However, it does not give information on why it's receiving SIGTERM. SIGTERM is usually sent by commands such as *kill*.

---

### Post by husskii on 2010-01-17
is there a way to view the logs for ```
SIGTERM
``` lol
or wat log can i view that might give more details

---

### Post by husskii on 2010-01-17
****NOPE THOUGHT I HAD THE SOLUTION BELOW< BUT APACHE2 STILL FAILS ON SERVER REBOOT*********:'(

ok I think I found the problem with some help from another site, but in case anyone else has this problem this is the error in ```
/etc/apache2/sites-enabled/monsterhost.co.cc.vhost
```

```
    php_admin_value upload_tmp_dir /var/www/clients/client0/web9/tmp
    php_admin_value session.save_path /var/www/clients/client0/web9/tmp
    php_admin_value open_basedir /var/www/clients/client0/web9/web:/var/www/clients/client0/$

[<Directory /var/www/monsterhost.co.cc/web>
  AllowOverride All
</Directory>
</VirtualHost>
```

and this is how it should look, u need to change line 62 (the open_basedir one) to this:

```
php_admin_value open_basedir /var/www/clients/client0/web9/web:/var/www/clients/client0/web9/tmp:/usr/share/php5:/tmp:/usr/share/phpmyadmin
```

but of-course your domain and where it says web9, what ever web numbers your up to..

cheers

---

### Post by Charlietje on 2010-01-18
Can you post your complete virtual host file

---

### Post by husskii on 2010-01-21
hi Charlietje
Thank for offering but its ok I found the problem :)
if you notice in my vhost next to ```
<Directory /var/www/monsterhost.co.cc/web>
```
for some reason I had the symbol [ at the start when it shouldnt of been there :/

cheers

---

