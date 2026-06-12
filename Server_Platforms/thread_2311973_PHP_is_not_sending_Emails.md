---
title: "PHP is not sending Emails"
date: 2016-01-31
forum: Server Platforms
---

### Post by PC-2011 on 2016-01-31
I have been trying to get a lamp installation working on my old laptop for going on a week now. Im almost to the point where all the pieces I need for my project are in place except for PHP decided its not going to work with postfix to send emails through gmail. If run the code to send an email I get email sent but no email has been sent according to gmail or received by another gmail. I used [https://devops.profitbricks.com/tutorials/configure-a-postfix-relay-through-gmail-on-ubuntu/](https://devops.profitbricks.com/tutorials/configure-a-postfix-relay-through-gmail-on-ubuntu/) to setup postfix. I don't want to post all the different configuration files since there all long and there are a lot of them so as asked for I will happily supply them.

---

### Post by SeijiSensei on 2016-02-01
Open a terminal on the machine and type:
```

$ telnet gmail-smtp-in.l.google.com smtp

```
You should see
```

Connected to gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP 82si28288453pfn.23 - gsmtp

```
If you cannot connect, your ISP blocks outbound connections to the SMTP port, 25, as an anti-spam measure.  Ask your ISP if there is a relay server you can use.

If you can connect, take a look at /var/log/mail.log and see what errors are reported.

(Hold down Ctrl and hit "]", then enter "quit" to exit telnet.)

---

### Post by PC-2011 on 2016-02-01
So I followed your instructions and got this. I just changed the email used when I posted it for privacy. Everything looks fine to me. It looks like its starting the daemon to run postfix, then reloading the config file. Then loading the message and login information then sends it to google.
```

Feb  1 10:03:21 james-Inspiron-1520 postfix/master[1141]: daemon started -- version 2.11.0, configuration /etc/postfix
Feb  1 10:03:23 james-Inspiron-1520 postfix/master[1141]: reload -- version 2.11.0, configuration /etc/postfix
Feb  1 10:05:33 james-Inspiron-1520 postfix/pickup[1430]: EF1A2C2191: uid=33 from=<www-data>
Feb  1 10:05:33 james-Inspiron-1520 postfix/cleanup[2604]: EF1A2C2191: message-id=<20160201150532.EF1A2C2191@james-Inspiron-1520.localdomain>
Feb  1 10:05:33 james-Inspiron-1520 postfix/qmgr[1431]: EF1A2C2191: from=<www-data@james-Inspiron-1520.localdomain>, size=397, nrcpt=1 (queue active)
Feb  1 10:05:35 james-Inspiron-1520 postfix/smtp[2606]: warning: database /etc/postfix/sasl/sasl_passwd.db is older than source file /etc/postfix/sasl/sasl_passwd
Feb  1 10:05:38 james-Inspiron-1520 postfix/smtp[2606]: EF1A2C2191: to=<#####@gmail.com>, relay=gmail-smtp-in.l.google.com[173.194.196.27]:25, delay=6.5, delays=1.5/3.8/0.95/0.26, dsn=2.0.0, status=sent (250 2.0.0 OK 1454339138 q9si15944204igh.78 - gsmtp)
Feb  1 10:05:38 james-Inspiron-1520 postfix/qmgr[1431]: EF1A2C2191: removed
```

---

### Post by nerdtron on 2016-02-01
Login to the google account that you use and see the sent messages if your emails are sent. Look for any errors/bounced emails that you have tried to send.

---

### Post by PC-2011 on 2016-02-01
Sent folder dose not have any new emails in it. There are also no errors bounced emails.

---

### Post by lisati on 2016-02-01
That looks to me like Gmail has accepted the email. Have a look in your Gmail spam/junk folder, and see what shows up.

---

### Post by SeijiSensei on 2016-02-02
Gmail might not like mail from addresses like [email]www-data@james-Inspiron-1520.locald[/email]omain.  Can't you send these messages from a legitimate domain?

---

### Post by nerdtron on 2016-02-02
Better to test from the bash command line first. If you can send emails from bash, then move on to troubleshoot the php sending problem.

---

### Post by PC-2011 on 2016-02-02
Im trying to use this to develop websites for fun so I don&#8217;t have a domain.

---

### Post by michaelebsch on 2016-02-06
Did you enable SMTP relaying in your gmail account and authorize your device to login to the gmail account? I had issues with one of my dev sites on my server using a gmail account to send emails when I realized that gmail was blocking the login request until I confirmed that the device (server) was allowed to access the account.

---

### Post by PC-2011 on 2016-02-07
So I tried to just configure postfix with this [https://easyengine.io/tutorials/linux/ubuntu-postfix-gmail-smtp/](https://easyengine.io/tutorials/linux/ubuntu-postfix-gmail-smtp/) then I told gmail to allow less secure apps and it worked. If anyone needs some clarifications let me know I would be happy to help.

---

### Post by nerdtron on 2016-02-07
I thought you already enabled that beforehand. But anyway, I've used to relay email alerts using my gmail account before. I hope you won't get blocked because after about a month, my gmail account was closed by google due to possible spamming. It's weird cause I only send email once a day to 3 recipients.

---

