---
title: "help with postfix config?"
date: 2011-08-01
forum: Server Platforms
---

### Post by sneakyimp on 2011-08-01
I'm hoping there's a postfix wiz out there who might spare a moment to help me sort a problem.  I've got an Amazon EC2 instance with postfix set up to use Amazon SES for mail delivery (which is a [total pain](https://forums.aws.amazon.com/thread.jspa?threadID=72553)). The particular problem I'm having is that samhain (a security tool) cannot send its email notifications.  Some important things about this configuration:
1) I don't want any mail at all being delivered to a mailbox on this machine. All mail destined for mydomain should be sent to Google Apps.
2) I DO want mail sent to 'root' or 'root@localhost' to be emailed to a real FQDN address, e.g., [email]admin@mydomain.com[/email]
3) I don't want this machine accepting any remote mail connections via SMTP or otherwise.
4) Any email sent out to the internet from this machine must be sent via Amazon SES because Amazon puts all their EC2 IP addresses on a 'policy block list' -- in other words they don't really permit outgoing mail to be sent directly from these EC2 instances.

**How can I make sure that mail sent from this server to root@localhost is sent to [email]admin@mydomain.com[/email]?**
Right now, with my current config (see below), sending mail to root@localhost gets an error.  I use sendmail thusly:
```
$ sendmail -t
To: root@localhost
Subject: test email
Here is a test mail 
.
```
The mail log shows this error:
```
Aug  1 09:24:36 ip-10-100-237-252 postfix/error[32027]: 00EE97214B: to=<root@localhost.mydomain.com>, orig_to=<root@localhost>, relay=none, delay=20, delays=20/0.01/0/0.01, dsn=5.0.0, status=bounced (local delivery is disabled)

```

Interestingly, just sending mail to 'root' using sendmail results in mail being successfully delivered to [email]root@mydomain.com[/email]:
```

$ sendmail -t
To: root
Subject: just 'root' my brutha
Testing mail from the server here.  This just send to 'root'.
.
```

HOWEVER, samhain somehow fails when I set 'root' as the target email address.  From the samhain log:
```

ERROR  :  [2011-08-01T08:49:56+0000] msg=<Timeout on SMTP session init>, subroutine=<sh_mail_start_conn>, service=<mail>, host=<ip-WWW-XXX-YYY-ZZZ.ec2.internal>
F2C9747FC601DD241C1A6C1E4EB204F66551F01EADAE619F
ERROR  :  [2011-08-01T08:49:56+0000] msg=<Service failure>, service=<mail>, obj=<root>
2D4295AB3335E918BDD097884A103A04A37620285A5924B1

```

I'm hoping that I can solve this problem by altering my postfix configuration.  Any emails sent to either "root", "root@localhost", or "root@mydomain.com" should all get sent out on the internet from this server to [email]root@mydomain.com[/email].  I've been consulting the postfix docs and find them confusing.  Here is some detail on my setup:
```
$ sudo postconf -n
config_directory = /etc/postfix
default_transport = aws-email
inet_interfaces = loopback-only
local_transport = error:local delivery is disabled
mydomain = mydomain.com
mynetworks_style = host
myorigin = $mydomain
relayhost = $mydomain
smtp_generic_maps = hash:/etc/postfix/generic
smtpd_banner = $myhostname ESMTP $mail_name

```
Note that I added aws-email to master.cf as described in the Amazon Docs.

Any help would be extremely welcome.

---

