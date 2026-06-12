---
title: "Maildir delivery problem"
date: 2010-01-12
forum: Server Platforms
---

### Post by jim39 on 2010-01-12
I'm starting my learning curve for seting up an ubuntu mail server using postfix and dovecot. I allowed the system installer to setup "MAIL, LAMP, OPENSSH, and DNS" servers for my home office environment. Everything is working well with the exception of the mail server.
 
When I send a test email and log into the server as a tty user it insicates I have mail and I can see them from there but when I connect with pop3 or imap it authenticates fine and shows my inbox but the messages are not in the inbox.
 
 
I'm running ubuntu server edition x64 9.10
 
The only things on postfix I have changed is the mailbox format.
I used the command **sudo postconf -e 'home_mailbox = Maildir/'**
 
I verified the change was made to the /etc/postfix/main.cf file and the entry shows:
home_mailbox = Maildir/
 
I also changed the corresponding entry in dovecot to:
mail_location = maildir:~/Maildir
 
other than 1 or 2 authentication setting those are the only ones I've changed "out of the box" so to speak.
 
It appears that the mail is still in the /var spooler and is not getting delivered to the users Maildir folder.
 
Anyone have any ideas what I should check next?
 
Thanks in advance.
 
Jim

---

