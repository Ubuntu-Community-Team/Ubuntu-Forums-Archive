---
title: "using the PHP mail function on Ubuntu 6 LTS server"
date: 2006-09-15
forum: Server Platforms
---

### Post by nick1 on 2006-09-15
Greetings,

To start, here are my system specs:
Ubuntu 6.06 LTS server
Apache2, MySQL, PHP5
(chose LAMP installation option during install of Ubuntu)
IPKungFu (firewall, all out-bound traffic is allowed)

My mail.php script:

```
<?php $to = 'nobody@example.com'; $subject = 'the subject'; $message = 'hello'; $headers = 'From: [email]webmaster@example.com[/email]' . "\r\n" . 'Reply-To: [email]webmaster@example.com[/email]' . "\r\n" . 'X-Mailer: PHP/' . phpversion(); mail($to, $subject, $message, $headers); ?>
```


I copied the code from [http://us2.php.net/function.mail](http://us2.php.net/function.mail) simply to see if the mail function would work. Of course I replaced 'nobody@example.com' with my real email address.
Now when I run mail.php, I'm not seeing an email in my inbox. I waited for a few more minutes and refreshed my inbox, but still no email. I'm new to the mail() function so I'm not sure what all is required to properly run it. Does the mail() function require a mail server to be installed on my Ubuntu box? I hope not, since all I want to use the mail() function for is to send myself alerts if certain parts of my code fail.

Thank you for your time,

*Nick*

---

### Post by chrisfay on 2006-09-15
You have to uncomment the section in your php.ini file that pertains to the 'sendmail' directive. Depending on where your file is located:

> sudo vi /etc/php5/apache2/php.ini

Then look for the section about half way down that looks like this:

> ; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
;sendmail_path = 

and change to 

> ; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
sendmail_path = /usr/sbin/sendmail -t

Unless you do this, php will not allow mail to be sent using the mail function. This also assumes that you have a functioning mail server on your system.

---

### Post by nick1 on 2006-09-17
Thank you to everyone who replied.  I finally figured it out.  I documented the process I used to get this working and thought I would share it to help others who will one day have the same questions I did about sending email from PHP scripts.  I welcome all comments and suggestions to improve this piece of documentation.  Thanks.

---

Installing Mail Support in PHP

It is possible to send emails from PHP scripts.  Sending emails from PHP scripts can be a confusing topic at first, especially if it is your first time.  To get started, there are two questions you need to answer before proceeding any further:

1.)  Am I using Windows or a flavor of *nix (unix or linux)?
2.)  Am I hosting my website on a third-party server or am I building the server myself?

Sending email from a PHP script under Windows is very different from sending email from a PHP script under *nix.  And whether you are using a third-party webhost to host your website or building the server yourself will determine how much work you need to do to send emails from a PHP script.  In general, less work is required to send emails from a PHP script when you are hosting your website on a third-party server.

A mail server is required to be installed on the PHP server.  Installing a mail server on your PHP server might not sound appealing to you, especially if all you want to do is send yourself alerts that one of your PHP scripts is failing.  There is a work around, however.

The following method describes how to configure PHP to send emails without installing a mail server on your Ubuntu Linux server and assumes you built the server yourself.  The following packages are required:

1.)  php-mail
2.)  php-net-smtp

PHP-mail and PHP-net-SMTP are PEAR modules for PHP.  Install these two packages using either apt-get or Synaptic package manager.  Restart the Apache web server after these two packages are installed.

The following links will teach you the programming syntax that is required to send emails through PHP and provide a sample email script:

[http://pear.php.net/manual/en/package.mail.mail.php](http://pear.php.net/manual/en/package.mail.mail.php)
[http://www.hudzilla.org/phpbook/read.php/15_5_2](http://www.hudzilla.org/phpbook/read.php/15_5_2)
[http://email.about.com/od/emailprogrammingtips/qt/et073006.htm](http://email.about.com/od/emailprogrammingtips/qt/et073006.htm)

---

*Nick*

---

### Post by louisgag on 2007-07-08
If you want to use Perl, you can also install  libmail-sendmail-perl which is supported on the 6.06 LTS ubuntu server.

```
  use Mail::Sendmail;

  %mail = ( To      => 'you@there.com',
            From    => 'me@here.com',
            Message => "This is a very short message"
           );

  sendmail(%mail) or die $Mail::Sendmail::error;

  print "OK. Log says:\n", $Mail::Sendmail::log;
```

---

