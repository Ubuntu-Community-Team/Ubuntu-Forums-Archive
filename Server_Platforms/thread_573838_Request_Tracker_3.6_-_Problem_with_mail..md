---
title: "Request Tracker 3.6 - Problem with mail."
date: 2007-10-12
forum: Server Platforms
---

### Post by johng4 on 2007-10-12
Extensive googling, forum searches, mailing list scowering have all lead me to nothing...

I can not get the rt-mailgate to work.  So far I've managed to get Postfix to deliver the e-mail to the rt-mailgate command.  From there, it just.. poofs.  Below is the log of a test message I sent to my "General" queue.

Here is the output of  /var/log/mail.log:
```

Oct 12 00:53:21 john postfix/smtpd[22867]: connect from zzzz.yyyy.com[xx.xx.xx.19]
Oct 12 00:53:22 john postfix/smtpd[22867]: 21A0C2F6C9: client=zzzz.yyyy.com[xx.xx.xx.19]
Oct 12 00:53:22 john postfix/cleanup[22872]: 21A0C2F6C9: message-id=<1192168623.5359.41.camel@fujiko>
Oct 12 00:53:22 john postfix/qmgr[22831]: 21A0C2F6C9: from=<johng@tuneforge.net>, size=1187, nrcpt=1 (queue active)
Oct 12 00:53:22 john postfix/local[22874]: 21A0C2F6C9: to=<support@aaa.bbb.net>, relay=local, delay=0.31, delays=0.26/0.01/0/0.04, dsn=2.0.0, s$
Oct 12 00:53:22 john postfix/qmgr[22831]: 21A0C2F6C9: removed
Oct 12 00:53:22 john postfix/smtpd[22867]: disconnect from xxxx.yyyy.com[xx.xx.xx.19]

```

xxxx.yyyy.com is the mail server I use for the [email]johng@tuneforge.net[/email] e-mail account (not local).
aaa.bbb.net is my local mail server fqdn.

Everything seems to work just fine until it hits the rt-mailgate command.

---

### Post by johng4 on 2007-10-12
Further tracking on this issue shows that my e-mails are not being sent either.. they are captured instead by my apache2 error.log

Here's the section from the error.log:

```

[Fri Oct 12 03:10:31 2007] [error]: error:    couldn't parse head; error near:
Greetings,
This message has been automatically generated in response to the
creation of a helpdesk call:
"Testing Reminders",
a summary of which appears below.
There is no need to reply to this message right now. Your ticket has been
 assigned an ID of [support.snohoma.net #3]. Please include this string
in the subject line of all future correspondence about this issue.  (/usr/share/request-tracker3.6/lib/RT/Template_Overlay.pm:336)


```

---

### Post by johng4 on 2007-10-14
recent error tracking resulted in the following...

```

xxxx@john:/var/mail# /usr/bin/rt-mailgate --queue General --action correspond --url 'http://support.snohoma.net/rt' < root
An Error Occurred
=================

302 Found
xxxx@john:/var/mail# nano root
You have new mail in /var/mail/root
xxxx@john:/var/mail# /usr/bin/rt-mailgate --queue General --action correspond --url 'http://support.snohoma.net/rt' < root
An Error Occurred
=================

302 Found

```

Can't seem to find anything relevant to the 302 Error I'm getting when putting a direct mail into the mailgate.

It appears this is the source of the delivery error.  I've set all the permissions in the General queue to allow everyone the permissions needed for mail.

---

### Post by johng4 on 2007-10-15
Ok, after enough digging I found out what the issue was..

Postfix was delivering mail to rt-mailgate.  The mailgate was having an issue with the URL I was entering into the alias command.

The actual URL is [https://support.snohoma.net:911/rt/](https://support.snohoma.net:911/rt/), but I had it as [http://support.snohoma.net](http://support.snohoma.net) (which works for a browser, but not for the mailgate).

Now, the only issue I'm having is getting my Autoreply to work on ticket creation.  All other e-mails coming from RT work.  Still working that one out.

---

### Post by johng4 on 2007-10-15
SOLVED!

Ok, the template I was using lacked the very top part of the message, which told RT to send it out.

I feel stupid for missing it, but smarter for having troubleshot this all the way through.

Either way.. looks like the problem was at the Keyboard Input Layer.

---

