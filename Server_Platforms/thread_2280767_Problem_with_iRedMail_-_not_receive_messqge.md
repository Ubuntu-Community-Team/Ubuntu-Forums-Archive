---
title: "Problem with iRedMail - not receive messqge"
date: 2015-06-02
forum: Server Platforms
---

### Post by peter195 on 2015-06-02
Hello,

I'm begging with ubuntu so please for your patient :]

I have problem with mail server. Everything was ok and suddenly i cant receive mails. I restart server and didn't help.
I didn't create this server so I don't know how to handle with this problem.

I know that amavisd is not running.. 

service amavis status 
* amavisd is not running 

I cant start it,I get message:

/etc/init.d/amavis start
Starting amavisd: chown: changing ownership of '/var/run/amavis': Operation not permitted

sudo /etc/init.d/amavis start
Starting amavisd: Error in config file "/etc/amavis/conf.d/(à-user": Cant open PEM file /var/lib/dkim/kelsoe.com.au.pem: No such file or directory at /usr/sbin/amavisd-new line 561

Anyone can help?

---

### Post by DuckHook on 2015-06-02
Hi peter195 and welcome to Ubuntu and the forums.

I do not use *iRedMail*, nor *amavis* so cannot help you technically. However, as a new Ubuntu user, I advise against running your own mail server until you have more Ubuntu under your belt. I may be wrong, and you might be a very experienced Linux guru, but since you are posting on a beginner's forum and did not set up this server, I am assuming that you are also new to Linux. If so, then it is not wise to be running something as complex and technical as a mail server until you have a lot more experience with Linux and the CLI.

If you still want to try looking for a solution, then I suggest that you alert a mod and have this thread moved to the server subforum where all the server experts gather.

---

### Post by sandyd on 2015-06-02
> **peter195 said:**
> Hello,

I'm begging with ubuntu so please for your patient :]

I have problem with mail server. Everything was ok and suddenly i cant receive mails. I restart server and didn't help.
I didn't create this server so I don't know how to handle with this problem.

I know that amavisd is not running.. 

service amavis status 
* amavisd is not running 

I cant start it,I get message:

/etc/init.d/amavis start
Starting amavisd: chown: changing ownership of '/var/run/amavis': Operation not permitted

sudo /etc/init.d/amavis start
Starting amavisd: Error in config file "/etc/amavis/conf.d/(à-user": Cant open PEM file /var/lib/dkim/kelsoe.com.au.pem: No such file or directory at /usr/sbin/amavisd-new line 561

Anyone can help?
You are missing your DKIM keys. See [http://www.iredmail.org/docs/sign.dkim.signature.for.new.domain.html](http://www.iredmail.org/docs/sign.dkim.signature.for.new.domain.html) for details on the process, and [http://www.dkim.org/](http://www.dkim.org/) on details on what DKIM is.

To fix the error, run
```

sudo amavisd-new genrsa /var/lib/dkim/kelsoe.com.au.pem

```
to generate the keys.

---

### Post by peter195 on 2015-06-03
Thank you for your reply.


This mail server was working 4-5 years.

I can open iRedCube, I can send message but I cant receive it.

I get only undelivered mail like below:

[COLOR=#333333][FONT=Lucida Grande]This is the mail system at host mail.batist.be.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                   The mail system

<[EMAIL="postmaster@batist.be"]postmaster@batist.be[/EMAIL]>: connect to 127.0.0.1[127.0.0.1]:10024: Connection
    refused
[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Reporting-MTA: dns; mail.batist.be
X-Postfix-Queue-ID: 04BB31206FD
X-Postfix-Sender: rfc822; [EMAIL="romek.mowinski@batist.be"]romek.mowinski@batist.be[/EMAIL]
Arrival-Date: Mon,  1 Jun 2015 15:11:15 +0200 (CEST)

Final-Recipient: rfc822; [EMAIL="postmaster@batist.be"]postmaster@batist.be[/EMAIL]
Original-Recipient: rfc822;[EMAIL="postmaster@batist.be"]postmaster@batist.be[/EMAIL]
Action: failed
Status: 4.4.1
Diagnostic-Code: X-Postfix; connect to 127.0.0.1[127.0.0.1]:10024: Connection
    refused[/FONT][/COLOR]

You still think that is the problem with missing DKIM keys?
How it possible that keys now are wrong after years?

Thank you for your support.

---

