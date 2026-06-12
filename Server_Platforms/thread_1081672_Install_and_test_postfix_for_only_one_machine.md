---
title: "Install and test postfix for only one machine"
date: 2009-02-26
forum: Server Platforms
---

### Post by gui076 on 2009-02-26
Hello all,

I have one PC with kubuntu on it.

I would like to create a mail serveur on it and send e-mail to itself.

I found a lot of tutorial using a specific domain name but not for doing what I want.

So I was thinking using 127.0.0.1, is it possible ?
If yes I will really appreciate a little help :-)

Regards,

---

### Post by E_K on 2009-02-26
first lets get the reason while you would want to mail your self on the same machine straight

wouldnt that machine that is mailing the information already have the information on it, that you want mailed in the first place?

Sorry, though it seems pointless to email say machine #1 when machine #1 already has that information on it.

---

### Post by gui076 on 2009-02-26
Hi,

Because I have only one laptop to test the mail server.
and I think it would be possible to create a database in a second time and tests others functions...

---

### Post by albinootje on 2009-02-26
> **gui076 said:**
>  I would like to create a mail serveur on it and send e-mail to itself.

If you install postfix on your machine, and choose "Local only" during the initial postfix (deb package) configuration, then you can send emails to yourself through postfix on your machine.

Test sending emails with Mutt :
```

sudo apt-get install mutt

```
You can also try Alpine instead of Mutt, just fill in your local username in the To: field, edit the body and send it.
I've just tested it on my desktop machine and it works fine.

---

### Post by E_K on 2009-02-26
good info and all but the point?

---

### Post by gui076 on 2009-02-26
it works with mutt but is it an imap or pop system ?

and I would like to use thunderbird instead of mutt :-)

---

### Post by gui076 on 2009-02-26
I installed courier-imap package and it is working like I want :-)

thanks for your help guys :-)

---

