---
title: "postfix + dspam wrong path for digest files"
date: 2010-04-07
forum: Server Platforms
---

### Post by hippysurfer on 2010-04-07
Hi

I am struggling to get dspam to work properly.

I have follow the instructions ([https://help.ubuntu.com/community/Postfix/Dspam]("https://help.ubuntu.com/community/Postfix/Dspam")) to the letter but when I send spam/ham to the [email]ham@mydomain.net[/email] address I see a problem in the logs.

The problem appears to be that when dspam filters the mail it stores the digests in:

                           /var/spool/dspam/data/mydomain.net/<user>

But when it tries to find the digests to add them to the spam/ham database it looks in:


                           /var/spool/dspam/data/local/<user>

But I can not find anywhere in the config that controls this. 

As I followed the instructions on the ubuntu  forums I can not be the first person to see this problem.

Any pointers?

Richard

logs:

> 
Apr  7 22:27:02 rat postfix/smtpd[19662]: connect from localhost[127.0.0.1]
Apr  7 22:27:02 rat postfix/smtpd[19662]: EAC8AE0B6A: client=localhost[127.0.0.1]
Apr  7 22:27:03 rat postfix/cleanup[19659]: EAC8AE0B6A: message-id=<0D3D54F4-4E18-4EE8-88F7-DE7D4B9A45C2@mydomain.net>
Apr  7 22:27:03 rat postfix/qmgr[18849]: EAC8AE0B6A: from=<rjt@mydomain.net>, size=3165, nrcpt=1 (queue active)
Apr  7 22:27:03 rat dspam[19665]: Unable to open file for reading: /var/spool/dspam/data/local/rjt/rjt.sig/4bbcf8a653512168214050.sig: No such file or directory
Apr  7 22:27:03 rat dspam[19665]: Signature retrieval for '4bbcf8a653512168214050' failed
Apr  7 22:27:03 rat dspam[19665]: Unable to find a valid signature. Aborting.
Apr  7 22:27:03 rat dspam[19665]: process_message returned error -5.  dropping message.
Apr  7 22:27:03 rat dspam[19666]: Unable to open file for reading: /var/spool/dspam/data/local/rjt/rjt.sig/4bbcf8a653512168214050.sig: No such file or directory
Apr  7 22:27:03 rat dspam[19666]: Signature retrieval for '4bbcf8a653512168214050' failed
Apr  7 22:27:03 rat dspam[19666]: Unable to find a valid signature. Aborting.
Apr  7 22:27:03 rat dspam[19666]: process_message returned error -5.  dropping message.
Apr  7 22:27:03 rat dspam[19667]: Unable to open file for reading: /var/spool/dspam/data/local/rjt/rjt.sig/4bbcf8a653512168214050.sig: No such file or directory
Apr  7 22:27:03 rat postfix/smtpd[19662]: disconnect from localhost[127.0.0.1]

---

### Post by lame666 on 2011-02-08
I'm not an expert, but this how I solved this for myself:
1) Configured DSAM as described here: [https://help.ubuntu.com/community/Postfix/Dspam](https://help.ubuntu.com/community/Postfix/Dspam)
2) Got same error as you did
3) Figured out that dspam searches /var/spool/dspam/data/local/<user> if no domain specified in user name (--user argument)
4) Hard-coded my domain into /etc/dspam/dspam-retrain script (added $user .= '@example.com'; line before while loop)

It's first time I saw PERL, so there must be better way to modify this retrain script(do it with regex).

---

