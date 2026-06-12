---
title: "php mail() for mere mortals"
date: 2008-11-03
forum: Server Platforms
---

### Post by edpatterson on 2008-11-03
I have searched, read, searched again, installed, uninstalled, reinstalled, changed packages, configured php.ini, checked every error log I could imagine and still can not get php's mail() function to work.

My last attempt was to install exim as a slew of google hits said exim is Ubuntu's preferred sendmail agent.

Here is my test page
```

<?php
  $name="Ed Patterson";
  $email = "edpatterson@email.com";
  $recipient = "edpatterson@email.com";
  $mail_body = "This would be the addition report";
  $subject = "URL added to the everyone list";
  $header = "From: ".$name." <".$email.">\n";
  
  mail($recipient, $subject, $mail_body, $header);
  echo "Mail Sent";
?>

```
my /etc/php5/apache/php.ini file has
```

sendmail_path = /usr/sbin/sendmail

```
Requesting the page from a browser returns
Mail Sent
and finally in the syslog
```

Exim is a Mail Transfer Agent. It is normally called by Mail User Agents, not directly from a shell command line. Options and/or arguments control what it does when called. For a list of options, see the Exim documentation.

```
It simply can not be this complicated. I must have missed a very basic step somewhere.

Ed

---

### Post by Vegan on 2008-11-03
Exim and postfix are MTA programs, and I invoke spamming via sendmail.

Mind you I also have dovecot on the machine too.

---

### Post by cdenley on 2008-11-03
I use postfix. Give that a try
```

sudo apt-get install postfix

```
If you still have problems, check the log
```

tail /var/log/mail.log

```
It could simply be getting blocked as spam based on your dns configuration.
> Exim and postfix are MTA programs, and I invoke spamming via sendmail.
You're a spammer?

---

### Post by edpatterson on 2008-11-05
Well, I installed postfix but I do not think it is what I am looking for. Or perhaps it is not the best tool for what I want to do.

The server is used from proxy filtering. Squid blocks request, sends user to a php page where they may request it. If/When the request it it is added to a MySQL database and the white lists are regenerated. I would like to recieve an email too. I figured this would be a one liner and it is in php, it is getting something/anything to send the message out that is the problem.
```

postfix/master[12314]: fatal: bind 0.0.0.0 port 25: address already in use

```
followd a few minutes later after attempting to send a message via php
```

sm-mat[12651]: NOQUEUE: SYSERR(root): hash map "access": missing map file /etc/mail/access.db: No such file or directory

```
I already have an smtp server that will pass mail for this server if I can figure out how to get it there.

Thanks,
Ed

---

### Post by cdenley on 2008-11-05
Apparently you already have a server running on port 25, so postfix won't start.
```

sudo lsof -i :25

```

---

### Post by edpatterson on 2008-11-12
<much reading, testing has passed>
I have installed postfix and mailx which claimed to have uninstalled sendmail. 'ps aux | grep mail' showed sendmail was still running. I killed the process, accessed my mailtest.php page. It reported success (1). /val/log/mail.err reports no errors. The message was not received by any of the accounts. The email accounts here are of course not the ones I used.
```

<?php
  $to = "ed_patterson@adress1, edpatterson@address2, pattersoned@address3";
  $subject = "Mail from Ubuntu PHP";
  $message = "The message, $subject, was sent to $to\n";
  echo mail($to,$subject,$message)."<br>\n";
  echo "Did it go (this is from Ubuntu)?<br>\n";
 ?>

```
Perplexed I installed XAMPP on a thumbdrive under Windows, configured PHP for my external smtp server, used the same php page and all 3 accounts received the message so I am fairly certain the PHP stuff is right.

I am at a loss where to go next. I tried to find the postfix 'outbox' for lack of a better term and failed. I can only assume the message(s) is stuck some where on my Ubuntu box waiting for something to deliver it.

Ed

---

### Post by CrucifiedEgo on 2008-11-12
you can try sudo postqueue -p to view messages that are queued and waiting to go out.  You can also look at /var/log/mail.log to see if it's reporting anything leaving.

---

### Post by edpatterson on 2008-11-13
Fixed!
I had to edit the php.ini file
[FONT="Courier New"]sendmail_path = /usr/sbin/sendmail -t -i -f [email]servername@domain.com[/email] (space between the -f and address is important)
[/FONT]
Discovered this by reading /var/log/mail.info. Mail was leaving my system from [email]www-data@domain.com[/email]
I also learned that it is a good idea to restart apache after editing the php.ini file...

Thanks to all for the help!
Ed

---

