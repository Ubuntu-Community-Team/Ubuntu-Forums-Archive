---
title: "I am having some issue is round cube"
date: 2010-07-02
forum: Server Platforms
---

### Post by samy4linux on 2010-07-02
HI Guys,

  I have installed the Roundcube ,Iam having some error and some clarification.

    The command what is used for installing Mysql in 
   sudo apt-get install mysql-server

CREATE DATABASE roundcubemail;
GRANT ALL PRIVILEGES ON roundcubemail.* TO username@localhost IDENTIFIED BY 'password';
FLUSH PRIVILEGES;
and i have done all the procedures,but the roundcube is not at all fetching the MYSQL in the configuration step and iam getting a error that makesure the database exits or not so i do no what to do.

 My second clarification is that we are giving Auto_user option in the Imap configuration and in the last step it is asking for the user name and password, so there can give my own user name and password for the first login, so that user login can i user like a root login for my roundcube.

   PLEASE GIVE SUGGESTION TO SOLVE THIS ISSUE

  Hi Iam waiting for your valuable reply Please help me in this Issue

---

### Post by scrooge_74 on 2010-09-23
I know, many months latter, I had a similar issue with roundcube not conecting to MySQL.

there is a line in /etc/roundcube/db.inc.php

which requieres your database user and pass

$rcmail_config['db_dsnw'] = 'mysql://admin_user_for_roundcube:_password@localhost/name_of_DB_for_roundcube';

as long as this it not set right you get weird error messages

---

### Post by lisati on 2010-09-23
Moved to "Server Platforms"
> **scrooge_74 said:**
> I know, many months latter, I had a similar issue with roundcube not conecting to MySQL.

there is a line in /etc/roundcube/db.inc.php

which requieres your database user and pass

That can do it, I've experienced similar hiccups when setting things up. Sometimes it's easy to miss steps like this or make a simple typo when following tutorials.

---

