---
title: "FTP issues"
date: 2006-04-27
forum: Server Platforms
---

### Post by xoppaw on 2006-04-27
Hi,
I have set up a home server running breezy badger, apache, php, mysql, and vsftpd.  Now that I have all this set up I can't get the ftp to work properly.  I can connect to the ftp server just fine, as well as browse the entire file structure, but I'm not able to upload any files to the server.  I have set all of my permissions using the chmod -R 777 as well as making myself owner of the files with chown -R maddox.  When I do a ls -l :

drwxrwxrwx  2 maddox root   4096 2006-04-16 13:41 apache2-default
-rwxrwxrwx  1 maddox root    387 2006-04-20 16:31 index.html
-rwxrwxrwx  1 maddox root 505475 2006-04-16 15:19 latest.tar.gz
-rwxrwxrwx  1 maddox root     21 2006-04-16 14:06 testphp.php
drwxrwxrwx  5 maddox 1011   4096 2006-04-16 15:28 wordpress

I am fairly new to linux and am not running any sort of GUI on this system, so help with command line is what I'm looking for.  

Any suggestions are appreciated. 


xoppaw   ](*,)

---

### Post by hagen00 on 2006-04-28
First of all, making everything 777 will not sort out your problems. For example, your php or html pages don't need to be 777. 644 is absolutely fine. Read up on man chmod if you don't know what 644 is. Also making your folders that are accessible from the web world writable when they don't need to is a security risk. 

If you can say you can actually log into your ftp server, check the following things. 

1. The folder that you want to upload to needs to be owned by the user you log in as (Unless of course it's 777 - which is not great).
2. in /etc/vsftpd.conf you need to have write_enable=YES. Also look in that conf file to see if there is anything else you want to change i.e. allow anon logins or uploads, only allow your username to log in etc. All that can be changed in the conf file. Be sure to restart the ftp server after making changes. sudo /etc/init.d/vsftpd restart

HTH

H

---

### Post by xoppaw on 2006-04-28
Thanks alot, I needed to enable the writing in my ftp program.  I knew it would be something simple.
Thanks Again,
xoppaw

---

### Post by hagen00 on 2006-04-28
Great! Glad to help 8)

---

