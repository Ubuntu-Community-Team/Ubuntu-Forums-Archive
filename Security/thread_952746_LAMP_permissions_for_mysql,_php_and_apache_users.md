---
title: "LAMP permissions for mysql, php and apache users"
date: 2008-10-19
forum: Security
---

### Post by oi_antz on 2008-10-19
I have LAMP running on Ubuntu desktop in a virtual box, but I'm not sure the best way to set up my LAMP permissions. By default Apache runs as www-data, root owns /var/www, mysql runs as mysql and I run X as antz. 

This means I can't write to /var/www to create new scripts, so I chown it to antz. Then Apache can't execute the scripts so I run Apache as antz, then mysql can't write a file with the command [HTML]SELECT * ... INTO OUTFILE '/var/www/...'[/HTML] not sure how to make mysql run as antz but maybe thats not the right solution anyway ...

I've found a heap of info on how to install the LAMP packages, which is great, but I can't find how to configure permissions so that all these users can access the same files and co-operate like they should. 

Just wondering if someone can tell me the proper way to set up my server? Cheers.

---

### Post by Drezard on 2008-10-19
Use sudo whenever you wana do something? How I set up mine, was I left everything pretty much default (If you look at it, its obsure as hell, but in theory its pretty much default).

First off I create a directory in /home/myusername/ called php/scripts/ I have a pretty much copy of my /var/www directory in there. I edit all the scripts in there then I do a "sudo cp /home/myusername/php/scripts/* /var/www" whenever I make updates. That way if I accidently do a rm /var/www/mybigscript.php I can just copy it over from my home again :P

Next, whenever you make changes to Apache, run "sudo /etc/init.d/apache2 restart" and just run things as sudo like that.  

In theory it should all work but give that a go and post problems :-) 

Daniel

---

### Post by oi_antz on 2008-10-19
Hi Daniel, thanks for your suggestion.

I have set up a new virtual box to test your theory, left all permissions as they are after installing the packages. I created the following file in /home/antz/phpscripts/select_into_outfile.php and sudo cp'd it to /var/www/select_into_outfile.php:

[PHP]<?php
$conn = mysql_connect('localhost', 'root', '***secret***') or die('error connecting to db');
mysql_select_db('test_database', $conn) or die('error selecting db');
mysql_query("SELECT * FROM test_table INTO OUTFILE '/var/www/output.txt'") or die(mysql_error($conn));
die('done');
?>[/PHP]

Running it produces this error:

```
Can't create/write to file '/var/www/output.txt' (Errcode: 13)
```

... www is owned by root and mysql is running as mysql, not as root, so it cannot write to the web directory as is sometimes required.

---

### Post by Drezard on 2008-10-19
Is that the script that gives you that error? or running the cp?

If its the cp you may need to add sudo to the start of that cp command. Basically since root owns that directory u need root permissions to write to it so, sudo cp... will give cp root permissions. 

Give that ago.

Return with results :)

Daniel

EDIT: woops... sorry didn't see that it was an mysql error. Can i ask why you want to save the output to a web viewable directory? My only idea is creating a group called webusers or webserver then putting mysql, root and whoever elses needs access to /var/www in that group then run:

[QUOTE]

chgrp webserver /var/www
chown g+rwx webserver /var/www

That should fix that problem.

---

### Post by oi_antz on 2008-10-19
> 
Can i ask why you want to save the output to a web viewable directory?

Yeah, its not necessarily going to be a public directory. When I develop sites, most of my files (classes, logs, templates etc) go outside the public directory. 

I'm planning to use Ubuntu's rising star: rapache. My future structure will look more like this:

/var/www/example.com/www/
/var/www/example.com/backups/

Where the first directory ./example.com/www/ is the public folder and ./example.com/backups/ is the backup folder (still within the ftp/apache/mysql scope, but outside the public folder). A cron PHP service will backup the critical tables by gz'ing the output of a "select into outfile" command.

By the way, this works naturally on all decent hosting plans, just I can't seem to get it working on my LAMP and I'm wondering how it is done so I can test projects in my dev environment before going live.

---

### Post by cariboo on 2008-10-20
Can you actually connect to mysql in a  terminal?, From your output above it doesn't seem to be accepting your password.

Jim

---

### Post by Drezard on 2008-10-20
It is connecting or else PHP would throw a fatal error...

---

### Post by oi_antz on 2008-10-20
yes, its definitely getting to line 4 and throwing a hissy about the linux user permissions - mysql does not have write permission to /var/www

---

### Post by Drezard on 2008-10-20
Did you check out my last idea?

---

### Post by oi_antz on 2008-10-20
> 
chgrp webserver /var/www
chown g+rwx webserver /var/www


sudo chgrp happens without error, but does not allow mysql to write the file.
sudo chown g+rwx webserver /var/www reports error: "Invalid user: `g+rwx'"

I showed a bit of intuition though: 

sudo chown mysql /var/www

Now the folder /var/www is owned by mysql and the owner is permitted to read and write. I am still getting the same error from running that command:

Can't create/write to file '/var/www/output.txt' (Errcode: 13) 

Running the command from mysql command line as root does not work either, and I have checked that the mysql root user has in fact got file permissions ...

---

### Post by Drezard on 2008-10-21
sorry about that. Its not chown its chmod....

---

