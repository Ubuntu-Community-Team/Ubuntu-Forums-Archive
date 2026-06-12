---
title: "Mail Server Setup, NEED Help!"
date: 2007-11-29
forum: Server Platforms
---

### Post by go_beep_yourself on 2007-11-29
I am trying to setup the following, and I have made some progress. Here's my setup.

[LIST]
[*]Fetchmail (downloads from my gmail account)
[*]Mutt (I need to recompile it to use an encryption plugin and compression for email)
[*]Evolution (Reads mail that Fetchmail downloads, and needs to be able to use Postfix for sending emais)
[*]Procmail (Sorts my email with regular expressions and prints certain emails, I also need to set it up in conjunction with Spam Assassin)
[*]Fetchyahoo (downloads emails from my yahoo account because pop3 access is not free for those who sign up with and choose usa as their country)
[*]Mailman (I'm still trying to figure out what I am going to use this for, but I think it would be very cool and useful to learn.)
[*]Postfix (smtp server for relaying mail to a smarthost.)
[/LIST]

Here are my questions.

[LIST=1]
[*]How can I know if I need SASL when setting up Postfix?
[*]How can I know if I need SMTP Authentication?
[*]Do I need it because gmail uses it even though I will be relaying mails to my internet?
[*]Should I configure Postfix to use mbox or Maildir format?
[*]Why should I configure it to use one or the other?
[*]Does Fetchmail use mbox or Maildir?
[*]Which one does it use by default?
[*]Should I configure Postfix to use the same as Fetchmail?
[/LIST]

---

### Post by MJN on 2007-11-29
> **go_beep_yourself said:**
> Here are my questions.
[LIST=1]
[*]How can I know if I need SASL when setting up Postfix?
[*]How can I know if I need SMTP Authentication?
[*]Do I need it because gmail uses it even though I will be relaying mails to my internet?
[*]Should I configure Postfix to use mbox or Maildir format?
[*]Why should I configure it to use one or the other?
[*]Does Fetchmail use mbox or Maildir?
[*]Which one does it use by default?
[*]Should I configure Postfix to use the same as Fetchmail?[/LIST]
 
Deep breath....
 
1. If you want to use your server for sending mail _from remote clients_ (e.g. connecting with a mail client from outside your network) then you will need some form of client authentication otherwise you'll be acting as an open relay. Hence, some form of external authentication process is required and SASL is as good as any.
 
2. As above, if you need remote access you need it (unless you plan on using a webmail interface which would handle its own authentication).
 
3. Are you sending outgoing mail via Gmail's servers, or your ISPs? I don't use Gmail from what I recall from reading posts on here it does indeed require authentication - this is not the same as your client authentication and so doesn't need external SASL support (but would still use the SMTP AUTH built in to Postfix).
 
4. An endless debate (search for discussions) but I prefer maildir by a long way mainly down to the simple storage mechanism (unmodified one-message-per-file architecture) the lockless operation (useful with busy systems with distrubuted storage).
 
5. Only you can decide. If it makes it easier I recommend going with maildir unless you can find a good reason for you to do otherwise.
 
6. Neither - it doesn't perform local delivery hence is format-independent.
 
7. N/A given the above.
 
8. N/A given the above.
 
If I were you I'd take this thing one step at a time as you've got a bit of ground to cover! (There's your cue Herman! :))
 
Mathew

---

### Post by HermanAB on 2007-11-29
Installing Postfix is a great learning experience, but if you want something that works, does absolutely everything you want and more and be done with it in about 20 minutes flat, then look at this: [http://www.citadel.org](http://www.citadel.org)

Cheers,

Herman

---

### Post by go_beep_yourself on 2007-11-29
> **MJN said:**
> Deep breath....
5. Only you can decide. If it makes it easier I recommend going with maildir unless you can find a good reason for you to do otherwise.


Why not Maildir++? I just recently found out about it. Is it not supported by Postfix?

---

### Post by MJN on 2007-11-29
Despite its name Maildir++ is a simple extension of maildir and, for all intents and purposes, can be regarded as being the same. The only differences are a slight tweak of the folder layout and folder quota sizes.

Postfix, and indeed most other mail-related applications, will be quite happy working with Maildir++ but it's not something that needs concern you either way.

Mathew

---

