---
title: "Simple mail forwarder"
date: 2009-02-17
forum: Server Platforms
---

### Post by yannos on 2009-02-17
Hello all. I'm want to know if there is something I could use to download mail from a POP account, store it in a local maildir, and then forward it to another address. I'm looking at procmail, but it's kinda intimidating. Is there something a bit more simple I could use?

---

### Post by songshu on 2009-02-17
> **yannos said:**
> Hello all. I'm want to know if there is something I could use to download mail from a POP account, store it in a local maildir, and then forward it to another address. I'm looking at procmail, but it's kinda intimidating. Is there something a bit more simple I could use?

procmail seems to me the best way to do this.

what problem you have with procmail?

---

### Post by yannos on 2009-02-17
I will give it a try then, tonigh when I'm home. I read a bit about it and somewhat got a little scared :)

---

### Post by songshu on 2009-02-17
its not as big a hurdle as it seems, just give it a try and come back to us if you need more help ;)

---

### Post by HermanAB on 2009-02-17
You need Fetchmail, Procmail and Nullmailer.

Cheers,

Herman

---

### Post by yannos on 2009-03-12
Hello, I'm back :)
I finally had some time to mess with this and I think I'm close. I use getmail to download mail from my main account. I have 2 rules for each mail received, one save it to my local Maildir, the other send it to procmail. In my .procmailrc I have:

```
:0
* !^FROM_DAEMON
* !^FROM_MAILER
| mail yannos@gmail.com
```

So, any mail not from a daemon or mailer will catch this rule and use mail to actually send the mail elsewhere (my gmail account). This is what I got in procmail's log:
```

Subject: testing 1-2
Folder: mail yannos@gmail.com 1800
```

and I never receive the message. So I think the only part that is wrong is how to send back the mail. I think my mail command is part of the postfix package (witch I just installed and configured so it uses my isp smtp server) but I'm not even sure.

I'm getting there!

---

### Post by yannos on 2009-03-12
Ok I got it. 

```
:0
* !^FROM_DAEMON
* !^FROM_MAILER
! yannos@gmail.com
```

and setting myhostname in mail.cf to something valid seems to do the trick.

---

