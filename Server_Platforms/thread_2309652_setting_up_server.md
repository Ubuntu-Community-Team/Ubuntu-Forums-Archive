---
title: "setting up server"
date: 2016-01-12
forum: Server Platforms
---

### Post by wst12 on 2016-01-12
Hi,

I am a newbie to the Ubuntu system and would appreciate your help. I am taking over a project to develop an iPad app but is using Ubuntu as its server. I was given the codes to the server by the previous owner and am trying to set up the server following the README file.

I am currently at the step where it requires me to:

[LIST]
[*]
symlink the .conf file to the nginx folder (sudo ln -s /path/to/project/folder/daf.conf /etc/nginx/sites-enabled) if successful the name will appear in blue after the command: ls /etc/nginx/sites-enabled

I tried doing it but the name appears red. I would appreciate any insights in this. Thank you!
[/LIST]

---

### Post by steeldriver on 2016-01-12
Hello and welcome to the forums

The red color usually indicates a broken symbolic link (i.e. one in which the target does not exist) - did you remember to replace 
```

/path/to/project/folder/

```

by the **actual **path to the appropriate folder? Does the file daf.conf exist there?

---

### Post by wst12 on 2016-01-12
Hi, thank you for your reply. Yes, i did use the path which the daf.conf file exists.

---

### Post by nerdtron on 2016-01-12
what is the output of the following commands:
```
ls -l /etc/nginx/
ls -l /etc/nginx/sites-enabled
ls -l /the/correct/path/to/project/folder/daf.conf 
```

---

### Post by wst12 on 2016-01-12
[SIZE=2][FONT=arial]I have managed to get the file name to turn red now! I am now trying to create a PostgreSQL database and am having problems. It gives me the error peer authentication failed for user. I checked and see if I actually created a database using \l. The database name is listed there. I ran the following commands:[/FONT][/SIZE][COLOR=#000000][FONT=Calibri][FONT=arial][SIZE=2]
[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri][FONT=arial][SIZE=2]sudo -u postgres psql template1
[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri][FONT=arial][SIZE=2]CREATE USER _user_ WITH PASSWORD _password_;[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri][FONT=arial][SIZE=2]CREATE DATABASE _database_;[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri][FONT=arial][SIZE=2]GRANT ALL PRIVILEGES ON DATABASE _database_ TO _user_;[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri][FONT=arial][SIZE=2]\q [/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri][FONT=arial][SIZE=2]
[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri][FONT=arial][SIZE=2]psql -d _database_ -U _user_

Thanks!

[/SIZE][/FONT][/FONT][/COLOR]

---

### Post by SeijiSensei on 2016-01-12
Looks like you're a former MySQL user trying to use the same commands in PostgreSQL. Try this method instead.

First, use "sudo su" to become the root user in Linux, then "su postgres" to become the postgres super user.

Next, create a PG user with your own username by running "createuser -P username" at the prompt. Answer the questions that follow.  A password is optional.  If you don't want one, omit the "-P" switch.  I rarely use DB passwords since most of the time access to my databases is limited to the localhost interface.  To enable network access you need to edit /etc/postgresql/9.3/main/pg_hba.conf.

Finally, exit out of all of this and log in to Linux with your username.  Now run "createdb dbname" to create a database owned by you. 

This is the way I've created users and databases for years.  For the "official" Ubuntu approach read this: [https://help.ubuntu.com/community/PostgreSQL](https://help.ubuntu.com/community/PostgreSQL)

---

### Post by wst12 on 2016-01-13
That worked! Thank you so much!

---

