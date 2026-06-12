---
title: "ssmtp, mdadm and email"
date: 2012-05-11
forum: Server Platforms
---

### Post by samcoinc on 2012-05-11
We installed ssmtp and set it up correctly (I think) I can send emails out using ssmtp.  I Have the email setup in the mdadm.conf also. 

sudo mdadm --monitor --scan --test --no-sharing 
sendmail: 573 root@EMPIRE120503 failed to route the address 

I am at a loss..

thanks
sam

12.04 lts

---

### Post by ian dobson on 2012-05-11
Hi,

Is EMPIRE120503 an actual host name. ie can you ping EMPIRE120503? If the host is just the server running mdadm then just use root@localhost and make sure the receiving email server accepts the address.

Regards
Ian Dobson

---

### Post by rubylaser on 2012-05-11
I use my Gmail account with ssmtp to send my mdadm alerts like [this]("http://zackreed.me/articles/39-send-system-email-with-gmail-and-ssmtp").

---

### Post by ian dobson on 2012-05-12
Hi,

I don't think you've got ssmtp set up correctly.
Sendmail seems to be trying to use your alias email address rather than the actual address.

regards
ian dobson

---

### Post by davidesweden on 2012-07-26
Hi,

I have a similar problem with mdadm and email. The error I get when running the command below is:

mdadm --monitor --scan --test --oneshot
sendmail: 501 Syntax error in arguments

I believe ssmtp is configured correctly as the test email sent using the command below works fine.
echo test|sendmail MYEMAIL

I also configured the ssmtp using:
root=MYEMAIL
mailhub=smtp.mail.yahoo.com:465
rewriteDomain=
hostname=MYEMAIL
UseTLS=YES
#UseSTARTTLS=YES
FromLineOverride=YES

mdadm.conf file looks like:
MAILADDR MYEMAIL


Any help would be appreciated.
Thanks!

---

