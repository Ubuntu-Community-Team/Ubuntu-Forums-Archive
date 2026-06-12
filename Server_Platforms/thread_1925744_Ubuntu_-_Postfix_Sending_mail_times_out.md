---
title: "Ubuntu - Postfix Sending mail times out"
date: 2012-02-15
forum: Server Platforms
---

### Post by choin on 2012-02-15
Hi all,
 
Im running a LAMP server, downloaded as VMWare appliance and created a website to run on my server.
 
When trying to send a mail fromout my website I receive time outs in my /var/log/syslog file.
 
The php script does returns a true value from sending the mail.. so no scripting error.
 
I am running multiple websites, but actually using one, and when sending mail I see this error in my syslog:
 
Feb 15 07:54:58 lamp postfix/smtp[23905]: DE0BE2161D: to=<[EMAIL="mail@gmail.com"]mail@[EMAIL="to=mail@gmail.com"]gmail.com[/EMAIL][/EMAIL]>, relay=none, delay=742, delays=637/0.01/105/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[209.85.225.27]:25: Connection timed out)
 
im not really sure where to start debugging.
 
My network connection is just fine, my website is running and available online. So It shouldnt be a network issue.
 
One thing: I don't have port 25 open on my router TOWARDS my webserver, but I don't want to receive any mails.. I just want to send them.
 
Thanks for the help in advance!

---

### Post by SeijiSensei on 2012-02-15
Many ISPs block outbound SMTP transactions to keep infected computers on their networks from sending spam.  You need to talk with them about their policies.  (If you're on a residential connection, even running your webserver might violate your terms-of-service; most residential connections prohibit servers.)

Your ISP might have an SMTP relay host you can use for outbound mail.

---

### Post by choin on 2012-02-15
Hi SeijiSensei,
 
I think that could be the case indeed.
My ISP does have a relay server, but I prefer to skip the relay server of my provider and just send the mail myself. If gmail e.g. blocks residiential adresses... that would make sense.
 
One other thought I have, is not having a PTR record online for my mail server. Unfortunately since I'm not the owner of my IP address, I can't create that one.
 
I will try and test using the relay server.
 
To prevent my server sending a 500 mails a second (ISP thinks that is Spam).. is there a way to limit my postfix to send only x-mails a minute ?? Or is there a way to see how many mails are waiting in the queue?? If I can't limit the send-mails, then I can always cleanup the queues :).
 
Thnx!

---

