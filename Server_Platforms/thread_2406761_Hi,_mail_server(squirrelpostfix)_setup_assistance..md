---
title: "Hi, mail server(squirrel/postfix) setup assistance."
date: 2018-11-25
forum: Server Platforms
---

### Post by tjv001 on 2018-11-25
Hi
Can i pay somebody to install a mail server on my Ubuntu server? I think its called squirrel?! I basically want someone to remotely to set it up or provide reasonably simple stages to do it by myself. Ive tried postfix and its complex. 
Thanks.
Tim.

---

### Post by garye on 2018-11-25
Tim, there are some easy to follow instructions here.... [https://www.tecmint.com/setup-postfix-mail-server-in-ubuntu-debian/](https://www.tecmint.com/setup-postfix-mail-server-in-ubuntu-debian/)

Gary

---

### Post by tjv001 on 2018-11-26
Great many thanks! Unfortunately I get this error: 


godzukee@ubuntu18:~$ sudo apt-get install apache2 php5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package php5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Tim.

---

### Post by darkod on 2018-11-26
Ubuntu 18.04 comes with PHP 7 instead of PHP 5. That is why package php5 is not found in the default repositories.

Also, as far as I know, Squirrel Mail is only a webmail client. That is an additional part on the mail server that allows webmail capabilities.

For a mail server to work you need at least two necessary components:
Mail Transport Agent (MTA): usually used is postfix
Mail Delivery Agent (MDA): usually used is dovecot

Installing Squirrel does not mean you can avoid installing Postfix.

---

### Post by tjv001 on 2018-11-26
Thanks for the reply. I still cant install using php7.
Heres the details if you can help.
:
oot@ubuntu18:/home/godzukee# sudo apt-get install apache2 PHP7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package PHP7
root@ubuntu18:/home/godzukee# 


regards
Tim.

---

### Post by howefield on 2018-11-26
The package won't be named PHP7, that's why it's unable to locate it. Try simply php or php7

---

### Post by tjv001 on 2018-11-26
Cool. Thanks. It worked ! But the package configuration gui doesn't appear automatically to continue with the installation.
Can you help with this?
Tim.

I get the following error:

 ```
sudo apt-get install dovecot-imapd dovecot- pop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'dovecot' is not installed, so not removed
E: Unable to locate package pop
root@ubuntu18:/home/godzukee# sudo apt-get install dovecot-imapd dovecot- pop3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'dovecot' is not installed, so not removed
E: Unable to locate package pop3
```

:confused: Any ideas?
Tim.

---

### Post by SeijiSensei on 2018-11-27
There's a space between "dovecot-" and "pop". The bash parser interprets those as separate arguments to apt.

---

### Post by tjv001 on 2018-11-28
<Hi, thanks for the reply This is what i typed in:

 sudo apt-get install dovecot-imapd dovecot - pop (and tried pop 3)

I get this error message:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dovecot is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'dovecot' has no installation candidate
E: Unable to locate package pop

  Is any one able to help with this?

Hope you can help.
Regards
Tim.

---

### Post by SeijiSensei on 2018-11-28
Again there appears to be a space in "dovecot- pop".

---

### Post by bluexmas on 2018-11-28
@initiator - are you aiming to build a production mailserver, or it's just for learning purposes? because the procedure above is quite old and incomplete. a production mailserver is not a trivial task at all.

---

### Post by xubuntu84 on 2018-11-28
> **bluexmas said:**
> @initiator - are you aiming to build a production mailserver, or it's just for learning purposes? because the procedure above is quite old and incomplete. a production mailserver is not a trivial task at all.

What bluexmas said... a production mail server is not trivial. Speaking from the basis of running one for ~15K users, it's time consuming if you don't have proper filtering and automation built into the workflow. If you are just playing around, have fun! Otherwise, have a look at [iRedMail]("https://www.iredmail.org/"). It does a somewhat decent job of getting you all the components you need to run a mail server - including the webmail client. Do note that they request you have a fresh server to begin the installation, and you should be somewhat familiar with setting the hostname of your system and what to set it to. 

Squirrelmail is a very "slimmed down" front end (read: antiquated). Roundcube is a bit better, and it's what comes with iRedMail.

If this is for production, I believe they offer paid-for services to help you out. Hopefully this partially answers your original question.

Now, to address a couple of your posts. 
1. It's best to post code using the CODE brackets (see menu, looks like #).
2. As pointed out, the command line is case-sensitive. Therefore, PHP7 is not the same as php7.
3. If you see apt-get in some online tutorial, it will likely work, but it should be an immediate flag that the article is old. apt is sufficient nowadays. apt-get is retained in current versions, but not necessary. For example:
```
sudo apt install postfix
``` is sufficient.
4. The following are not the same:
```

dovecot- pop
dovecot - pop
dovecot-pop3d

```
please be aware that you are entering what is intended, not just copy/paste. 
5. I haven't followed this article, but if you're playing around, give it a shot: [Dovecot Server Guide]("https://help.ubuntu.com/lts/serverguide/dovecot-server.html.en")

Good Luck!

---

### Post by bluexmas on 2018-11-29
In addition to what xubuntu84 said, for a production server you would need:
- postfix
- dovecot
- amavis-new
- spamassasin
- clamav
- roundcube
- opendkim
- dcc
- apache (or nginx) + php + mysql

- a good recipe to install and configure all components so they talk to each other properly

- access to dns managemnt to set up SPF and DKIM records
- posibility to set up reverse dns
- check to be sure that the mail server ip is not blacklisted
- get in touch with microsoft support :) (they usually block ips sending mail to their outlook.com)

As mentioned above, iRedMail is a very good alternative to ease the pain of configurations for different server components.

After you have the mailserver up and running, the dance begins: you need to maintain it updated and secure, check it periodically and write as many automatic maintenance tasks for it as possible, depending of the needs. It's really not an install-and-forget thing.

---

### Post by tjv001 on 2018-11-30
HI,
Can anyone suggest further troubleshooting tips? It would be very appreciated!
regards,
Tim.

---

### Post by SeijiSensei on 2018-11-30
As everyone has said, setting up a production mail server is not for the faint of heart.  What specific software are you using and what specific problems do you have?  Asking for "troubleshooting tips" tells us nothing.

---

### Post by tjv001 on 2018-12-06
Thank you everyone for replying I haven't checked my PC for a while and I have missed all of your advice. Ill run through all of your suggestions now and reply when finished.
):P

Just for learning and experimenting!

Just for fun!!not production environment

---

### Post by tjv001 on 2018-12-06
Hi

Ive abandonned postfix and squirrel and im setting up  iRedmail instead. I get to the following stage:


Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
+OK Dovecot ready

I downloaded Roundcube and extracted it on my windows 10 machine. As I'm new to this how do i
install it   on windows 10?
Thank you.

---

