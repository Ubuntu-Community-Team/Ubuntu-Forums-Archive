---
title: "Mail server question"
date: 2008-06-03
forum: Server Platforms
---

### Post by GuruMadMat on 2008-06-03
Hi all,

I looked around and found some solutions for what I want but I'm not sure..

This is what I want:

[IMG]http://www.springtrampolines.be/smissaert/mail.jpg[/IMG]

I want my server to collect my email from 2 servers
there is only one email address per mailserver.
The client must have 2 inbox's, so 2 logins to my server
one login is mail from mailserver 1
the other is mail from mailserver 2
the connection between the clients have to be secured with SSL or TLS
when I send mail it has to go to my server and send it from there through my ISP

Maybe someone could give me a howto and tell me what I have to change to fit my needs...

---

### Post by andol on 2008-06-03
How about running [fetchmail]("http://fetchmail.berlios.de/") on "My server"?

---

### Post by GuruMadMat on 2008-06-03
I know i will have to use fetchmail but i need some other things too...

I found this tutorial:
[http://flurdy.com/docs/postfix/]("http://flurdy.com/docs/postfix/")

will this work for me?
Or is this not what I want?

---

### Post by andol on 2008-06-03
Yes, you'll need a Mail Transfer Agent (MTA) such as postfix. That is what fetchmail will hand of its downloaded mails to. For your client to collect the mails from your server you most likely want a POP- or IMAP-server.

Feel free to take a look at this category in the community documentation.

[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

---

