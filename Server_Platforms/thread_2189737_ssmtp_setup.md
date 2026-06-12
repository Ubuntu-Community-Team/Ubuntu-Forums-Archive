---
title: "ssmtp setup"
date: 2013-11-23
forum: Server Platforms
---

### Post by mourgolikos on 2013-11-23
I am trying to setup ssmtp on my ubuntu server so I can sent mails from my website.
I installed ssmtp on my server and configured the ```
/etc/ssmtp/ssmtp.conf
``` to the following 


```
# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=MyEmail@gmail.com


# The place where the mail goes. The actual machine name is required no
# MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=smtp.gmail.com:465


AuthUser=MyEmail@gmail.com
AuthPass=MyPass
UseTLS=YES
UseSTARTTLS=YES
AuthMethod=LOGIN


# Where will the mail seem to come from?
rewriteDomain=gmail.com


# The full hostname
hostname=MyEmail@gmail.com


# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
FromLineOverride=YES

```

I have also edited revaliases to
```
[COLOR=#888888][FONT=verdana]root:MyEmail@gmail.com:smtp.gmail.com:465[/FONT][/COLOR]
[COLOR=#888888][FONT=verdana]localusername:MyEmail@gmail.com:smtp.gmail.com:465[/FONT][/COLOR]
```

Then I tried the following line to see if it works

```
To: recipientMail@gmail.com
From:MyEmail@gmail.com
Subject: test

test test



```

and then I pressed Ctrl+D 

after 10 mins or so I gave up waiting realizing that something is going wrong. Can anyone tell what is it?

---

