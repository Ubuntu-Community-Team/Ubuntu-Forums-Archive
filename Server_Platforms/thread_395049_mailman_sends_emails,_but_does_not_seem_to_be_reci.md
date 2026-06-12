---
title: "mailman sends emails, but does not seem to be recieving anything"
date: 2007-03-27
forum: Server Platforms
---

### Post by Brazen on 2007-03-27
I set up mailman per these instructions: [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/email-services.html#mailman](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/email-services.html#mailman)

I've created a new mailing list.  When I go to the web page and sign up for it (with an email address that has nothing to do with the adminstrator or moderator, etc), I recieve an email asking for confirmation.  I return the confirmation email, but I'm still not signed up for the list.  I tried sending messages to the list and nothing happens.

Can somebody help me figure this out?  To start with I should probably check to see if exim is even getting the emails, but I'm at a loss when it comes to email junk :confused:

---

### Post by Mr. C. on 2007-03-27
Check you logs in /var/log to see what exim is doing with the mail.

Posts do not not show up in the archives immediately - they show up after mailman does its periodic run to post archives.

MrC

---

### Post by Brazen on 2007-03-27
> **Mr. C. said:**
> 
Posts do not not show up in the archives immediately.

MrC

I'm not even at that point yet.  I respond to the confirmation email, but I never show up as a user (ie, going as an admin to the lists webpage shows 0 users).

---

### Post by Mr. C. on 2007-03-27
Understood.  But you are at the point where you need email to be working; that was my first suggestion.  You need to learn how to read your emailer's logs... this is critical to solving such problems.

MrC

---

### Post by Brazen on 2007-03-27
> **Mr. C. said:**
> Understood.  But you are at the point where you need email to be working; that was my first suggestion.  You need to learn how to read your emailer's logs... this is critical to solving such problems.

MrC

oh yeah, I know.  I tar'ed up the log directory and brought it home.  I had to go pick up my kids, but I'm going to look through the logs tonight... hopefullly ;)

---

### Post by Brazen on 2007-03-28
This is the only thing in the logs:```
2007-03-27 15:46:32 1HWIYq-0002yh-IB <= test-bounces@lists.company.com H=localhost (LISTS.company) [127.0.0.1] P=esmtp S=2045 id=mailman.0.1175028390.11450.test@lists.company.com
2007-03-27 15:46:32 1HWIYq-0002yh-IB => brazen@cox.net R=smarthost T=remote_smtp_smarthost H=192.168.1.10 [192.168.1.10]
2007-03-27 15:46:32 1HWIYq-0002yh-IB Completed
```
other than a bunch of "Start queue run" "End queue run" lines.  So this leads me to believe the return emails are not even making it to the server?!  Our DNS is hosted, is there way I can query the DNS server to see what it is reporting for our MX record?  Odd thing is, I'm not getting back any Non-delivery reports.

The above log would of course be the outgoing email from the mailman server which is being recieved just fine.

---

### Post by Mr. C. on 2007-03-28
Sorry for the delay in responding.

What do the mailman logs (smtp, vette, bounces, etc.) show ?

I don't know what your mailer setup is, so can't read too much from the logs other than a message was sent to your smart host relay 192.168.1.10 by mailman (we know this because it has a mailman message id).   It does seem then from your logs though that your system is not receiving your email.  Have you verified you can send/receive fine w/out mailman?

You can see what your MX records are by running the **host** command:

```
$ host cox.net       
cox.net has address 68.1.17.9
cox.net mail is handled by 100 mx.east.cox.net.
cox.net mail is handled by 100 mx.west.cox.net.
```

MrC

---

### Post by Brazen on 2007-03-29
Ah, that 'host' command helps.  Our mx records are screwed up, I'll try and get our duct tape and chicken-wired ISP to fix it.

---

### Post by Brazen on 2007-03-29
Ok, now the emails are getting to our email gateway (a TrendMicro IMSS server) but it fails when trying to send it on to the mailman server.  Could there be something in exim that needs changed in order to accept outside email?  This is the error from the email gateway, if it means anything to anyone:```
ERROR:  ERROR CONNECTING TO INBOUND SMTP SERVER! 	[17c:624]
ERROR:  MDA finish, delivery fail since <LRT: SendMail SMTP fail and no branch> and spend <906> ms 	[17c:624]
```

I'll look through the exim logs and see if there is anything corresponding to this.

---

### Post by Mr. C. on 2007-03-29
The exim logs will tell you why it is not allowing your gateway to forward.

MrC

---

### Post by Brazen on 2007-03-29
ok, there was nothing in the logs corresponding to any incoming connection.  On a whim I ran dpkg-reconfigure on exim4-config and now it seems to be recieiving emails.  I _think_ the problem was that it was only listening on 127.0.0.1.  However, there still seems to be a problem.

I tried replying again to a subscription confirmation and I also tried sending to the list owner, but these show up in the /var/log/exim4/rejectlog:

```
rejected RCPT <test-owner@lists.company.com>: relay not permitted
rejected RCPT <test-request@lists.company.com>: relay not permitted
```

---

### Post by Brazen on 2007-03-29
ha, ok.  I ran dpkg-reconfigure again and this time I put "lists.company.com" in when it asks for what domain this is the endpoint for.  I guess I just figured it would know that one already because I had to put it in earlier in the config.

It _seems_ to be working now.

---

