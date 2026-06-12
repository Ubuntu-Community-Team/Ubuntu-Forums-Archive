---
title: "amavis and spam tag"
date: 2007-07-29
forum: Server Platforms
---

### Post by meimato on 2007-07-29
I configured a postfix mail server in Dapper, with amavis as spam filtering agent; it seem to work properly, cause if I specify 
$final_spam_destiny = D_BOUNCE; 
in my 20-debain_defaults, spam mails are not delivered to the mailbox (and I see in mail.log that amavis blocked spam).

The problem is that I'd like the email to arrive, while being tagged as ***SPAM*** in the subject; what parameter I have to specify in my 20-debian_defaults? If I put D_PASS amavis detect the email as spam, passes it the mailbox but doesn't add the ***SPAM*** tag...

---

### Post by Mr. C. on 2007-08-03
meimato,

Do you still need help on this ?

$sa_tag2_level_deflt controls insertion of spam headers and subject tagging.  You want this to be below sa_kill_level_deflt.

Don't BOUNCE spam - as you become a source of backscatter.  Use any of D_DISCARD, D_PASS, D_REJECT.

See: [http://marc.info/?l=amavis-user&m=118299304511514&w=2](http://marc.info/?l=amavis-user&m=118299304511514&w=2)

For Subject tagging, the recipient must be considered a local user, so make sure you have local_domain_maps correctly set.

MrC

---

### Post by meimato on 2007-08-06
Thank you for the reply, but (be patient) I've more to ask.
I'm testing amavis with GTUBE; I tried setting the $sa_tag2_level_deflt at 5.5 and sa_kill_level_deflt at 12, but:
- if I put D_DISCARD as final_spam_destiny, spam mail are not delivered to my inbox
- if I put D_PASS they are delivered but non subject tag is added

Where I have to specify the local_domains_map? Can you give me an example?

---

### Post by Mr. C. on 2007-08-06
This goes in the amavisd.conf file, but I believe Debian (and hence Ubuntu) stores this configuration in different locations.

GaryV has several documents describing the Debian install, and how to configure amavisd-new for various situations:
[http://www200.pair.com/mecham/spam/](http://www200.pair.com/mecham/spam/)

This is the overview of the configuration file breakdown:
[http://www200.pair.com/mecham/spam/debian-amavisd-new_2.4.2.html](http://www200.pair.com/mecham/spam/debian-amavisd-new_2.4.2.html)

In particular, this file apears to be the place to set local_recipient_maps:

[http://www200.pair.com/mecham/debian/2.4.2/05-domain_id](http://www200.pair.com/mecham/debian/2.4.2/05-domain_id)

MrC

---

### Post by meimato on 2007-08-06
Thank you very much, I'll give a look.
Just after posting i tried puttig local_domains_map here and there... it seems working if I put it inside 50-user


By the way: I'm using two different systems, one with Dapper and one with Feisty: Dapper doesn't have the 05-domain_id, but it seems working putting local_domains in 50-user.
Feisty has 05-domains_id: I'll try with that, too.
Again, thank you very much.

---

### Post by Mr. C. on 2007-08-06
That is good news.

If your want a breakdown of your spam stats, grab a copy of my amavis-logwatch utility:

[http://www.mikecappella.com/logwatch/](http://www.mikecappella.com/logwatch/)

MrC

---

