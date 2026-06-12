---
title: "E-mails not sent to outward server"
date: 2009-06-29
forum: Server Platforms
---

### Post by Findarato on 2009-06-29
Hello,

I am having a big e-mail problem with one of my clients hosted on my server.

His website is hosted on our server, but the e-mails are hosted somewhere else. The MX is configured well and there is no problem. When I send him an e-mail through a normal e-mail program (client), it arrives at the other server fine. The problem is, when a script on his website (PHP - contact form) sends some results to his e-mail, the server somehow looks for the e-mail to be present on MY servers (it does not go through the external MX). 
I have checked EVERYTHING, but can't seem to find a solution. Would anyone here know where the problem might be?

Thank you very much for the help.

---

### Post by Findarato on 2009-07-31
Can anybody please help me here, I have no idea how to solve this problem or even where to start looking :(

---

### Post by fakrulalam on 2009-07-31
It seems that your server is defining it self as local delivery for the users domain. Is there any email server configured in your hosting server? If yes, what MTA you are using? If you try to send mail using php contact form, what does you maillog says?

---

### Post by Findarato on 2009-07-31
An e-mail service is indeed installed on my hosting server. I will check the mailing logs in a bit and get back to you.

---

### Post by Findarato on 2009-07-31
How can I check which MTA I am using ? (Someone else installed this server, and I am desperately trying to fix it, even though I am no expert in this :( )

---

### Post by Findarato on 2009-07-31
This is what my mail log says :

Jul 31 20:24:10 ns321463 postfix/qmgr[2937]: AB09F270BE: from=<www-data@something.com>, size=436, nrcpt=1 (queue active)
Jul 31 20:24:10 ns321463 postfix/virtual[11508]: AB09F270BE: to=<info@anotherthing.com>, relay=virtual, delay=0.07, delays=0.03/0.01/0/0.02, dsn=2.0.0, status=sent$
Jul 31 20:24:10 ns321463 postfix/qmgr[2937]: AB09F270BE: removed

Would the problem be with "relay = virtual" ?

(I changed the adresses ofcourse, but hope you can help me with this)

---

### Post by fakrulalam on 2009-08-02
:-) Ya, it seems so. Log says you are running postfix with virutal hosting facilities. Please check the configuration of /etc/postfix/main.cf files. Virtual domain can be defined directly to /etc/postfix/main.cf file with  virtual_alias_domains parameter. This parameter can also link to any file. If it is define to any file (most probably /etc/postfix/virtual). If you get the domain is listed there than your mail server is configured for that domain as virtual server which cause this server to deliver the mail to local inbox.

---

### Post by Findarato on 2009-08-04
Hello again,

I just wanted to tell everyone this indeed fixed my issue.

Thank you very much for the help fakrulalam :)

---

