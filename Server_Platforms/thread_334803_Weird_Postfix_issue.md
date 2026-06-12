---
title: "Weird Postfix issue"
date: 2007-01-09
forum: Server Platforms
---

### Post by matman42 on 2007-01-09
I'm running 6.06 server setup from the Perfect Setup How-to and I've run into an issue with postfix.  I'm installing Drupal and it would not email the initial password out to my email address at insightbb.com.  However it will email out to gmail.com without an issue.  When I look in the mail.log there is an error that reads:

'www postfix/smtp[11231]: connect to gateway.insightbb.com[74.128.0.19]: server refused to talk to me: 554 asav12.manage.insightbb.com (port 25)'

Any ideas why it will send to gmail and not insightbb?  I've updated the php.ini for email information and there is a definite 'from:' on the email header when I receive it at gmail.

---

### Post by MJN on 2007-01-10
Are you on a dynamic IP and/or other potential range of IP addresses that they could be blocking (as an anti-spamming measure)? One would hope the blocking SMTP server would explain the reason for rejection but alas not all do.
 
Mathew

---

### Post by matman42 on 2007-01-18
I'm on a static IP so that shouldn't be an issue.

And the receiving SMTP server gives no clue as to why it won't accept the mail.

---

### Post by jtc on 2007-01-18
How does your SMTP introduce itself? What's the HELO?

Another anti-spam meassure is to drop connections which isn't totally up to spec. This due to the average spam-bot beeing kind of sloppy written.

If you want to, you can send me an email ( [email]l06andol@midgard.liu.se[/email] ) and I'll take a look in the serverlogg, at the mailheader, etc.

Otherwise I would advice you to test sending to a bunch of diffrent addresses/mailserver and see if it's a common problem, or simply insightbb who dislikes your mail. If it is the later perhaps you should contact their postmaster and find out what the problem is?

---

### Post by chrisfay on 2007-01-20
> And the receiving SMTP server gives no clue as to why it won't accept the mail.

I would go [here]("http://www.robtex.com/rbls.html") and check if your IP is listed in the RBL. My home mail server was constantly being rejected until I found out whoever had my IP previously got it blacklisted all over the place.

Try using a relayhost to send your outbound mail through your isp. You should be good to go after that.

---

### Post by etola on 2007-04-27
some mail servers reject  mails coming frim un-registered hosts but gmail does not. 
I also bumped into this when I tried to send email to my university network. I solved the issue by 
relaying my messages over gmail. if you are interested check 

[http://ubuntuforums.org/showthread.php?t=425655](http://ubuntuforums.org/showthread.php?t=425655)

---

