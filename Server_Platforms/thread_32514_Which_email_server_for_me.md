---
title: "Which email server for me?"
date: 2005-05-08
forum: Server Platforms
---

### Post by DaturaX on 2005-05-08
Was wondering which email server is for me? I will want to configure using both GUI and console and this program must also provide webmail?

Anyone?

---

### Post by Xerampelinae on 2005-05-08
I've tried postfix and qmail.  I found postfix to have a nicer config file.  I got the impression qmail would be more useful to set up for a professional, high performance type setup though.

I'm not sure if there's a GUI config tool, but maybe webmin has something... I don't use webmin myself, so I can't say...

---

### Post by LordHunter317 on 2005-05-08
Don't ever use qmail in any new setups.  It's license is unfree and it's author (and the only who can legally mantain and distribute the entire codebase) refuses to work on it any more, so it slides into obsolesence.

Postfix and exim4 both trounce it terms of performance and featureset. My personal preference is for postfix, it's much eaiser to configure than exim4.

Postfix handles sending mail and delivering locally to the user's mail spool.  It doesn't handle POP/IMAP (end-user delievery) nor does it handle webmail.

For POP/IMAP the courier suite is a good choice.  This requires you use Maildirs, but that's a good thing, not a bad one.  It can do SSL.  This is my general choice for providing end-user delievery.

For webmail, squirrelmail or Horde/IMP are good choices.  Squirrelmail probably being easier to configure and setup than Horde/IMP.

For anti-virus and spam, I use mailscanner with clamav and SpamAssassin.  Mailscanner is a deamon that wraps around a bunch of anti-virus suites and SA to provide integrated checking and is much faster than any other solution I've seen.  It's a bit complicated to setup, but the payoff is worth it in the end.

---

### Post by Ric_ on 2005-05-09
I'd definately go with Postfix too being an ex-exim hardcore user Postfix is the future! It work very nicely with amavisd which will help you easily spam and virus scan with ClamAV and SpamAssassin.

---

### Post by robertbb on 2005-05-11
Could someone please comment on the relative merit of comparable (and competing) antivirus 'helper-daemons' such as amavisd and mailscanner?

I'm looking to implement one soon, but can't seem to differentiate between the options.  I'm after a brief technical, administrative and feature comparison..

Thanks in advance

---

### Post by Ric_ on 2005-05-12
Well as i stated before I run Postfix.

Hooked onto that I have amavisd-new. Now this was designed for Postfix so intergration is very well documented.

What amavisd-new does is use other programs such as spam assassin and clamav. These are extremly simple to intergrate. I have found a guide for debian so this should work with Ubuntu. Just ignore the first few chapters about changing apt sources and stuff.

[http://www200.pair.com/mecham/spam/spamfilter20041003.html](http://www200.pair.com/mecham/spam/spamfilter20041003.html)

That should  give you an excellent start into building your system. Amavisd will call spam assasin and clam when it needs then. You can set spam levels and quarentine directories for clam and SA in the one conf file.

I'm currently running two of these as promary and secondary MX, to filter mail before it hits the NT boys servers. Works a treat!

---

### Post by jimcooncat on 2005-05-12
[QUOTE=LordHunter317]Don't ever use qmail in any new setups.  It's license is unfree and it's author (and the only who can legally mantain and distribute the entire codebase) refuses to work on it any more, so it slides into obsolesence.[/QUOTE]
I've been using qmail for a while, and it's a very stable solution for what it does. The author, though, didn't address spam tagging or antivirus support, leaving that to others. This is the main problem I've been running into -- the additional support programs needed (like qmailscanner) to provide a full service just aren't up to the same quality as qmail itself.

Also, qmail uses weird locations in the file system hierarchy, and the license refuses to allow distributors to install the files in sane locations. But it sure does run well! The end result, though, is I wouldn't set up a new mail server with it, either.

---

