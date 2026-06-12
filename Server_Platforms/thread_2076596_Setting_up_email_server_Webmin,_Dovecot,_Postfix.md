---
title: "Setting up email server: Webmin, Dovecot, Postfix"
date: 2012-10-26
forum: Server Platforms
---

### Post by AvengerX9 on 2012-10-26
I need some help again with the mail server setup. I have managed to get the server to send email from the website, but I would like to setup some mail accounts to receive mail too.

I'm using Webmin, Dovecot, Postfix and Squirrelmail. I have installed those, but when I try to login to one of the email accounts from Squirrelmail I get this error.

> ERROR: Connection dropped by IMAP server.

and when I try to send an email to this account I get this

> 
Delivery to the following recipient failed permanently:

     [email]xxxxxx@xxxxxxxxx.no[/email]

Technical details of permanent failure:
DNS Error: DNS server returned answer with no data

----- Original message -----

DKIM-Signature: v=1; a=rsa-sha256; c=relaxed/relaxed;
        d=gmail.com; s=20120113;
        h=mime-version:date:message-id:subject:from:to:content-type;
        bh=LFpSKFKIibp3cVi4hQa9IHbBMXFpSRYzO50kJdeIFBc=;
        b=F5d2ZZjaOyzqOeX5Swgmlo/b7AAS5Mo6VXypMOhxYXNzYio0pIN7YwMrj3aDrTG34A
         HEE05UyTyKdpv/OerLVE5DFLAp3NlNrs/BLVcuyB9Q8vYb5mBmwQoyHm38jI6RxN4ba2
         mypd7OxzCoX1qf6CzNCBMXNQEKi2e8bXKVC9BA7xqTnwrj0EVkc+T/i7qkgoyftpFKZ/
         iiXxCRCW5f2hTVQL3OPWdoXK2Kqj108Y1sBgS+eI9Q4nKSGucm5/Lg9S1qSa8f8W83Ut
         w5n/TFdkLfHGQgPl9w4iLyuD0cLcyJSGtCEUkBBGCDR1aG+iUWdpka7fFtg8mF8iWw7a
         Ui6w==
MIME-Version: 1.0
Received: by 10.68.213.6 with SMTP id no6mr30716010pbc.113.1351260582915; Fri,
 26 Oct 2012 07:09:42 -0700 (PDT)
Received: by 10.66.75.136 with HTTP; Fri, 26 Oct 2012 07:09:42 -0700 (PDT)
Date: Fri, 26 Oct 2012 16:09:42 +0200
Message-ID: <CALtvZM9SnYOgPfzNKNPUkhfn+qgosd6T-o0Mz-ySORsRE-iGdA@mail.gmail.com>
Subject: Hello there
From: My Name Here <my.name@gmail.com>
To: [email]xxxxx@xxxxxxx.no[/email]
Content-Type: multipart/alternative; boundary=e89a8fb208380b2e3504ccf6df44



Hope you can help :) Thanks for reading!

/Roger

---

### Post by AvengerX9 on 2012-10-26
update> I can login to squirrelmail and send emails, but I cannot send to my email address. Then I get the error above

---

### Post by AvengerX9 on 2012-10-26
Update> All errors are gone AFAIK. When I send to my email from my gmail account the mail never hits my inbox so what is going on ?

I don't get any errors from google as I used too and there is nothing in the mail.log file.

I guess there might be something with my MX record, it looks like this

> mydomain.com - 1h - MX - 10 - mail.mydomain.com

---

### Post by confusedstingray on 2012-10-28
try mx toolbox.com to test your mail server.
do you have and spam filters in place that might be sending 
your mail to junk

---

