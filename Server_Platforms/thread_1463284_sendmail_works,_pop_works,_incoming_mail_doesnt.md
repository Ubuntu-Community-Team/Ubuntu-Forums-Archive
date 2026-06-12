---
title: "sendmail works, pop works, incoming mail doesnt"
date: 2010-04-26
forum: Server Platforms
---

### Post by mellowfish on 2010-04-26
I created some email accounts on my personal server awhile ago. postfix+courier with virtual mapping for a second domain I own.

These accounts work great.

However: today I went to add another one. I added it to the virtual file, postmap'd it, restarted postfix (not sure if needed) and ran maildirmake.

The outcome: I can send myself mail at the new address using sendmail from my server where all the accounts are. 
I can grab those emails I just sent via pop3 into my gmail inbox automagically (still love that feature of gmail).

But I cannot send myself email to this location from anywhere else (other email accounts).

I can't figure out what the difference is between this new account and my other three that work just fine.

Any help would be appreciated, or a pointer to a good how-to (I cound't find one that covered setting up new accounts *after* an installation).

I would really like to start being able to set up a lot of email accounts since I am finally starting to use this other domain, but apparently I need a refresher on how to do it.

---

### Post by Iker Etxebarria on 2010-04-27
Can you put the result of the ```
tail /var/log/mail.log
``` command?

---

### Post by uberlinuxnerd on 2010-04-27
First things first, I would check your MX records are good for your second domain. There are plenty of tools online (google will reveal all!) to do this for you. After that is confirmed good/bad can you post your configs?

---

### Post by mellowfish on 2010-04-27
uberlinuxnerd:
> I know both my domains have valid mx records because I have working email accounts on both domains.  Only this new address is not working, and it happens to be a virtual account since it is on my second domain.

Or so I thought. Thanks for the pointer to the mx records, those were the problem.

---

