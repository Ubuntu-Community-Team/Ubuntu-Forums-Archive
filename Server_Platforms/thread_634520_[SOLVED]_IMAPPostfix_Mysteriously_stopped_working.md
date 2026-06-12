---
title: "[SOLVED] IMAP/Postfix Mysteriously stopped working"
date: 2007-12-07
forum: Server Platforms
---

### Post by charmcity on 2007-12-07
Hi,

I'm looking for clues - I've been going over the logs and trying to understand why my email has stopped receiving messages.  Everything was working fine - postfix recieving mail, handing it off to Cyrus IMAP mailboxes via a local LMTP connection.  I did change my ethernet NIC today - however it is working fine, I have connectivity, the IP address is the same, I don't see how this could be the problem, all that's changed is my MAC address and I have even made sure to change this new interface to eth0 on my linux box

Does anyone see anything in the log snippet below that could be a clue to the problem?  I just don't see it:

```
Dec  7 19:03:02 tommy postfix/pickup[6301]: 662242C06FC: uid=1001 from=<genesisma>
Dec  7 19:03:02 tommy postfix/cleanup[6419]: 662242C06FC: message-id=<20071208000302.662242C06FC@tommy.bostonst.com>
Dec  7 19:03:02 tommy postfix/qmgr[6302]: 662242C06FC: from=<genesisma@bostonst.com>, size=852, nrcpt=1 (queue active)
Dec  7 19:03:02 tommy cyrus/lmtpunix[6601]: accepted connection
Dec  7 19:03:02 tommy cyrus/lmtpunix[6601]: lmtp connection preauth'd as postman
Dec  7 19:03:02 tommy cyrus/lmtpunix[6601]: WARNING: sieve script /var/spool/sieve/g/genesisma/defaultbc doesn't exist: No such file or directory
Dec  7 19:03:02 tommy cyrus/lmtpunix[6601]: duplicate_check: <20071208000302.662242C06FC@tommy.bostonst.com> user.genesisma       0
Dec  7 19:03:02 tommy cyrus/lmtpunix[6601]: duplicate_check: <20071208000302.662242C06FC@tommy.bostonst.com> user.genesisma       0
Dec  7 19:03:02 tommy cyrus/lmtpunix[6601]: mystore: starting txn 2147483677
Dec  7 19:03:02 tommy cyrus/lmtpunix[6601]: mystore: committing txn 2147483677
Dec  7 19:03:02 tommy cyrus/lmtpunix[6601]: duplicate_mark: <20071208000302.662242C06FC@tommy.bostonst.com> user.genesisma       1197072182 1872
Dec  7 19:03:02 tommy cyrus/lmtpunix[6601]: Delivered: <20071208000302.662242C06FC@tommy.bostonst.com> to mailbox: user.genesisma
Dec  7 19:03:02 tommy postfix/lmtp[6422]: 662242C06FC: to=<genesisma@bostonst.com>, orig_to=<genesisma>, relay=tommy.bostonst.com[/var/run/lmtp], delay=0.05, delays=0.03/0/0/0.01, dsn=2.1.5, status=sent (250 2.1.5 Ok)
Dec  7 19:03:02 tommy postfix/qmgr[6302]: 662242C06FC: removed

```

The error I'm getting from Fetchmail running on my server  (which is polling an external POP3 mailbox every minute) is:

```
fetchmail: SMTP connect to tommy.bostonst.com failed
fetchmail: SMTP transaction error while fetching from tomp@mail.genesismidatlantic.com and delivering to SMTP host tommy.bostonst.com
fetchmail: Query status=10 (SMTP)

```

Help! Please

Thanks and Best Regards,
Tom

---

### Post by charmcity on 2007-12-07
Solved!

Ha -- Always solve it right after you resort to posting your problems don't ya?

The answer is that I also updated my "Domain" name while playing around with my settings.  The ubuntu app changed my hosts file in /etc and appended an extra .bostonst.com  to tommy.bostonst.com  (making it tommy.bostont.com.bostonst.com)  Hence it was not resolving correctly in my setup.   Found this to be the problem by trying to ping my server (from myserver).  

Cheers,

Tom

---

