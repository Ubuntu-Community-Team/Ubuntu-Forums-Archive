---
title: "Setting up mail on my server"
date: 2013-09-01
forum: Server Platforms
---

### Post by AvengerX9 on 2013-09-01
I havent been around the server or computer for a while, but last time I was I had problems setting up the mail. I forgot what I did so I just wanna remove everything related to mail and start the installation over. Can anyone help a ubuntu newbie with the required commands to perform this task.

From the webmin I can see there are some mail stuff installed under the server tab.

Looks like this

**[&#8211;] Servers**
[LIST]
[*]Apache Webserver
[*]Dovecot IMAP/POP3 Server
[*]MySQL Database Server
[*]ProFTPD Server
[*]Procmail Mail Filter
[*]Read User Mail
[*]SSH Server
[/LIST]


I just need to make it work so my wordpress site can send the confirmation email to the users.

---

### Post by CharlesA on 2013-09-01
Are you just going to be sending mail, or do you also need to receive it?

If you just need to send mail, install postfix and tell it to listen on 127.0.0.1 and you should be good.

---

### Post by AvengerX9 on 2013-09-01
Both. I have removed the modules from webmin and I installed the postfix again using the sudo apt-get postfix. I'm on this guide [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

I also have three domains on different folders on the server, but need only the mail setup for one for now.

---

### Post by CharlesA on 2013-09-01
I used this guide for setting up my mail server.

[https://library.linode.com/email/postfix/postfix2.9.6-dovecot2.0.19-mysql](https://library.linode.com/email/postfix/postfix2.9.6-dovecot2.0.19-mysql)

Granted I am using MariaDB instead of MySQL, but it is a drop-in replacement, so you don't actually need to do anything if you want to use MariaDB instead of MySQL.

---

### Post by AvengerX9 on 2013-09-01
Thanks. I will check that link out and try set it up :)

---

### Post by AvengerX9 on 2013-09-04
Okay I have tried to follow that as good as I can and it seems like Im getting pretty close, but I still have an issue. When I log onto my server from the telnet I got a message "you got mail" but when I try to read it(sudo mail) I get this message 

> No mail for root

I use this to read my mail log 

> grep -i fail /var/log/mail./

and I get this 

> /var/log/mail.log.1:Jun  7 09:01:08 latonia dovecot: pop3-login: Disconnected (auth failed, 1 attempts): user=<te                                [email]st@lyse.net[/email]>, method=PLAIN, rip=218.30.22.119, lip=192.168.0.102
/var/log/mail.log.1:Jun  7 09:02:06 latonia dovecot: pop3-login: Disconnected (auth failed, 1 attempts): user=<te                                [email]st@lyse.net[/email]>, method=PLAIN, rip=218.30.22.119, lip=192.168.0.102
/var/log/mail.log.1:Jun  7 09:02:26 latonia dovecot: pop3-login: Disconnected (auth failed, 1 attempts): user=<te                                [email]st@lyse.net[/email]>, method=PLAIN, rip=218.30.22.119, lip=192.168.0.102
/var/log/mail.log.1:Jun  7 09:02:46 latonia dovecot: pop3-login: Disconnected (auth failed, 1 attempts): user=<te                                [email]st@lyse.net[/email]>, method=PLAIN, rip=218.30.22.119, lip=192.168.0.102
/var/log/mail.log.1:Jun  7 09:03:07 latonia dovecot: pop3-login: Disconnected (auth failed, 1 attempts): user=<te                                [email]st@lyse.net[/email]>, method=PLAIN, rip=218.30.22.119, lip=192.168.0.102
/var/log/mail.log.1:Jun  7 09:03:27 latonia dovecot: pop3-login: Disconnected (auth failed, 1 attempts): user=<te                                [email]ster@lyse.net[/email]>, method=PLAIN, rip=218.30.22.119, lip=192.168.0.102
/var/log/mail.log.1:Jun  7 09:03:47 latonia dovecot: pop3-login: Disconnected (auth failed, 1 attempts): user=<te                                [email]stmail@lyse.net[/email]>, method=PLAIN, rip=218.30.22.119, lip=192.168.0.102
/var/log/mail.log.1:Jun  7 09:04:07 latonia dovecot: pop3-login: Disconnected (auth failed, 1 attempts): user=<tr                                [email]aining@lyse.net[/email]>, method=PLAIN, rip=218.30.22.119, lip=192.168.0.102
/var/log/mail.log.1:Jun  7 09:04:27 latonia dovecot: pop3-login: Disconnected (auth failed, 1 attempts): user=<tr                                [email]aining@lyse.net[/email]>, method=PLAIN, rip=218.30.22.119, lip=192.168.0.102
/var/log/mail.log.1:Jun  7 09:04:47 latonia dovecot: pop3-login: Disconnected (auth failed, 1 attempts): user=<up                                [email]load@lyse.net[/email]>, method=PLAIN, rip=218.30.22.119, lip=192.168.0.102
/var/log/mail.log.1:Jun  7 09:05:06 latonia dovecot: pop3-login: Disconnected (auth failed, 1 attempts): user=<us                                [email]er1@lyse.net[/email]>, method=PLAIN, rip=218.30.22.119, lip=192.168.0.102
/var/log/mail.log.1:Jun  7 09:05:26 latonia dovecot: pop3-login: Disconnected (auth failed, 1 attempts): user=<us                                [email]er@lyse.net[/email]>, method=PLAIN, rip=218.30.22.119, lip=192.168.0.102
/var/log/mail.log.1:Jun  7 09:06:24 latonia dovecot: pop3-login: Disconnected (auth failed, 1 attempts): user=<us                                [email]er@lyse.net[/email]>, method=PLAIN, rip=218.30.22.119, lip=192.168.0.102
/var/log/mail.log.1:Jun  7 09:06:44 latonia dovecot: pop3-login: Disconnected (auth failed, 1 attempts): user=<we                                [email]b1p1@lyse.net[/email]>, method=PLAIN, rip=218.30.22.119, lip=192.168.0.102
/var/log/mail.log.1:Jun  7 09:07:03 latonia dovecot: pop3-login: Disconnected (auth failed, 1 attempts): user=<we                                [email]b@lyse.net[/email]>, method=PLAIN, rip=218.30.22.119, lip=192.168.0.102
/var/log/mail.log.1:Jun  7 09:07:23 latonia dovecot: pop3-login: Disconnected (auth failed, 1 attempts): user=<we                                [email]bmaster@lyse.net[/email]>, method=PLAIN, rip=218.30.22.119, lip=192.168.0.102
/var/log/mail.log.1:Jun  7 09:08:23 latonia dovecot: pop3-login: Disconnected (auth failed, 1 attempts): user=<we                                [email]bmaster@lyse.net[/email]>, method=PLAIN, rip=218.30.22.119, lip=192.168.0.102
/var/log/mail.log.1:Jun  7 09:08:42 latonia dovecot: pop3-login: Disconnected (auth failed, 1 attempts): user=<ww                                [email]w@lyse.net[/email]>, method=PLAIN, rip=218.30.22.119, lip=192.168.0.102
/var/log/mail.log.1:Jun  7 09:09:01 latonia dovecot: pop3-login: Disconnected (auth failed, 1 attempts): user=<@l                                yse.net>, method=PLAIN, rip=218.30.22.119, lip=192.168.0.102


---

### Post by CharlesA on 2013-09-04
Check /var/mail/root

I can't say I've had that experience with my setup, but I also have a .forward file in /root/ that points to my main email address.

---

### Post by AvengerX9 on 2013-09-04
Im starting to consider pay somebody to set it up for me :)

