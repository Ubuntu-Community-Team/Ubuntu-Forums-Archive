---
title: "Postfix delivering mail to user."
date: 2006-03-09
forum: Server Platforms
---

### Post by gmclachl on 2006-03-09
I set up postfix on my server at home by following the guide at 
[http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p4](http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p4)

  Any I can't seem to get it to work properly 

  I tried telnet domain 25

---- 
Trying xx.xx.xx.xxx...
Connected to mail.domain.ext.
Escape character is '^]'.
220 server1.domain.ext ESMTP Postfix (Ubuntu)

HELO domain.ext

250 server1.domain.ext

MAIL FROM: [email]user@somedomain.com[/email]

250 Ok

RCPT TO: [email]admin@domain.ext[/email]

250 Ok

DATA
354 End data with <CR><LF>.<CR><LF>
Subject: hello
this is a test
.
250 Ok: queued as 0A6705B405B

If i now ssh into the box and type
   mail admin
I get 
  no mail for admin

So it seems to be queued but it isn't getting delivered locally 

Any suggestions as to the problem. I know that in the set up I use imap and MailDir but I don't know if I then have to do anything else locally.

Thanks 
George

---

### Post by ariek on 2006-03-09
Hi George,

Ones you have configured Postfix to deliver mail into a maildir, you should check your mail dir directory - have you created one yet? - or try with an IMAP client such as Evolution.

Arie

---

### Post by gmclachl on 2006-03-09
[QUOTE=ariek]Hi George,

Ones you have configured Postfix to deliver mail into a maildir, you should check your mail dir directory - have you created one yet? 
[/QUOTE]
 Um...nope. Where would I create one? inside the home directory?

> 
- or try with an IMAP client such as Evolution.

Arie

 Well that seems to be another problem. When i try to use an email client it refuses to accept my password. 

George

---

### Post by ariek on 2006-03-09
Presuming you have installed CourierIMAP
- login as the user you want to create the maildir for;
- cd /home/USER;
- maildirmake Maildir.
Now you can check /home/USER/Maildir, or use IMAP client.

---

### Post by gmclachl on 2006-03-09
Thanks, it's working now. My big problem seems to be my router at home, because it uses NAT it coughs a huge hariball if I try to connect to my domain. i.e mail.mydomain.com 

Which means that I can't really collect email when at home. However to try and get round this I have set up my email client to point to the internal address of the server. In this case 192.168.2.100 but it just times out. 

When I go home tonight I will try it again now, that I have made the changes.

Thanks again.
George

---

