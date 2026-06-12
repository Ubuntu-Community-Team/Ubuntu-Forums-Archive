---
title: "Sypheed anonymized"
date: 2007-05-20
forum: Server Platforms
---

### Post by Dax0r on 2007-05-20
When i send something with sylpheed,it shows this thing

X-Mailer: Sylpheed 2.4  (GTK+ 2.10; i686-pc-linux-gnu):

Well I dont want that who reads my mails know my os and my email client....there is a way to hide it?

---

### Post by Pollywoggy on 2007-05-20
> **Dax0r said:**
> When i send something with sylpheed,it shows this thing

X-Mailer: Sylpheed 2.4  (GTK+ 2.10; i686-pc-linux-gnu):

Well I dont want that who reads my mails know my os and my email client....there is a way to hide it?

Yes there are a couple of ways.  One is in the email client itself, but since I have not used Sylpheed in a few years, I am not certain how to do it or if it can be done there.

The method I use involves changing something in the MTA configuration files, but that will not work if your mail client connects to your ISP's mail server in order to send mail.  If you are using Postfix, you can use something like this:

/^received:.*192\.168\.1\./    IGNORE
/^User-Agent/   IGNORE
/^X-Evolution/ IGNORE
/^X-Virus/ IGNORE
/^X-Mailer/  IGNORE


The last line is the one that applies to your situation and you put it in your header_checks:

header_checks = regexp:/etc/postfix/header_checks.re

You can do something similar in Exim but I do not recall specifics for Exim.

---

### Post by Dax0r on 2007-05-23
> **Pollywoggy said:**
> Yes there are a couple of ways.  One is in the email client itself, but since I have not used Sylpheed in a few years, I am not certain how to do it or if it can be done there.


Thanks,it's a good idea.
Btw I found an email client way,but this is a good alternative

---

