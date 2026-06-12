---
title: "Mail server errors need help figuring out what went wrong?"
date: 2009-09-18
forum: Server Platforms
---

### Post by hockey97 on 2009-09-18
Ya, I test my mail server and it has errors this is my first time trying to get postfix to work with mysql.

I am getting the error :  SMTP -> ERROR: RCPT not accepted from server: 451 4.3.0 : Temporary lookup failure


So far it's good when a user from like aol.com sends mail to the server. It gets to the server and then when the mail server looks for the user on the mail server it gives this error.

Here is the mail server test full results but took out my domain name:

```

Resolving hostname...
Connecting...
SMTP -> FROM SERVER:
220 hostname ESMTP Postfix (Ubuntu)
SMTP -> FROM SERVER: 
250-hostname
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH CRAM-MD5 DIGEST-MD5 NTLM LOGIN PLAIN
250-AUTH=CRAM-MD5 DIGEST-MD5 NTLM LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
MAIL FROM: user@aol.com
SMTP -> FROM SERVER:
250 2.1.0 Ok
RCPT TO: user@my_custom_domaian.com
SMTP -> FROM SERVER:
451 4.3.0 : Temporary lookup failure
SMTP -> ERROR: RCPT not accepted from server: 451 4.3.0 : Temporary lookup failure

Message sending failed.
```

In the mail logs I can see the transport maps in mysql is failing. 
I also see a error showing a double bounce.



I followed this setup: [http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy_p2](http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy_p2)

just on that page from top to bottom. I didn't do whats on the next pages.

Do you think it should work? If I followed that tutorial from top to bottom.

---

### Post by i.r.id10t on 2009-09-19
AOL is pretty strict about who they accept mail from - could be you don't have reverse dns, etc. Try using a different account to send to.

---

### Post by hockey97 on 2009-09-19
I just tried gmail account and get the same error. 

The error I am getting is a lookup error on my mail server. I config postfix to talk with mysql. 

What I am seeing that the e-mails are getting to my mail server and connected to my mail server with  no problem. It's just when my mail server has to deliver the e-mails to the user it gets the error. I did install postfix-mysql. 

I followed the steps on this page :  [http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy_p2](http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy_p2)

I only followed whats on that page I didn't go to the next page or anything.

The only thing I didn't do according to that tutorial is that I am using mysql root account to access the databases. In the tutorial it asked to create a new account for postfix.

I assumed that it didn't make a difference if you made a new account or used one that is already made. However I could be wrong. They also said to make sure your FQDN  IS right else it wont work. I don't know what FQDN stands for. 

If you go on that page and scroll down it's close to the end of the page. It's the only Text on that page that is RED. 

I am guessing it's talking about the hostname. I typed in terminal the command hostname and got the name printed out . 
I am woundering if this hostname is the name of my computer or does it mean the domain name of my websites? 
I am guessing they meant the computer hostname. So I currently am using the hostname that been setup with ubuntu at the start.

---

