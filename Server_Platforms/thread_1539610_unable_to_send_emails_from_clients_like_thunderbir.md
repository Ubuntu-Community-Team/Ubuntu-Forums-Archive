---
title: "unable to send emails from clients like thunderbird."
date: 2010-07-26
forum: Server Platforms
---

### Post by hhamilton on 2010-07-26
I am using postfix as my MTA. It is running on ubuntu and I am administering the system through webmin. I can send email from the command line in linux, and i can recieve email, but when I try to send email from a client, it doesn't work. 

Try as I might with different configurations, I can't send email from a client. when I look in the mail.log i only find: 

Jul 26 19:16:43 alpha postfix/smtpd[24185]: warning: 99.153.1.214: hostname adsl-99-153-1-214.dsl.applwi.sbcglobal.net verification failed: Name or service not known
Jul 26 15:31:00 alpha postfix/smtpd[17430]: connect from unknown[99.153.1.214] 
Jul 26 15:31:31 alpha postfix/smtpd[17430]: lost connection after UNKNOWN from unknown[99.153.1.214] 
Jul 26 15:31:31 alpha postfix/smtpd[17430]: disconnect from unknown[99.153.1.214] 

after trying to send a message. I have no idea what could be wrong. 

thanks for any help,

---

### Post by lisati on 2010-07-26
That looks like someone else trying to connect to your email server from the outside and failing. From where I sit, it looks unrelated to your problems sending with an email client. The clue is the entry *connect from unknown[99.153.1.214]*, which is an sbcglobal.net customer's IP address based somewhere near Appleton. Am I right in assuming that it's a different ISP in a different part of the USA?

Have a look on Webmin's Servers->Postfix mail server page. Down near the bottom there's an option to view what has been put in your system's mail queue - perhaps your outgoing mail has been deferred.

---

### Post by lisati on 2010-07-26
p.s. I've knocked together a tool on my website that I sometime use to troubleshoot email problems. It's a small scale cross between some of the things [whatismyipaddress]("http://whatismyipaddress.com/") and [blacklistalert.org]("http://www.blacklistalert.org/") do, aimed more at identifying spam-related problems than configuring Postfix. I mention it here (a) because I used it to locate the IP address mentioned in the OP's log, and (b) it might be useful to someone:

[http://lisati.homelinux.com](http://lisati.homelinux.com) will try to identify your current location and checks to see if you're on *some* [DNSBL]("http://en.wikipedia.org/wiki/DNSBL") lists.
[http://lisati.homelinux.com?ip=x.x.x.x](http://lisati.homelinux.com?ip=x.x.x.x) will do the same for a specific IP address (replace the x.x.x.x with the IP address you want to query)

---

### Post by hhamilton on 2010-07-26
hello, thanks for the help. that [unknown] ip near appleton is my personal dsl account which I am using to test things. I buy it from a local company that buys a big pipe from att. the connection is a pretty good representation of what people how need t use the mail server will be using.

you are right in the fact that it probably is a server side problem, but i have been playing around with different configuration settings in thunderbird to try to get it to work.

edit: i can send email now, but my server is an open relay, so am working on authentication

---