---

### Post by CharlesA on 2013-09-04
Sidenote, those auth errors are strange. Do those email address exist in the database? I did a bunch of testing before deploying my mail server and used simple password to make sure everything was working correctly.

---

### Post by AvengerX9 on 2013-09-04
the email address there @lyse.net is the ISP. I dont know where they come from. I dont have any email address like those

---

### Post by CharlesA on 2013-09-04
Uh... That doesn't make any sense.

The local IP is a private IP and the remote IP is 218.30.22.119. Is that the IP of your server?

It would probably be a good idea to run this tool against your domain:
[http://mxtoolbox.com/SuperTool.aspx](http://mxtoolbox.com/SuperTool.aspx)

---

### Post by AvengerX9 on 2013-09-04
This is my IP 79.161.88.51

---

### Post by CharlesA on 2013-09-04
Well, something is definitely set up wrong.

Could setup a virtual machine and test doing the mail server install before you try it on the production machine?

Personally, if you just want to send out confirmation emails for wordpress or whatever, just install postfix and set it to listen to localhost and be done with it.

---

### Post by AvengerX9 on 2013-09-04
Thanks. Will try do that. Dont really need anything else anyway  :)

---

### Post by vietduong-ma on 2013-10-04
Hi experts,

 I can send email  from my local domain at home using postfix, doveco in Ubuntu. I checked gmail, I received from local domain email at home. I tried to send back to see if I can  receive from local email. gmail messaged that godaddy domain kicked back  to gmail. I am currently purchased domain at godaddy but I didn't buy  email from the domain yet. My friend said I can create it. Therefore, I  got problem. For example, my domain name is **abc.com** where I bought at  godaddy. My email at local at home is using **info@abc.com**. When I reply  back to **info@abc.com**, the message deliver failure from godaddy sent back  right away. How can I solve this method? I am a beginner to setup this thing. I would love to learn from you. Thanks

---

### Post by CharlesA on 2013-10-04
I hope you have setup an MX record so the email server knows what server it is sending mail to for your domain.

---

### Post by nerdtron on 2013-10-05
> **AvengerX9 said:**
> Im starting to consider pay somebody to set it up for me :)

1 click install for the complete mail server with anti virus and spam detection. It also have paid version if you want more features.
[http://www.iredmail.org/install_iredmail_on_ubuntu.html](http://www.iredmail.org/install_iredmail_on_ubuntu.html)

---

