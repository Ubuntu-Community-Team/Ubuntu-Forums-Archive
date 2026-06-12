---
title: "Secondary Email Server"
date: 2007-05-11
forum: Server Platforms
---

### Post by roynencore on 2007-05-11
New to linux, I need help in setting up a secondary email server for work. I was able to install Ubuntu server software. I did research on the web learn how to step up email server and dns records. After reading variety of information believe got the DNS figured out but confused on how to proceed with setting up the secondary email server. Need a good tutorial on how to setup secondary email server and learn from.

Plee from Linux nOOb eager learn.

---

### Post by elst on 2007-05-12
It's no different from setting up a primary, except that you definitely want it to pass messages on to a separate system, whilst in lots of cases the primary SMTP server is also the POP or IMAP server, and so the mail stops there. There's probably not much point having more than one SMTP server unless the mail is stored on a separate system to the SMTP servers.

---

### Post by roynencore on 2007-05-18
Let's say primary server is under going some maintenance. Mail gets bounced when primary email server is down. A secondary server is put into place to catch those emails until primary is backup and running. Secondary server senses the primary is backup and running and sends it all the queued mail. International emails are important to international operations and maintenance usually happens late at night state side but international time difference becomes an issue.

Problem there is no clearly written tutorial information on how to set up a secondary email server for somebody just getting into Linux.  I was hoping the forum users could provide information. I sure not only one look for this type of information. :confused:

---

### Post by elst on 2007-05-18
Remember that delivery failures are expected - legitimate servers will retry several times if the first attempt fails, so you don't permanently lose mail if your SMTP service is temporarily offline. If you store your mail on the primary then having a secondary doesn't help your users much, because they can't access their mailboxes whilst the primary server is offline, so maintaining a genuine never-interrupted mail service probably requires at least 4 boxes - two relays and two access and/or storage servers. At that point, you are at the level where paying for training or specialist consultants is justifiable.

You add a secondary mail server by installing an SMTP service on a separate system and configuring it to forward only (to whichever system actually stores mail), and then just registering another MX in your DNS domain for the secondary. Remember that you need to run filtering on all mail before it hits user mailboxes, so any alternative mail route must have the same level of filtering as the primary.

EDIT: You can pay for other people to run a secondary mail service for your domain, in which case all you have to do is add the MX for their server to your DNS domain. That may be more cost-effective than maintaining your own, but I haven't looked into it closely.

---

### Post by rickyjones on 2007-05-18
I want to go ahead and say that this /shouldn/t be that difficult. I've never done though but I am also interested in a HOWTO for it. Any one have experience in this?

-Richard

---

### Post by MJN on 2007-05-18
> **roynencore said:**
> Let's say primary server is under going some maintenance. Mail gets bounced when primary email server is down.<snip>

Stop! ;)

Mail doesn't get bounced, it gets queued on the sending MTA and retried after a period. These retries will continue until it's own configurable timeout is reached - this in practice is usually a matter of days so plenty... if your MTA is not back within that time then you've probably got bigger problems anyway...

I'm not saying a backup MTA is a bad idea (although there are disadvantages, particular for spam filtering), more just pointing out that your requirement for one may not be as critical as you think.

Mathew

---

