---
title: "Nullmailer help"
date: 2009-07-11
forum: Server Platforms
---

### Post by Mocker on 2009-07-11
Hi folks,

I came across a bunch of error messages in my syslog recently from nullmailer complaining that it couldn;t send mail. After checking the forums here, I found out that I could configure nullmailer to send mail via my ISP's SMTP server. This sounds like a good thing,s icne I'd like to get the various error emails that various systems are trying to send. So, I configured it using the /etc/nullmailer files adminmail to give an email address I want to send errors to, and edited the remotes file to point to my ISP's SMTP server, adding in the --user and --pass options.

I'm still getting errors in syslog from nullmailer, but they have changed:

```

Jul 11 23:18:53 server nullmailer[11772]: Starting delivery: protocol: --port=25 host: smtp.my.isp file: 1246797035.30281
Jul 11 23:18:53 server nullmailer[11772]: Sending failed:  Could not exec program
Jul 11 23:18:53 server nullmailer[11772]: Starting delivery: protocol: --port=25 host: smtp.my.isp file: 1236600009.9940
Jul 11 23:18:53 server nullmailer[11772]: Sending failed:  Could not exec program
Jul 11 23:18:53 server nullmailer[11772]: Starting delivery: protocol: --port=25 host: smtp.my.isp file: 1237116915.17941
Jul 11 23:18:53 server nullmailer[11772]: Sending failed:  Could not exec program
Jul 11 23:18:53 server nullmailer[11772]: Starting delivery: protocol: --port=25 host: smtp.my.isp file: 1236687287.14793
Jul 11 23:18:53 server nullmailer[11772]: Sending failed:  Could not exec program
Jul 11 23:18:53 server nullmailer[11772]: Delivery complete, 23 message(s) remain.

```

Gee, useful error message there :roll:. Could it maybe tell me **what** program it's trying to exec?  Does anyone know what nullmailer is trying to call, and how do I set it up?

---

### Post by skitching on 2010-04-19
Just in case someone else also has this problem:

I got this, and eventually realized that my /etc/nullmailer/remotes file had an invalid line.

The remotes file needs to contain something like:
   my.isps.smtp.server  smtp

Presumably nullmailer then executes "nullmailer-smtp" or similar. I had omitted the protocol specification ("smtp") hence the (rather unhelpful) error message.

---

