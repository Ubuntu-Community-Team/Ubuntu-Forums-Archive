---
title: "Ubuntu Server Issue"
date: 2015-12-30
forum: Server Platforms
---

### Post by Sourav_Saha on 2015-12-30
I am very new in ubantu 14.04.2, Today I build a LAMP server . [http://labriskassess.com/](http://labriskassess.com/) is showing php page. but [http://labriskassess.com/info/info.php](http://labriskassess.com/info/info.php) showing blank page.

Also [http://labriskassess.com/info/h.php](http://labriskassess.com/info/h.php) is giving error 500

Please help me to resolve this issue.

---

### Post by brian-mccumber on 2015-12-30
Well at [http://labriskassess.com/info/h.php](http://labriskassess.com/info/h.php) I am getting hello world echoed to the browser. I could probably help with info.php if I could see the code for it. Can you post your code from info.php using the  tags here or at [http://pastebin.com](http://pastebin.com) ? I could use view page source but it will only display the html code not the php.

---

### Post by brian-mccumber on 2015-12-30
Wait, it showed me the code on your page since your opening php tag is missing the php.

```

[COLOR=#282B2D][FONT=monospace]<?php
[/FONT][/COLOR]    // Show all information, defaults to INFO_ALL
    phpinfo();
?>

```[COLOR=#222222]

[FONT=Verdana]The opening tag needs the php behind the ? It tells the server that php code is coming otherwise it could be xml or something unless you have turned on short tags in your php.ini file which is not recommended.[/FONT]

[/COLOR]http://php.net/manual/en/language.basic-syntax.phptags.php

---

### Post by Sourav_Saha on 2015-12-31
Thanks a bunch Brian, you saved my day.

If I ask one more question, I wanted to enable remote access mysql ubuntu 14.04

When I run this command:
[COLOR=#373E4D][FONT=helvetica]GRANT  ALTER, ALTER ROUTINE, CREATE, CREATE ROUTINE, CREATE TEMPORARY TABLES, CREATE VIEW, DELETE, DROP, EVENT, EXECUTE, INDEX, INSERT, LOCK TABLES, REFERENCES, SELECT, SHOW VIEW, TRIGGER, UPDATE ON  `labriskassesscess`.* TO 'root'@'labriskassess' WITH GRANT OPTION

Getting this error "[/FONT][/COLOR][COLOR=#373E4D][FONT=helvetica]Access denied for user 'root'@'%' to database 'labriskassesscess'"[/FONT][/COLOR]

---

### Post by brian-mccumber on 2015-12-31
Is 'root'@'labriskassess' your Ubuntu root user? If so you need to create a MySQL user and give it those permissions then log in using a MySQL user not your Ubuntu user account. Your MySQL user will only be one word. You could install MySQL Workbench and it would probably make things a little easier on you.

[https://dev.mysql.com/doc/workbench/en/](https://dev.mysql.com/doc/workbench/en/)

---

### Post by SeijiSensei on 2015-12-31
It's also possible that your root user is 'root'@'localhost' rather than 'root'@'labriskassess'.

One of the reasons I prefer PostgreSQL is that its methods for managing users and access are much simpler than MySQL's.

---

### Post by Sourav_Saha on 2016-01-05
[COLOR=#373E4D][FONT=helvetica]Thanks a ton Brian and [/FONT][/COLOR]SeijiSensei...fixed it...Yay :p Everyday learning new things here...that's magical !!! \\:D/[COLOR=#373E4D][FONT=helvetica]


How can I open port 465 to send email using gmail smtp from ubantu 14.04?

[/FONT][/COLOR]When I run the command 'sudo ufw allow 465" 

It replies with "port status close"

---

### Post by Tapas_Das on 2016-01-05
We are getting the error "Expected response code 250 but got code "535", with message "535-5.7.8 Username and Password not accepted. Learn more at535 5.7.8 [https://support.google.com/mail/answer/14257](https://support.google.com/mail/answer/14257) ke10sm89667687wjb.3 - gsmtp"

---

### Post by mastablasta on 2016-01-05
> **Sourav_Saha said:**
> [COLOR=#373e4d][FONT=helvetica]
How can I open port 465 to send email using gmail smtp from ubantu 14.04?

[/FONT][/COLOR]When I run the command 'sudo ufw allow 465" 

It replies with "port status close"

you do not need to open the port to send a message, you only need to open it to offer remote access to a service.

if oyu just need it to send messages (but not receive) then you can use sSMTP: [https://wiki.debian.org/sSMTP](https://wiki.debian.org/sSMTP)

---

### Post by Sourav_Saha on 2016-02-10
I have enabled SFTP in my ubuntu server but not able to upload files via FTP. I have set the permission to 777. But still the problem persists.

---

### Post by SeijiSensei on 2016-02-10
SFTP does not support connections from plain-text FTP clients over port 21.  It uses the SSH port, 22.  You'll need a SFTP client.  Most Ubuntu file browsers like Nautilus and Dolphin support sftp:// URLs to connect with.  From Windows, use the program called WinSCP.

---

### Post by mastablasta on 2016-02-12
also Filezilla for sFTP - works well in Windows as well as Linux.

---

