---
title: "How can I send an email from php application."
date: 2006-03-27
forum: Server Platforms
---

### Post by Bunro on 2006-03-27
What I would like is to be able to send an email from a PHP application. I am working on a test machine as localhost.
I have seen the tread and link to [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)
The question is do I need to install all the described packages and configure them?
Or is there an simple configuration. My goal is only for testing purpose and not for production. 

Regards, Robert

PS. Sorry for the basic question but I am new to the mailserver area.

---

### Post by gborzi on 2006-03-27
I had a similar problem, because I had to know the ip address assigned to my PC at office by dhcp, which changes at every restart. I solved it with a shell script in /etc/init.d . Here is the script, that uses telnet on port 25 to send the message:
[I]#! /bin/sh
#
# local - local settings
SENDER="borzi@ingegneria.unime.it"
SMTP_SERVER="ingegneria.unime.it"
RECIPIENT="gborzi1@alice.it"
MESSAGE_ID=prova
DATE=`date -R`
MESSAGE_BODY=`/sbin/ifconfig eth0`
SUBJECT=informazioni
MAIL_FILE=/tmp/$1~

. /lib/lsb/init-functions

case "$1" in
start)
   log_begin_msg "Sending ipaddress"
   echo "HELO $SENDER"                             >  $MAIL_FILE
   echo "MAIL From: <$SENDER>"                     >> $MAIL_FILE
   echo "RCPT To: <$RECIPIENT>"                    >> $MAIL_FILE
   echo "RCPT To: <$SENDER>"                       >> $MAIL_FILE
   echo "DATA"                                     >> $MAIL_FILE
   echo "Message-ID: $MESSAGE_ID"                  >> $MAIL_FILE
   echo "Date: $DATE"                              >> $MAIL_FILE
   echo "Sender: $SENDER"                          >> $MAIL_FILE
   echo "From: $SENDER"                            >> $MAIL_FILE
   echo "To: $RECIPIENT"                           >> $MAIL_FILE
   echo "Subject: $SUBJECT"                        >> $MAIL_FILE
   echo ""                                         >> $MAIL_FILE
   echo "$MESSAGE_BODY"                            >> $MAIL_FILE
   echo ""                                         >> $MAIL_FILE
   echo "."                                        >> $MAIL_FILE

   cat $MAIL_FILE | telnet $SMTP_SERVER 25
   rm -f $MAIL_FILE
   ;;
   stop)
   ;;
*)
   log_success_msg "Usage: /etc/init.d/local {start|stop}"
   exit 1
esac

exit 0[/I]
it also sends the same email to [email]borzi@ingegneria.unime.it[/email].

---

### Post by Bunro on 2006-03-27
Thanks  Giuseppe for your reaction,

But sorry, I think it is not the answer to my question. Or I didn't understand your answer.

My question is how can I sent email from my php application via postfix. in a simple way.

Regards, Robert

---

### Post by gborzi on 2006-03-27
Hello Bunro,
I don't know php, isn't it a scripting language for the web ? If php can use system commands, you can use telnet to send email through SMTP, and you don't need to use postfix.

---

### Post by Bunro on 2006-03-27
[QUOTE=gborzi]Hello Bunro,
I don't know php, isn't it a scripting language for the web ? If php can use system commands, you can use telnet to send email through SMTP, and you don't need to use postfix.[/QUOTE]

Yes, it is a scripting language for the web (server side scripting language).
But how do I have to setup my system to be able to sent the email. PHP.ini and or postfix configuration?

Sorry, this is not unfamiliar terrain. for me.

Regards, Robert

---

### Post by CrustyDOD on 2006-03-27
Ubuntu default installation comes with the ability to send email from PHP from local server.. Just go to [http://www.php.net/manual/en/function.mail.php](http://www.php.net/manual/en/function.mail.php) and copy and paste an example to PHP file and run it.. Then check your email ;)
Oh, you need to open 25 tcp port in firewall and if it fails, check logs..

---

### Post by Bunro on 2006-03-27
Thanks Crusty DOD for your answer,

But I think I need to set php.ini and possibly also postfix? Postfix is (or may be partly) installed with Apache, PHP and MySQL.
At this moment went I am sending an email from my php application I am not receiving any email.

Do you know where I can find possible log files?

Regards, Robert

---

### Post by fakey1223 on 2006-04-26
To get the php mail() function working, I installed the sendmail package (doing so removed postfix).

---

### Post by LordHunter317 on 2006-04-26
I'll have to say this in every thread, but there is no need to do that.  Postfix is a drop-in replacement for sendmail.

---

