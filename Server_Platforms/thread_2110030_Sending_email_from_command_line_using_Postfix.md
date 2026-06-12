---
title: "Sending email from command line using Postfix"
date: 2013-01-29
forum: Server Platforms
---

### Post by Abu_Dayya on 2013-01-29
I have Ubuntu Server 12.04 installed, and I'm testing sending an email to my gmail account. I have absolutely zero experience with this, and don't know what half the guids online talk about (relay, and stuff). What I did so far, is installing postfix and setting it up as per thid guide

[http://ubuntu-tutorials.com/2008/11/11/relaying-postfix-smtp-via-smtpgmailcom/](http://ubuntu-tutorials.com/2008/11/11/relaying-postfix-smtp-via-smtpgmailcom/)
```

Install the required packages

    sudo aptitude install postfix libsasl2 ca-certificate libsasl2-modules

Configure Postfix

This tutorial will not outline how to configure your postfix server, but we&#8217;ll jump directly to the relayhost section.  You&#8217;ll want to add the following lines to your /etc/postfix/main.cf file:

    relayhost = [smtp.gmail.com]:587
    smtp_sasl_auth_enable = yes
    smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
    smtp_sasl_security_options = noanonymous
    smtp_tls_CAfile = /etc/postfix/cacert.pem
    smtp_use_tls = yes

The above lines are telling Postfix that you want to relay mail through gmail on a specific port, telling it to authenticate, and where to find the username and password.  The last three lines specify the authentication types supported, where the certificate authority file is and that it should use tls.

Define Username and Password

Next we&#8217;ll need to populate the sasl_passwd file.  Create the file /etc/postfix/sasl_passwd with the following contents:

    [smtp.gmail.com]:587    user.name@gmail.com:password

This file should have restrictive permissions and then needs to be translated into a .db that Postfix will read.

    sudo chmod 400 /etc/postfix/sasl_passwd
    sudo postmap /etc/postfix/sasl_passwd

At this point you can restart Postfix and it should work, however it will complain about not being able to authenticate the certificate.  To take care of this issue we&#8217;ll use the ca-certificate package we installed and tell it where it can validate the certificate.
 cat /etc/ssl/certs/Thawte_Premium_Server_CA.pem | sudo tee -a /etc/postfix/cacert.pem

Go ahead and reload postfix (sudo /etc/init.d/postfix reload) and you should be set.

```

Now to test it here is what I'm doing
```
root@ubuntu:/etc/postfix# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 ubuntu ESMTP Postfix (Ubuntu)
ehlo localhost
250-ubuntu
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: myemail@gmail.com
250 2.1.0 Ok
rcpt to: myemail@gmail.com
451 4.3.0 <myemail@gmail.com>: Temporary lookup failure
data
554 5.5.1 Error: no valid recipients
quit
221 2.0.0 Bye
Connection closed by foreign host.
root@ubuntu:/etc/postfix#
   
```

I cannot specify a recepient. Any clues??

Also one I get this working, I want to be able to send an email from within a script. using something like /usr/bin/mail. anyone can give me an example?

Thanks

---

### Post by Abu_Dayya on 2013-02-01
ok so here is what i did. 

In the /etc/postfix/mail.cf i have this line
```
mydestination = gmail.com, ubuntu, localhost.localdomain, localhost
relayhost = [smtp.gmail.com]:587
```

then i created a local user that is the same as my gmail user account. Now when I test with this script

```

oot@ubuntu:/usr/local/nagios# cat /usr/local/nagios/mail-script.sh 
#! /bin/bash

emailRandomNo=$RANDOM

generatedEmailFile=/usr/local/nagios/formatmail.$emailRandomNo

echo "Mime-Version: 1.0" >> $generatedEmailFile
echo "Content-type: text/html; charset=\"iso-8859-1\"" >> $generatedEmailFile
echo "Subject: test" >> $generatedEmailFile
echo "From: myuser@gmail.com" >> $generatedEmailFile
echo "To: myuser@gmail.com" >> $generatedEmailFile
echo "Cc: myuser@gmail.com" >> $generatedEmailFile

echo "<font size=\"2\" face=\"Verdana\">" >> $generatedEmailFile
echo  "<p>test mail</p>" >> $generatedEmailFile
echo "<p>Best Regards,<br>">> $generatedEmailFile

cat $generatedEmailFile | /usr/sbin/sendmail -t 

root@ubuntu:/usr/local/nagios# 


```

When I run ths script, i recieve an email in my local user mailbox
```

root@ubuntu:/usr/local/nagios# su - myuser
No directory, logging in with HOME=/
$ mail
Mail version 8.1.2 01/15/2001.  Type ? for help.
"/var/mail/yousef.dardeer": 76 messages 76 unread
>U  1 myuser@gm  Wed Jan 30 16:45   22/963   test
& quit
root@ubuntu:/usr/local/nagios#

```

How do i get this email to be sent to my actual gmail account. not the localuser mailbox?

---

### Post by Abu_Dayya on 2013-02-05
A few days have apssed. Any help is appreciated guys.

Thanks

---

