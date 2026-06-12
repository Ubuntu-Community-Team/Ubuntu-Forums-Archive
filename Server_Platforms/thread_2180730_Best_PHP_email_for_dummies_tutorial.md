---
title: "Best PHP email for dummies tutorial?"
date: 2013-10-14
forum: Server Platforms
---

### Post by aysiu on 2013-10-14
I'm setting up a small Ubuntu LAMP server, and all the normal web portions work just fine. I got FTP up and running. I can SSH in okay. All my PHP code is good. I'm feeling pretty good about myself for being able to get this up and running.

The big snag I've run into is sending email via PHP.

I've done a lot of research. I've tried PHPMailer and SSMTP. I don't want the Ubuntu server to be a mail server. I'd just like to send emails via SMTP (using Gmail or something else).

I seem to get stuck at odd places (SSMTP can send via root on the command-line but not via a regular user or via PHP, and libphpmailer seems to just not work at all).

Does anyone have recommended links to a "send email via PHP on a Ubuntu server without making the server itself an email server" for dummies tutorial? And when I say **"for dummies"** (no assumptions--real step by step), I really mean it. I'm not a server expert. I can do some fiddling on the command line to *nano* edit files or *chmod* permissions, but really assume I know almost nothing.

Any help is much appreciated. Thanks in advance.

---

### Post by SeijiSensei on 2013-10-14
First things first.  Are you trying to send mail to remote servers, or just send it internally?  Many ISPs block outbound connections on port 25 to stop spam from customers with hijacked computers that have been turned into spambots.  You can test this by running "telnet gmail-smtp-in.l.google.com 25" from the command prompt?  If you can't connect, you need to talk to your ISP.

If that's not the problem, I would just install [Postfix]("https://help.ubuntu.com/community/Postfix").  PHP will talk directly to that over the localhost interface and let Postfix determine how to deliver your messages. The default installation should be all you need.  You shouldn't need to configure much of anything.

---

### Post by aysiu on 2013-10-14
As far as I know, Postfix actually sets up your Ubuntu server as a mail server. That's not what I wanted to do.

I did manage to figure it out eventually.

After install the *ssmtp*, I edited the /etc/ssmtp/ssmtp.config file as follows: ```
root=username@domain.com
mailhub=mail.authsmtp.com:25
rewriteDomain=domain.com
hostname=domain.com
FromLineOverride=YES
AuthUser=authsmtpusername
AuthPass=authsmtppassword
UseSTARTTLS=NO

``` edited the /etc/php5/apache2/php.ini file to include this line ```
sendmail_path=/usr/sbin/ssmtp -t -i
``` and then restarted the Apache service ```
sudo service apache2 restart
``` The only thing is that originally, because there's a password in the *ssmtp* config, I made the config file chmod 600 so only root could read it. I even tried adding *www-data* to the mail group, but that just didn't fly. Ultimately, it worked only when I chmoded the *ssmtp* file to 664, but should I be worried about that? The *4* part applies to only logged-in users, right?

---

### Post by pqwoerituytrueiwoq on 2013-10-14
i have used php mailer, to send emails via a email service like gmail
[https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/blob/master/email.php](https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/blob/master/email.php)
this is what the user fills out to use it
[[img]http://www.zimagez.com/miniature/screenshot-10142013-043523pm.php[/img]](http://www.zimagez.com/zimage/screenshot-10142013-043523pm.php)

---

### Post by CharlesA on 2013-10-14
> **aysiu said:**
> Ultimately, it worked only when I chmoded the *ssmtp* file to 664, but should I be worried about that? The *4* part applies to only logged-in users, right?

It should be "ok" but I prefer to not have passwords stored in clear text, especially if they are being used for web services.

With that being said, I usually just run postfix and use it as a relay if I need to send mail out from my web server. I know that isn't really what you want, but you can set postfix up in such a way that it will only relay for localhost and only listen to localhost, so it isn't exposed external connections.

---

### Post by aysiu on 2013-10-15
I'm okay with the password in plain text for now. Thanks, CharlesA.

---

