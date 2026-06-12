---
title: "this may be a newbie question but i have never used it before"
date: 2005-06-07
forum: Server Platforms
---

### Post by luckie on 2005-06-07
i am trying to make a few scripts that use the mail command to email me outputs.  My problem is that when i use the mail cmd i get a undeliverable message back in the users mailbox.  I do not want or need to recieve mail on this box, but i would liek to send it out.  Do i really have to set up something like postfix to  do this?  i am hoping there is a easier/better way to just send mail out.

thanks in advance for any and all help.

the luckie one

---

### Post by defkewl on 2005-06-08
Not that we don't want to help, but we just couldn't understand what you're trying to achieve :)

---

### Post by nocturn on 2005-06-08
Postfix is already installed by default.
But you are probably trying to send out to an ISP address, and your machine does not know how to route the message.


You could try an smtp command (seach freshmeat or google) instead of mail.

---

### Post by luckie on 2005-06-08
let me try and explain thinks better.  i am trying to send a email using the mail command.  The email address is not of a large isp, but is my companies address, lets say acme.com.  so i am using this in my script:

mail -s testing [email]luckie@acme.com[/email] < log.file

then when i check the mail of use luckie on the box i get this....

To: [email]luckie@localhost.loca[/email]ldomain [email]MAILER-DAEMON@localhost.loca[/email]ldomain
Subject: Re: Undelivered Mail Returned to Sender


i hope this helps in explaining things better.

i am going to take a look at the smtp cmd now.

---

### Post by LordHunter317 on 2005-06-08
The traditional UNIX mail(1) command uses your MTA delivery.  Postfix as delivered by Ubuntu is not setup OOB to deliver mail to the Internet.  Which is why you're getting these errors.

You can do one of two things:[list][*]Configure postfix[*]Use a program that natively understands SMTP to send your mail[/list]Which one you pick probably makes little difference.

---

### Post by alastair on 2005-06-08
This is pretty straightforward - and a Postfix config issue.

Postfix :

a) only listens (by default) to a local address (your own system) - OK so far
b) knows nothing (by default) about where to send non-local mail ....

You need to configure Postfix - but luckily this is not very hard (it is a good mail server).

You need to tell postfix how to deliver mail for "acme.com" - where to send this? Asssuming your system is not "acme.com" and you are sending locally.

Check your logs :

/var/log/mail.log

and your Postfix config file :

/etc/postfix/main.cf

Perhaps post it.

---

### Post by az on 2005-06-08
Could the problem be that your isp (or your email provider - the place you are sending it to) is not accepting the mail since it is coming from localhost?  

I know that I can send to yahoo mail, but not to my isp email account for that very reason.  In yahoo, it gets sent to the bulk (junk) folder.

---

### Post by relix42 on 2005-06-13
If you're just looking to have the machine drop some mail to from the command line, install nullmailer.  Very lightweight and just sends mail out to the specified SMTP server.  I found this more satisfactory then having a full SMTP server (Exim, Postfix, sendmail, qmail, etc) on a machine that just needs to send out an occational report.

Once installed, just echo/cat whatever you want sent out through the mail command.  For instance,

echo "Backup Done" | mail [email]address@domain.com[/email]

Or, use any standard redirection to have sent what you want to have sent.

nullmailer drops useful information into /var/log/mail.err and /var/log/mail.info for troubleshooting.

Make sure that whatever SMTP server you send to, allows you to send (i.e. relay) if need be, otherwise, you still won't get anything.

---

