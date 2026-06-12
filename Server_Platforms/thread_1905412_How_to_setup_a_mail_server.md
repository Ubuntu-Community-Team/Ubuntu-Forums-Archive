---
title: "How to setup a mail server"
date: 2012-01-06
forum: Server Platforms
---

### Post by ScottG89 on 2012-01-06
Hey guys, I currently have apache running for my web server and I have php installed. I recently found out that apache cannot send mail through the mail() function in php without other software installed. I was wondering if someone can tell me how to get a mail server up and running. I tried installing postfix and I tested the mail() function and it says it works now, but I don't know how to view the mail to see if it actually came through.

Thank you in advance,
Scott

---

### Post by dazman19 on 2012-01-06
you dont have to set up a mail server on that particular machine. you can use an existing mail server. Perhaps your ISP's email server. Setting up a mail server can be quite a bit of work, because there are lots of security things to be aware of. I generally tend to create a mail account for my web application and send from that. 

I prefer to use phpmailer to send email rather than the mail() function, but both work fine.

[PHP]
<?php
$smtpServer = 'mail.bacon.net.nz'; //set my mail server to this...

$to      = 'nobody@example.com';
$subject = 'the subject';
$message = 'hello';
$headers = 'From: webmaster@example.com' . "\r\n" .
    'Reply-To: webmaster@example.com' . "\r\n" .
    'X-Mailer: PHP/' . phpversion();
ini_set ( "SMTP", $smtpServer );
date_default_timezone_set('America/New_York');

mail($to, $subject, $message, $headers);
?> 
[/PHP]

---

