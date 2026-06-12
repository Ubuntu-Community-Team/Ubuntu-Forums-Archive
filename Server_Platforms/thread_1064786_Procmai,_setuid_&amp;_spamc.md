---
title: "Procmai, setuid &amp; spamc"
date: 2009-02-09
forum: Server Platforms
---

### Post by CrimsonRider on 2009-02-09
Hi, I am migrating my current Gentoo mailbox to my new Ubuntu 8.10 server. So far it all seems to work, however I run into a problem with configuring spamd/spamc and procmail, postfix.

For some reason, it doesn't set the uid to the user of the recipient, instead, it keeps falling back via root to nobody.

```

Feb  9 14:22:48 [spamd] spamd: connection from ruby [127.0.0.1] at port 56136_
Feb  9 14:22:48 [spamd] spamd: setuid to micheal succeeded_
Feb  9 14:22:48 [spamd] spamd: processing message <ded3019dc242$64179ccc$ac2d5877@fiiqmx.net> for micheal:1049_
Feb  9 14:22:48 [postfix/smtpd] disconnect from ppp-58-9-43-110.revip2.asianet.co.th[58.9.43.110]
Feb  9 14:22:49 [spamd] spamd: identified spam (32.0/5.0) for micheal:1049 in 1.2 seconds, 6148 bytes._

```
This snippet above shows what it should be, how it is on the current server.

This snippet below shows what it is now, on the new server;

```

Feb  9 14:07:29 ruby spamd[4863]: spamd: connection from localhost [127.0.0.1] at port 46501
Feb  9 14:07:29 ruby spamd[4863]: spamd: setuid to root succeeded
Feb  9 14:07:29 ruby spamd[4863]: spamd: still running as root: user not specified with -u, not found, or set to root, falling back to nobody
Feb  9 14:07:29 ruby spamd[4863]: spamd: processing message <49902A37.609@something.net> for root:65534

```

It falls back to nobody. How do I set it so, that postfix will excute procmail as the correct uid and procmail will trigger spamc as that uid?

For the record, here is the relavant part of the procmailrc
```

:0fw: spamassassin.lock
* < 524288
 | spamc
```

I've done some googling, but can't seem to find a solution. Any help would be appreciated.
and the postfix entry to use procmail;
```
mailbox_command = /usr/bin/procmail
```

---

### Post by CrimsonRider on 2009-02-10
Nobody has a clue?

Why doesn't postfix or procmail do a nice setuid before runing spamc?

---

### Post by jr mcfly on 2009-03-14
I'm having this exact problem as well.  Previous combinations of these packages worked flawlessly.  Anyone with any ideas???

---

### Post by jr mcfly on 2009-03-15
Additional information on my case: I have the log file messages described below, which are annoying but harmless (I think).  But, my real problem is that messages identified as Spam are placed in the users' Spam mailbox with permissions of "root:mail".  This means users cannot read them, and Squirrelmail will throw an error about permissions when it tries to read that folder.   Non-spam messages are fine.  

I've since tried the following:

in procmailrc, I've changed the command:

|/usr/bin/spamc

to:

|/usr/bin/spamc -u $LOGNAME

where LOGNAME is a procmail variable that holds the user that procmail is being executed on behalf of.  This solves part of the problem - now spamc is running setuid to the correct user, and the log messages about running as "nobody" have stopped.  CrimsonRider, this might solve your problem.

However, for me, the root cause of the problem still remains: messages that are identified as spam are still owned by root:mail, not by the user.

---

### Post by jr mcfly on 2009-03-17
solved - adding "DROPPRIVS=yes" in /etc/procmailrc solved the permissions problem.  Spamc started up setuid OK after this as well, I was able to remove the "-u $LOGNAME" from the spamc command.  Enjoy...

---

