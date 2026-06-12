---
title: "Postfix spam problem"
date: 2008-05-18
forum: Server Platforms
---

### Post by self-defence on 2008-05-18
Hi,

I've got a bit of a problem. I was able to configure Postfix and Dovecot with a webmail client and I can receive and send emails. But over the last few weeks the spam count has risen considerably (from 4-5 spams/day to 50-90/day). I was told that Spam Assassin would be a good choice but I'm stuck I don't know where to start to set it up because I was under the impression that it was already running. But how to get it to filter at least some of the spam.
I think that I've got Spam Assassin installed (I did it via Webmin) but now how to proceed. 

Thank you for your help.

Bye

---

### Post by hyper_ch on 2008-05-19
postfix has some anti-spam mechanisms included... you may want to first filter by that and then by spamassassin...maybe even integrate greylisting.

Besides: Spamassassni will only mark email as spam... it will attach a spam probablity in a header of the email. With that, you can then select what do actually do when it hits a certain limit.

---

### Post by battista on 2008-05-19
Spamassasin is more or less unreliable and inefficient. At least, it filteres sometimes mail that you don't want to be filtered.


I am very happy with greylisting (google, wiki)

The basic function is that every incoming mail gets a busy mailserver the first time the mail comes in, and that due to some rfc every true mta will make several retries until it non-delivers. 

Spammers normally don't retry.

Greylisting allows you to define a time period (normally 5 minutes), after which the next mail attempt from the same origin will be accepted and stored.

This already eliminates about 95 % of all spam. 

The rest can be handled by other means.

RBL lists is an easy and reliable one. 

My main.cf looks like this (use whitelist for the sources you want to leave unchecked)

```

smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_rbl_client ix.dnsbl.manitu.net, check_client_access hash:/etc/postfix/whitelist, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit_auth_destination, reject_rbl_client pbl.spamhaus.org, reject

```

You may also find this url useful:

```

http://www.howtoforge.org/the-perfect-spamsnake-ubuntu-8.04

```

This worked fine for me, it schould do for you aswell. Without it, I would have 30 spammails per minute. Now, it's 3 or 4 a day that come through, but, more important, not any true mail recognized as spam. Of cource, you may add spamassasin aswell (for example to set a spamflag in the mailheader), but I wouldn't use it for other purposes.

---

### Post by hyper_ch on 2008-05-19
[http://ubuntuforums.org/showthread.php?t=799565](http://ubuntuforums.org/showthread.php?t=799565)

---

### Post by Monicker on 2008-05-19
> **battista said:**
> Spamassasin is more or less unreliable and inefficient. At least, it filteres sometimes mail that you don't want to be filtered.



Please elaborate on that statement.  Spamassassin in itself does not actually drop spam messages.  It assigns a score which indicates how likely it is that a message is spam.  I have run several spam filtering gateways at work using spamassassin, and never had much trouble with false positives.  I can confirm less than a half dozen false positives over the course of several years.  And I always quarantine spam messages for a month so that I can go back and check if someone complains about not receiving a message.  To use spamassassin correctly, you need to give it samples of known spam and known ham, so that it can adjust its bayes learning appropriately. We do get some false negatives, because I err on the side of caution in my rules and scores, but even the number of those is relatively low;  I just use them for further tweaking of the bayes learning.

I do like the idea of grey listing, but I have never truly needed to use it for our business.

---

### Post by Donb01 on 2008-05-19
Here is another possible option.  Yes, I know it is 2 years out of date, but I am still running it and it still catches a helluva lot of spam.

Yeah it takes a little config, and it's not all nice and tidy like an ISP spam filter that puts them in a folder you can look at (you can do that if you want, and I would to start out).  It keeps a log/backup of the last 100 (configurable) messages it processes, so if you check your log and something got dropped as spam you just add the address to your whitelist and copy the message from the 'spam dumpster' back into your mailbox using  cat msg.XxX >> /var/spool/mail/user  and it pops right back into the mailbox.

I have AVG E-Mail Server edition running, but that still lets a lot of spam through.  I have this thing set to mark mail 'blocked' at score 3 and 'spam' at score 5 (spam > /dev/null) and I have it check Habeas, Spamcop, SPEWS, AHBL and SURBL RBL lists.  It probably eliminates 99% of the spam that AVG misses, and if I get 5 or so false positives in a week I can live with that.  I just whitelist the addresses and move the mail back into my mailbox.  I will warn you it DOES NOT like Yahoo addresses and the occasional other free mail provider.  I refuse to whitelist the entire Yahoo domain so usually the first couple times a new person sends me mail on Yahoo it gets dropped and I have to add them to my list.

Anyway - here it is:  [http://www.spambouncer.org](http://www.spambouncer.org)

If you are seriously considering it and need config help I will be happy to help out (as long as I don't get inundated with mail!  I still talk to the developer, and she claims she is working on 3.0, but the last time she said that was maybe 6 months ago....

---

### Post by MJN on 2008-05-19
> **battista said:**
> Spamassasin is more or less unreliable and inefficient. At least, it filteres sometimes mail that you don't want to be filtered.

Each to his own opinion and all that, but this statement really is nonsense.

SpamAssassin is incredibly powerful and effective, and arguably one of the best spam filters available. Your experience of it has obviously led you to think otherwise but I would say this must have been down to your (mis)configuration if you were getting false-positives to any great degree.

I do however agree with you that greylisting is very effective (although I would not consider its use as an alternative to SpamAssassin but rather used in addition to to compliment it).

Mathew

---

### Post by battista on 2008-05-20
I still see spamassassin as a gimmick. 

On my systems, greylist and rbl do the job, and for those mails who come through spamassassin may set a spam mailheader flag so that these are sieve'd into a special imap subfolder. 

My experience with spamassassin as a primary filter mechanism is three years old. So that statement of mine may not be up to date any more.

Currently I do not need spamassassin, cause greylisting / rbl works fine.

---

### Post by self-defence on 2008-05-20
Wow thanks for all the replies. 

battista -> this graylisting sounds really simple and easy to setup. I think for the beginning I'll give it a try for starters. So I just have to add the line you pasted into main.cf and restart postfix?

Donb01 -> thanks, I'll take a look at SpamBouncer it looks interesting. I just hope I'll be able to figure it out. Lately it seems that I don't have enough time to get involved too much in anything and then I don't get anything done since I run into problems.

Thank you all again I hope I'll be able to do something about the spam.

Bye

---

### Post by self-defence on 2008-05-29
Hi,

I've just had some time and tried to play around with this graylisting but seems to filter out everything. :confused:

battista -> I added the line to main.cf and restarted Postfix and now no email come throw what so ever.

Any ideas?

Thanks, bye

---

### Post by MJN on 2008-05-29
Post your logs... (/var/log/mail.log specifically)

---

### Post by self-defence on 2008-05-31
Hi,

I've been trying to post my mail.log file but I'm unable to post even just the relevant part. Anything specific I should be aware of in the log file?

Thanks, bye

---

### Post by dragonator on 2008-05-31
I don't know how tied you are to using SA, but I would recommend a different tool to do the job.  I've been using ASSP for a couple of years and have been very pleased with it.  You should about a 70-80% drop in spam just by enabling the delaying option (greylisting) and leaving everything else in test mode.  

[http://assp.sourceforge.net/](http://assp.sourceforge.net/)

---

