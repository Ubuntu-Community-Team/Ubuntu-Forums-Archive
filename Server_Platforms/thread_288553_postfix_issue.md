---
title: "postfix issue"
date: 2006-10-30
forum: Server Platforms
---

### Post by ryjac on 2006-10-30
Anyone know where i can change the bolded text? 

if so, would anyone know what the usual values are? I realize that they probably change from service to service.
Oct 29 23:37:55 mybox postfix/pickup[14660]: 45D9E14295: uid=1000 from=<currentUser>
Oct 29 23:37:55 mybox postfix/cleanup[15283]: 45D9E14295: message-id=<20061030043755.GA15265@mybox>
Oct 29 23:37:55 mybox postfix/qmgr[4926]: 45D9E14295: from=<currentUser@mybox>, size=417, nrcpt=1 (queue active)
Oct 31 23:37:56 mybox postfix/smtp[15285]: 45D9E14295: to=<email.domain@gmail.com>, relay=mail.dslHost.net[xx.xxx.xxx.xxx], delay=1, status=bounced (host mail.dslHost.net[xx.xxx.xxx.xxx] said: 553 **mybox.dslHost.net** does not exist (in reply to MAIL FROM command))



i've searched everywhere, including /etc/postfix/main.cf.

---

### Post by MJN on 2006-10-30
Set **myhostname** in /etc/postfix/main.cf to be fully qualified i.e. mybox.whatever.your.domain.is.
 
By default, **mydomain** will use the latter part, and then **myorigin** will use **mydomain.** End result = domain on the end of the your From: addresses (if not specified). Speaking of which, what client are you using to send your mail? And is it not configured with your From: address?
 
Mathew

---

### Post by ryjac on 2006-10-30
I'm currently testing with mutt.

I'm glad you brought up my from address. I thought I was prompted to type it in, but I never was after double checking.

So I tested again with telnet and put in my email address for the from and it works. 

I guess I have to figure out how to set my from in mutt.

Thanks MJN.

---

