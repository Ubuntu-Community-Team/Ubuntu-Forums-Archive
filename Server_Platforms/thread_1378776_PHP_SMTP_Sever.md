---
title: "PHP SMTP Sever"
date: 2010-01-11
forum: Server Platforms
---

### Post by Firestom on 2010-01-11
Hello!

In a PHP script, I want to use the mail() function to send an email confirmation upon sign-up. I have installed sendmail after installing PHP5, so I reinstalled it afterwards.

I'm running LAMP on Ubuntu 9.10 Desktop with Gnome.

In a simple test, I'm trying to send an email to myself, but it won't work: Here is the script I tried:
[PHP]<?php

$name = "Firestom";
$email = "email@adress.com";
$recipient = "MyRealEmail@emailadress.com";
$mail_body = "This is a testing mail";
$subject = "Test from PHP server";
$header = "From: ". $name . " <" . $email . ">\r\n";

mail($recipient, $subject, $mail_body, $header);
?>[/PHP]

---

