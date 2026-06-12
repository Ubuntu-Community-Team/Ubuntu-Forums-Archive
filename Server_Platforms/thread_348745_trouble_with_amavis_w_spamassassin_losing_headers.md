---
title: "trouble with amavis w/ spamassassin losing headers"
date: 2007-01-29
forum: Server Platforms
---

### Post by deuce868 on 2007-01-29
I have a mail server setup with dapper using amavisd and spamassassin. My trouble is that I have messages getting through and they don't have a spam status header. I have set in /etc/amavis/conf.d

$sa_tag_level_deflt = -5.0

I can find the messages in the mail.log and they have a spam score:
i.e. 

> 
Jan 27 12:26:38 dc amavis[29272]: (29272-07) Passed CLEAN, [82.243.11.135] <apyiylyoxoo@proxad.net> -> <gary@xxxxxxx.com>, Message-ID: <DA04E893A9D413A.EF924FBA3F@proxad.net>, mail_id: oEb3J3Yzom-M, Hits: 4.787, 5553 ms


The message does not have a spam score header added to it though. Other messages do have the header so I can't seem to figure out why these messages don't. 

Any ideas? The main trouble is that I'm trying to see what rules these messages that get through hit in spamassassin so I can tweak the scoring of the rules and get them blocked. 

Thanks for any help

---

### Post by Juzz on 2007-03-14
Do you have a learning script setup to allow SpamAssassin to learn what is spam and what is not?

There are a few learning scripts here:
[http://workaround.org/moin/PostfixTutorialContributions](http://workaround.org/moin/PostfixTutorialContributions)

I have used one of them myself to create a script that suited my setup.

---

### Post by deuce868 on 2007-03-14
I turned off most of the auto stuff like that. I found that since we get a large majority of good mail, it would be more lenient from certain domains letting forwarded spam through from those domains. 

I eventually got an answer to my initial problem. I had to add the domains I host into the spamassassin config so that it would add in the headers and such.

---

### Post by Juzz on 2007-03-14
There's nothing auto over those scripts - it reads the junk maildirs of specific (or all) users...

I modified one of the scripts to only read my junk maildir for spam and then read my inbox for ham - and I activate that script once I've collected a bunch of spam...

---

