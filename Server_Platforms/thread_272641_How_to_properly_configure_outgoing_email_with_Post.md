---
title: "How to properly configure outgoing email with Postfix"
date: 2006-10-06
forum: Server Platforms
---

### Post by don7777 on 2006-10-06
I am a bit confused about the configuration of Postfix. 

I'm running ubuntu 6.06 and the machine is connected to the internet with Verizon DSL which gives me a dynamic IP address. I'm running RT (request tracker) on the machine and I would like it to be able to send outgoing emails to users. At the moment, I have no need to receive incoming email though I would like to be able to receive email from localhost.

I suspect that my Postfix configuration is very close to correct but I'm having one bit of confusion as described below:

I have a domain hosted on the internet, let's call it X.com. I have an email address at X.com, let's call it don@X.com. I also have another email at Y.com, let's call it don@Y.com. I have been playing with /etc/mailname and have put two different values in the file. First, I put "localhost" in the file. When I send an email to user don on the local machine from the local machine, the email is sent fine. When I send an email from the local machine to don@X.com, the email never arrives. When I send the email from the local machine to don@Y.com, the email bounces with a message indicating that a fully qualified address is needed (i.e. the destination server did not like don@localhost). The next thing I tried was to put X.com in /etc/mailname. Now I tried sending the three email again (don, don@X.com, don@Y.com). don@X.com and don@Y.com arrived correctly. However, the email sent to the local user don arrived in don@X.com's email box.

So, the question I have is, what should go into /etc/mailname? If I set it to localhost, only email sent to users on the same machine is delilvered. If I set it to another machine's domain name (X.com) all the mail is sent and local email is sent to the other machine.

Thanks very much in advance for any help,
Don

---

### Post by sonic2000gr on 2006-10-07
Since you have a dynamic IP address you will have to register with a service like [www.dyndns.com](www.dyndns.com) (it is free). You will then get a name like something.dyndns.org which will be assigned to your server. You will have to keep the name pointing to your changing IP by using a client. (ddclient is a program that does just that.)

/etc/mailname should have something.dyndns.org as the name of your server. The receiving mail server will probably not accept your mails if your server name does not resolve. localhost cannot resolve, but something.dyndns.org will.

your email address will then be [email]someone@something.dyndns.org[/email].
You will still be able to receive email from localhost to localhost (internal mail)

---

