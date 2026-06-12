---
title: "Is installing a mail server on my home computer a stupid idea?"
date: 2009-11-04
forum: The Cafe
---

### Post by rob86 on 2009-11-04
I've been reading some linux webpages that talk about sending email from a terminal. This seems cool, but is it a stupid idea to run a mail server just for myself or do people actually do this?

---

### Post by ZankerH on 2009-11-04
If you just want to send and receive mail with a terminal application, just use a client like fetchmail or Mutt. Otherwise, go for it!

---

### Post by dragos240 on 2009-11-04
I have not gotten postfix to work yet. It's pretty frustrating.

---

### Post by FuturePilot on 2009-11-04
Just my opinion here. It's not reliable. With your own mail server you're relying on 1 server which means a single point of failure. There's no redundancy so if your server goes down or your connection dies and someone tries to send you something, well...

There may be other issues as well such as your ISP blocking certain ports and if you have a dynamic IP just about any email provider will reject anything you send so you'll have to configure the server in a certain way to avoid that.

Of course you could do it, I just wouldn't rely on it.

---

### Post by LookTJ on 2009-11-04
Both Comcast and ATT made it impossible to set up a mail server with the default configuration.

With Comcast, I had to setup smtp through them. ATT is much more difficult and so far no success. The ISPs did this to prevent spam I suspect. ATT used to have an opt-in for port 25, not anymore :(.

Hope you have better luck with your ISP if you decide to go ahead with this

---

### Post by amauk on 2009-11-04
> **rob86 said:**
> I've been reading some linux webpages that talk about sending email from a terminal. This seems cool, but is it a stupid idea to run a mail server just for myself or do people actually do this?I run my own mail server
(although from my home server, not my desktop machine)

---

### Post by infestor on 2009-11-04
if you get a server and a reliable connection why not?

---

### Post by MechaMechanism on 2009-11-04
Go for it!  I use Exim4 although in my case it's setup for remote smarthost because my ISP don't allow port 25.  If your ISP don't allow port 25 then I would suggest Tuffmail as your remote smarthost.  Get your your own domain too.  And don't use port 25, use 587 with TLS for encrypting your login.  And remember if the mail server is down no one can send you an email so have a backup server.  Good luck.

---

### Post by 3rdalbum on 2009-11-04
You can send mail from a terminal or a script without having an e-mail server.

I'd be careful with e-mail servers - the last thing you want is to leave it poorly secured and have spammers start using it.

---

### Post by JillSwift on 2009-11-04
Well, most mail servers won't accept smtp traffic from most "home" IP addresses. Though you can get around that easily enough with ssmpt and your ISP's smtp server.

As for receiving mail, as has already been said, if your connection and server are reliable enough, why the heck not?

---

### Post by Xbehave on 2009-11-04
security. Make sure it's safe and kept upto date, mail servers have a bad track record

---

### Post by NTolerance on 2009-11-05
I use exim4 + smarthost to my ISP email.  This allows my cron jobs to send me email about their status.  exim4 is very easy to configure in ubuntu, just run

```

sudo dpkg-reconfigure exim4-config
```

and follow the prompts.

---

### Post by Warpnow on 2009-11-05
If your power goes out...net goes down...PSU fals...

No email. I wouldn't use it for important things.

---

### Post by rob86 on 2009-11-05
I don't think installing a mail server is worth the effort really. I do however think fetchmail looks good. Does it work with GMail? I found conflicting reports on it's compatibility with GMail and a lot of the guides are almost 5 years old, probably a lot has changed since them..

Fetchmail seems kind of complicated. I don't know much about encrypting things. I tried to follow instructions, but some of the commands didn't do seem to work. I did manage to connect to my ISP's pop server, which was simple enough, but I didn't use any of that fancy encryption stuff most of the webpages I read talked about.

---

### Post by ade234uk on 2009-11-05
For educational purposes I would say yes, but for reading your email everyday its more hassle than its worth. You might as well get yourself a gmail account.

---

### Post by MechaMechanism on 2009-11-06
> **rob86 said:**
> I don't think installing a mail server is worth the effort really. I do however think fetchmail looks good. Does it work with GMail? I found conflicting reports on it's compatibility with GMail and a lot of the guides are almost 5 years old, probably a lot has changed since them..

Fetchmail seems kind of complicated. I don't know much about encrypting things. I tried to follow instructions, but some of the commands didn't do seem to work. I did manage to connect to my ISP's pop server, which was simple enough, but I didn't use any of that fancy encryption stuff most of the webpages I read talked about.
I don't use Gmail myself but here's what I found.

[http://linuxhelp.blogspot.com/2005/05/using-fetchmail-to-download-emails.html](http://linuxhelp.blogspot.com/2005/05/using-fetchmail-to-download-emails.html)
[https://help.ubuntu.com/community/GmailPostfixFetchmail](https://help.ubuntu.com/community/GmailPostfixFetchmail)
[http://download.gna.org/hpr/fetchmail/FAQ/gmail-pop-howto.html](http://download.gna.org/hpr/fetchmail/FAQ/gmail-pop-howto.html)
[http://www.axllent.org/docs/networking/gmail_pop3_with_fetchmail](http://www.axllent.org/docs/networking/gmail_pop3_with_fetchmail)
[http://souptonuts.sourceforge.net/postfix_tutorial.html](http://souptonuts.sourceforge.net/postfix_tutorial.html)

Do keep in mind that if you use the daemon then fetchmailrc needs to be chmod 600 and chown fetchmail:nogroup.  And of course Gmail settings for pop3 needs to be on.

---

