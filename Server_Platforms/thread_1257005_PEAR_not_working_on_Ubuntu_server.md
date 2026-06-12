---
title: "PEAR not working on Ubuntu server"
date: 2009-09-03
forum: Server Platforms
---

### Post by mjfroggy on 2009-09-03
Hello,

I am trying to setup PEAR so I can send email via php/Pear on my intranet website.

Anyway so I have PEAR installed using the web interface that it comes with and I installed the Mail module

I then tested it and get this error
[php]
Warning: Mail_smtp::include_once(Net/SMTP.php) [mail-smtp.include-once]: failed to open stream: No such file or directory in /var/www/PEAR/Mail/smtp.php on line 311

Warning: Mail_smtp::include_once() [function.include]: Failed opening 'Net/SMTP.php' for inclusion (include_path='.:/var/www/PEAR/') in /var/www/PEAR/Mail/smtp.php on line 311

Fatal error: Class 'Net_SMTP' not found in /var/www/PEAR/Mail/smtp.php on line 312

[/php]

However I confirmed that there is a folder called PEAR as well as Mail (case sensative) in my www dir. and the Mail folder has a file called smtp.php in it. So I am not sure what is causing this error?

I am then trying to use the below script (not sure if this helps)
[php]
<?php
include('PEAR/Mail.php');
/* mail setup recipients, subject etc */
$recipients = "****@c****.com";
$headers["From"] = "****@c***.com";
$headers["To"] = "****@c****.com";
$headers["Subject"] = "User feedback";
$mailmsg = "Hello, This is a test.";
/* SMTP server name, port, user/passwd */
$smtpinfo["host"] = "mail.c****.com";
$smtpinfo["port"] = "25";
$smtpinfo["auth"] = true;
$smtpinfo["username"] = "***@c****.com";
$smtpinfo["password"] = "****";
/* Create the mail object using the Mail::factory method */
$mail_object =& Mail::factory("smtp", $smtpinfo);
/* Ok send mail */
$mail_object->send($recipients, $headers, $mailmsg);
?>
[/php]

---

