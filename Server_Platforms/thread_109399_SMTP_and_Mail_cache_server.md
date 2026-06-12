---
title: "SMTP and Mail cache server"
date: 2005-12-28
forum: Server Platforms
---

### Post by mxa055 on 2005-12-28
Hi there,

I have an ubuntu machine setup as a gateway server for 3 PCs. I would like to have it  handle our e-mails though as well. 
What I would like to do is have the ubuntu box to download all the mail for 4 different mail accounts (from the same domain, say example.com) so

user1.example.com, user2.example.com, user3.example.com & user4.example.com (these exist on my website [www.example.com](www.example.com))

whenever a new mail arrives, or a small intervals say 10 minutes and store it locally (on the server). Then when I open my e-mail client on one of the other PCs retrieve mail from ubuntu box and not from pop.example.com for, say, user2.example.com

After that I would also like to be able to use the server for sending mail from the 3 PCs without waiting for large attachements to be uploaded. So say user2 sends a mail with a 5MB attachments, should see the message instantly leave and then the message should be send asap from the ubuntu server. 

Note that I am looking for a fullblown mailserver implementation and that chances are that I will not have to make any changes any time soon on the size of the implementation. 

What programs should I use and how should I configure them? I want my outgoing e-mails to be [email]user1@example.com[/email] (do they have to go through my websites mail server to be appended the example.com, do I have to change anything in the MX records on my website (note that the ubuntu server does not have a good uptime and thus could not use it as a primary mail server).

Thanks and sorry for the length of the message, just trying to be clear.

---

### Post by coren_ita on 2007-01-23
Hi!

I'd need something like that too... but I haven't a clue on how to start :(

---

### Post by anotherMichael on 2007-01-23
I also would appreciate some words of wisdom. I looked at IMAP server for retrieving plus postfix but I do not have enough experience to see if it will not get me in more trouble the getting email directly to my office PC.

---

