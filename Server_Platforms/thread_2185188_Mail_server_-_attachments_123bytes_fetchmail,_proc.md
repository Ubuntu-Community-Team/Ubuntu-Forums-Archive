---
title: "Mail server - attachments 123bytes fetchmail, procmail, msmtp"
date: 2013-11-01
forum: Server Platforms
---

### Post by jake.cryer on 2013-11-01
I'm using fetchmail , procmail and msmtp as an auto forward for a cisco unified messaging (UC540) IMAP.

Basically a voicemail is left and fetchmail gets the mail, procmail filters to the correct destination and msmtp sends it. All that is working fine.

What isn't working is the voicemail that is attached as a .wav is getting screwed up somewhere. When i receive the email with the attachment it is always 123bytes. 

.fetchmailrc has limit 0 specified in options

in the msmtp log file the mailsize varies 

I feel like its a size restriction somewhere but I cannot figure out where. 


extra info: I've proven the voicemail files are fine from the cisco box using outlook on a windows server to forward voicemails. It works but outlook runs like garbage.

---

### Post by SeijiSensei on 2013-11-01
Let's try breaking the problem apart a bit.  In the relevant .procmailrc add a line to default delivery recipe to forward a second copy of the message to another account like this:

```

:0c
/home/extra/mail/voice

```

Are the messages identical? Now what if you replace that rule with
```

:0c
! someone@example.com

```

---

### Post by jake.cryer on 2013-11-01
The copied messages are all the same size no matter how long the the voicemail. 
So either fetchmail isn't pulling it in right or procmail is messing it up. That at least eliminated msmtp from the problem.
```

-rw------- 1 jake jake 790 Nov  1 14:35 msg.nAgd
-rw------- 1 jake jake 790 Nov  1 14:39 msg.oAgd
-rw------- 1 jake jake 790 Nov  1 14:37 msg.pAgd
-rw------- 1 jake jake 790 Nov  1 14:33 msg.YAgd

```

---

### Post by jake.cryer on 2013-11-01
Fetchmail log shows its pulling in different size files. 
```

fetchmail: IMAP< * 1 FETCH (RFC822.SIZE 23068)
fetchmail: IMAP< * 2 FETCH (RFC822.SIZE 514386)

```

but later in the log and for all messages it shows.
```
fetchmail: reading message 1 of 2 (358 header octets) (log message incomplete)
fetchmail: reading message 2 of 2 (358 header octets) (log message incomplete)
```

---

### Post by jake.cryer on 2013-11-08
replaced fetchmail with getmail and issue is resolved.

---

