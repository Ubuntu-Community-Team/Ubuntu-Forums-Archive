---
title: "How big of a server do I really need?"
date: 2011-01-19
forum: Server Platforms
---

### Post by Weareblkflag on 2011-01-19
Hello Unbuntu world. I am a seeking info on how large of a server will I really need to get the job done. Here is what I want to do.
Im looking at hosting 5-10 websites for small business and there e-mail.
Thanks alot in advance I have learned alot from these fourms.

---

### Post by SeijiSensei on 2011-01-19
You could do this on a P4 with 512MB of memory.  Hosting websites and e-mail is not particularly demanding.  That includes running PHP scripts and a backend PostgreSQL or MySQL database.

Now if you want to scan all the e-mail for viruses and spams using something like [MailScanner]("http://www.mailscanner.info/"), I'd suggest a bit more CPU.  Of course that depends on how much spam you receive.  I host some domains that get 5-10 spams a minute or so, and others that get hardly any.

---

### Post by SeijiSensei on 2011-01-19
double post

---

### Post by James78 on 2011-01-19
> **SeijiSensei said:**
> You could do this on a P4 with 512MB of memory.  Hosting websites and e-mail is not particularly demanding.  That includes running PHP scripts and a backend PostgreSQL or MySQL database.

**Now if you want to scan all the e-mail for viruses and spams** using something like [MailScanner]("http://www.mailscanner.info/"), I'd suggest a bit more CPU.  Of course that depends on how much spam you receive.  I host some domains that get 5-10 spams a minute or so, and others that get hardly any.
I use Postfix and [ClamSMTP]("https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto#ClamSMTP SMTP Virus Filter") for that. :D

---

### Post by wongo888 on 2011-01-19
If you need your own hardware, you can probably get away with buying a second hand server off ebay for a couple of hundred bucks.

For such a small job, a VPS would be cheaper. Here is a small VPS I maintain. It has 15 domains, mysql, postfix and a Java app running on Tomcat. It is idle most of the time.

```

top - 17:25:17 up 1 day, 18:10,  1 user,  load average: 0.13, 0.03, 0.01
Tasks:  35 total,   1 running,  34 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.0%us,  0.4%sy,  0.0%ni, 98.5%id,  0.1%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1048576k total,   271568k used,   777008k free,        0k buffers
Swap:        0k total,        0k used,        0k free,        0k cached

```

---

### Post by SeijiSensei on 2011-01-19
> **wongo888 said:**
> For such a small job, a VPS would be cheaper.

Indeed. I have a couple of $30/month [Linode]("http://www.linode.com/") virtual machines with 512MB for exactly these sorts of tasks.  I like the reliability of daily VM snapshots and having my server be housed in a facility with honking big generators and a fat pipe to the Internet.  I was also greatly impressed when I was able to access the VM as a filesystem remotely and reinstall the openssl RPM I accidentally deleted the other day.  (*Everything* is linked against libcrypto these days!)

> **James78 said:**
> I use Postfix and [ClamSMTP]("https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto#ClamSMTP SMTP Virus Filter") for that. :D

What about SpamAssassin?  Do you run spamd?

I generally run CentOS on servers and have found MailScanner the best overall mail-scanning application for the RHEL/CentOS platform.  It comes with a nice installer that builds or rebuilds any needed Perl modules along the way.  It operates entirely at the MTA level rather than at the delivery stage like spamd.  MailScanner is also incredibly configurable.

---

### Post by Neo@Matrix on 2011-01-19
I have 22 domains with numerous sub domains on server with:```
Top output: 
top - 04:09:39 up 6 days,  4:13,  1 user,  load average: 0.84, 0.24, 0.07
Tasks: 278 total,   3 running, 274 sleeping,   0 stopped,   1 zombie
Cpu(s):  5.9%us,  0.8%sy,  0.0%ni, 93.0%id,  0.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4059708k total,  3049176k used,  1010532k free,   165472k buffers
Swap: 11888060k total,    39396k used, 11848664k free,   474624k cached
```
 :)

---

### Post by James78 on 2011-01-20
1 site with not much traffic.. But that's going to change real soon. :)
```
top - 21:09:32 up  9:08,  1 user,  load average: 0.10, 0.15, 0.11
Tasks: 150 total,   1 running, 149 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.3%us,  0.3%sy,  0.2%ni, 99.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2053172k total,  1005228k used,  1047944k free,    53672k buffers
Swap:   974712k total,        0k used,   974712k free,   317804k cached
```
> **SeijiSensei said:**
> What about SpamAssassin?  Do you run spamd?

I generally run CentOS on servers and have found MailScanner the best overall mail-scanning application for the RHEL/CentOS platform.  It comes with a nice installer that builds or rebuilds any needed Perl modules along the way.  It operates entirely at the MTA level rather than at the delivery stage like spamd.  MailScanner is also incredibly configurable.
Yes, I also use SpamAssassin for occasional emails that get through (I have a nice config that prevents 90% of spam). ;)

---

### Post by Weareblkflag on 2011-01-20
Thanks alot. Right now im testing the sites I already have built with in my home network. Im running a old.. Optiplex Pent 4 with 512 ram. 
I know im going to go the VM route. Im thinking kick it up to 1.5 Gig of ram and call it a day.
 
Thanks for all the feedback
 
Also I have hear about Spam Assassin. I like what I know about it so far.

---

