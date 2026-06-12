---
title: "PHP mail problem - cannot send when used with an HTML form"
date: 2011-10-02
forum: Server Platforms
---

### Post by __PG__ on 2011-10-02
Hello all. Long time lurker first time poster.

I'm writing a web page for the first time. I'm testing in a MacBook 5,3 running Ubuntu 10.04. I have installed apache and php and everything is working fine, until I get around to testing a php form to send mail.

I have configured php to send mail using gmail as a server. I can send mail from the following script titled 'mailform.php' using php at the command line $> php -f mailform.php
```

<?php
$to = "myaddress@yahoo.com";
$subject = "Test mail from PHP";
$message = "Hello! This is a simple email message";
$from = "myaddress@gmail.com";
$headers = "From:" . $from;
echo "Headers = $headers\n";
if(mail($to,$subject,$message,$headers)){
  echo "Mail Sent.\n";
} else {
  echo "Message Failed\n"; 
}
?> 

```However I cannot get php to send mail when used as part of a php form.  A good example of a test from can be found here: [http://apptools.com/phptools/forms/forms1.php](http://apptools.com/phptools/forms/forms1.php)

I have dowloaded and ran the file (lesson1.php), amending the email address as necessary. According to the script the mail is sent (i.e. the mail command executes as 'true' and 'Message Sent' is echoed to the browser). However the email never arrives.

Any suggestions as to where to go from here?

The mail log shows the following when attempting to send mail via a form
```

Oct  2 16:45:56 PagBook sm-mta[3585]: p925juZk003585: from=<www-data@PagBook>, size=525, class=0, nrcpts=1, msgid=<4e87fa57.OnLNLt3lyJjbDMUE%myaddress@gmail.com>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Oct  2 16:45:56 PagBook sendmail[3554]: p925jtEm003554: to=myaddress@yahoo.com, ctladdr=www-data (33/33), delay=00:00:01, xdelay=00:00:00, mailer=relay, pri=30377, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (p925juZk003585 Message accepted for delivery)
Oct  2 16:45:59 PagBook sm-mta[3587]: p925juZk003585: to=<myaddress@yahoo.com>, ctladdr=<www-data@PagBook> (33/33), delay=00:00:03, xdelay=00:00:03, mailer=esmtp, pri=120525, relay=mta5.am0.yahoodns.net. [74.6.136.65], dsn=5.0.0, stat=Service unavailable
Oct  2 16:45:59 PagBook sm-mta[3587]: p925juZk003585: p925jxZk003587: DSN: Service unavailable

```

---

### Post by Ryan Dwyer on 2011-10-02
There's a good chance it's related to not sending the From header. When a From address isn't specified it will use a default address which in your case appears to be www-data@PagBook. The receiving mailserver tries to look up this address for spam detection purposes. It discovers the domain doesn't exist and decides not to deliver the message.

So yeah, add a From header just like your first script and try it again.

---

### Post by SeijiSensei on 2011-10-02
Adding a From header is a good first step, but that alone won't necessarily change the "envelope" From, the From that is sent via SMTP.  To do that requires that the www-data user be "trusted" by the SMTP software.  I don't know how that's handled by sm-mta.

Even that may not be enough if you're on a residential connection.  Yahoo may simply not accept mail from your IP block to reduce the amount of spam it receives from Windows machines that have been turned into spambots by malware. You can test whether your IP address is listed in common spam blacklists [here](http://whatismyipaddress.com/blacklist-check).

---

### Post by __PG__ on 2011-10-03
Copying the $header variable format from mailform.php to lesson1.php has no effect.

The DSN error mentioned in the mail.log is often attributed to problems in /etc/hosts. However this doesn't explain why I can send mail from the command line but not using a web form.

I decided to investigate the php.ini files. In /etc/php5 I have three subdirectories: apache2, cgi and cli.  Each has their own php.ini files. All three files have the same variable for sendmail path:
sendmail_path = /usr/bin/mailx -t

The variable mail.add_x_header=On for all three files.

I've added a log file for each php.ini file. so that the mail.log variable is equal to 
mail.log = /home/username/Web/mail_php_apache.log for the php.ini located in /etc/php5/apache2
mail.log = /home/username/Web/mail_php_cgi.log for the php.ini located in /etc/php5/cgi
mail.log = /home/username/Web/mail_php_cli.log for the php.ini located in /etc/php5/cli

When using $> php -f mailform.php the following is written to ~/Web/mail_php_cli.log
mail() on [/home/username/Web/HTML_test/mailform.php:8]: To: [email]username@yahoo.com[/email] -- Headers: From:username@gmail.com

No mail.log file is created when I'm using the web form coded in lesson1.php.

So I presume this is now an apache/web related issue as to how the php form is being processed.

---

### Post by __PG__ on 2011-10-03
I just found this old ubuntu forums thread : [**PHP Mail won't send but sendmail works **]("http://ubuntuforums.org/showthread.php?t=1058311&page=2")which seems to have similar issues.

I'll work my way through that thread and see if I get any joy.

---

### Post by __PG__ on 2011-10-03
Ok so it's working now.

I had used [this link](http://klenwell.com/is/UbuntuCommandLineGmail) to setup command-line emails using msmtp/mailx and gmail.

There is good information on how to set up msmtp for php use here:

[https://wiki.archlinux.org/index.php/Msmtp](https://wiki.archlinux.org/index.php/Msmtp)

[http://www.jamwaffles.co.uk/tutorials/linux/localmail](http://www.jamwaffles.co.uk/tutorials/linux/localmail)

---

