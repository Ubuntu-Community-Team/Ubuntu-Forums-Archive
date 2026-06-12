---
title: "Postfix &amp; PHP"
date: 2006-01-13
forum: Server Platforms
---

### Post by iluminate on 2006-01-13
Hi !

I am trying to set up a server with Postfix and I am using Apache and PHP.
Now from a PHP script I send an outgoing email but of some reason the email is not delivered.
What is wrong?

In php.ini I have added -
sendmail_path = /usr/sbin/sendmail -t -i

Main.cf looks like this:
```
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = localhost.localdomain
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost.localdomain, localhost.localdomain, localhost
relayhost = smtp.myisp.net
mynetworks = 127.0.0.0/8
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

```

Please I really need help :(

---

### Post by Koybe on 2006-01-13
I think you need to be more descriptive. What's your PHP script, what are you exactly tryning to do. Do you have anything according to the mail you try to send in your log (/var/log/mail.log)?

---

### Post by iluminate on 2006-01-13
Hi and thanks for replying,

I must confess that I am a n00b, both to nix and PHP.
After checking the mail.log I found this -
Jan 13 21:57:58 localhost postfix/sendmail[29391]: fatal: No recipient addresses found in message header

What I did is that I created a simple example like this - 

```
<form action="mailer.php" method="POST">
To: <input type="text" name="to"><br>
From: <input type="text" name="email"><br>
Subject: <input type="text" name="subject"><br>
Message body:<BR>
<textarea rows="10" cols="40" name="message"></textarea><br>
<input type="submit" value="Send your message">
</form>

```

and

```
<?php
mail($to,
	$subject,
	$message,
"From: $email\r\nReply-to: $email\r\n");
?>
	
```

This example I created to check if the function mail is working.
Where did I go wrong?
When using an emailclient the relay smtp-server is working fine - How come?

---

### Post by iluminate on 2006-01-13
This is crazy...
I can not get it to work.
Is there a smart way to test if the settings are correct. I have tried to send an email via telnet to an external adress and it works just fine, but the PHP built in mail function wont work.
Any ideas would be appreciated!

Cheers

---

