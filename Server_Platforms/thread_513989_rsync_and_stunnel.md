---
title: "rsync and stunnel"
date: 2007-07-31
forum: Server Platforms
---

### Post by NeillHog on 2007-07-31
Two weeks ago I did not know what Linux was and now I am still an absolute beginner but, thanks to these forums, I am not going back to Windows :-)

I have been backing up off site for a few years with iBackup.com and this week I got my backup to them working again with rsync.

I use
$ rsync -r -v -z -t <your_directory> <ibackup username>@rsync.ibackup.com::ibackup
which then asks for my password and then everything works a s it should

So the backup is working but I would like it to be secure.

I have stunnel 3.26 installed on my system so I followed the instructions from iBackup:
Run Stunnel on your UNIX or linux server:
$ stunnel -c -d localhost:45873 -r rsync.ibackup.com:5000
and then run rsync through your local stunnel to encrypt the connection to IBackup using SSL.
$ rsync -r -v -z -t /home/mydata john@localhost::ibackup --port=45873

I receive the following eror messages:
rsync: failed to connect to rsync.ibackup.com: Connection refused (111)
rsync error: error in socket IO (code 10) at clientserver.c(98)
neither of which tell me anything and an internet search doesn't help either.

I have tried switching off the firewall in my DSL router but that did not help either.
Can anyone point me in the right direction?

Thanks!

---

### Post by jtc on 2007-07-31
Never mind. I didn't read the question properly

---

### Post by NeillHog on 2007-08-01
Better a wrong answer than none at all.
Looks like this is a really difficult question :-(

---

### Post by NeillHog on 2007-08-12
A week later and I am no further on this.
If any one ever finds an answer please let me know - even if it is in a few months.
Thanks!

---

### Post by dscherry on 2007-08-12
Hi,
I don't have an account with iBackup, so this is pure guesswork.  The error message indicates a failure to connect, which hints that you got out to their server, but either had wrong account info, password, or port number.
On the iBackup web page, they give general instructions, which you posted.  Are they the same as the specific instructions they offer when you enter your account/email info on their site?  (As I said, I don't have an account, so I don't know if they tweak the login for each account).
That's all I can think of to verify.  If that doesn't help, you could try their on-line or telephone tech support.  They claim it's included with having an account.

hth,
Dan

---

### Post by NeillHog on 2007-08-12
Thanks.
I am glad to hear that you think the problem is at "their" end.
I had sent a report request but received no answer. I just tried again and tomorrow I will ring.

Thanks again
Neill

---

### Post by dscherry on 2007-08-12
I suspect the 'problem' will be something you have to fix or configure at your end, but I do think iBackup will be the one who has to specify what that is.  They're the ones with the 'locked' door.  They have to tell what keys let you in.  You have to set up the keys accordingly.  Hopefully it will be something minor.

Good luck with it...
Dan

---

