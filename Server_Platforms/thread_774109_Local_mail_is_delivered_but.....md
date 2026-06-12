---
title: "Local mail is delivered but...."
date: 2008-04-29
forum: Server Platforms
---

### Post by phos4us on 2008-04-29
Hi all,

I have set up an Ubuntu 7:10 server here at work. It will primarily be a mail server.

I am using Postfix and Cyrus.

My problem is that when I fetchmail from my pop account on the internet, the mail is collected and delivered locally (i.e. running 'mail' as the user lists the messages), but when I try to access them via either pop or imap the server responds telling me there is no mail in the mailbox.

Any suggestions as to what I am doing wrong?

Any assistance will be greatly appreciated.

Thanks
Andy

---

### Post by s13884 on 2008-04-29
Can you paste the output of the following commnad ?

First attempt to download the mail from your pop, then run the following command.
tail /var/log/mail.log 

May be we can get some help.

Cheers

---

### Post by phos4us on 2008-04-29
```
Apr 29 16:53:59 mail postfix/lmtp[27773]: B2B5A650810: to=<andrew@localhost>, relay=none, delay=10042, delays=10042/0.44/0/0, dsn=4.4.1, status=deferred (connect to mail.local[/var/run/cyrus/socket/lmtp]: No such file or directory)
Apr 29 16:53:59 mail postfix/lmtp[27772]: A2C8365081B: to=<andrew@localhost>, relay=none, delay=8908, delays=8908/0.44/0/0, dsn=4.4.1, status=deferred (connect to mail.local[/var/run/cyrus/socket/lmtp]: No such file or directory)
Apr 29 16:53:59 mail postfix/lmtp[27772]: A1A3F650830: to=<andrew@localhost>, relay=none, delay=8875, delays=8875/0.46/0/0, dsn=4.4.1, status=deferred (connect to mail.local[/var/run/cyrus/socket/lmtp]: No such file or directory)
Apr 29 16:53:59 mail postfix/lmtp[27773]: ABBBE65082B: to=<andrew@localhost>, relay=none, delay=8884, delays=8884/0.46/0/0, dsn=4.4.1, status=deferred (connect to mail.local[/var/run/cyrus/socket/lmtp]: No such file or directory)
Apr 29 16:53:59 mail postfix/lmtp[27772]: 3AF5C65082A: to=<andrew@localhost>, relay=none, delay=8886, delays=8885/0.47/0/0, dsn=4.4.1, status=deferred (connect to mail.local[/var/run/cyrus/socket/lmtp]: No such file or directory)
Apr 29 16:53:59 mail postfix/lmtp[27773]: 34CAD65082F: to=<andrew@localhost>, relay=none, delay=8877, delays=8876/0.47/0/0, dsn=4.4.1, status=deferred (connect to mail.local[/var/run/cyrus/socket/lmtp]: No such file or directory)
Apr 29 16:55:04 mail cyrus/master[27783]: about to exec /usr/lib/cyrus/bin/pop3d
Apr 29 16:55:04 mail cyrus/pop3[27783]: executed
Apr 29 16:55:04 mail cyrus/pop3[27783]: accepted connection
Apr 29 16:55:12 mail cyrus/pop3[27783]: login: [172.16.48.101] andrew plaintext User logged in

```

This is what I get from mail.log after a pop connection. If I run 'mail -f /var/spool/mail/andrew' I get a list of some 30 odd messages in my mailbox.

I see it is complaining about '/var/run/cyrus/socket/lmtp' not existing, but it does. It is owned by root.root. Is this likely to be the problem?

Thanks.

---

### Post by phos4us on 2008-05-05
I still have no idea why local mail is delivered but cannot be retrieved via pop or imap. This blows my mind. I can't even think of anything to try.

Any suggestion or ideas would be very appreciated.

Thanks

---

### Post by phos4us on 2008-05-07
Problem solved. At least sort of.

I set everything in master.cf to not chroot and now everything is working.

Is this a security risk or is it relatively safe? The machine is not currently connected directly to the internet but may be later on.

Regards
Andy

---

