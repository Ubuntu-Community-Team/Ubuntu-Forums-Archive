---
title: "Postfix Cyrus - picture attachment size limit?"
date: 2008-04-07
forum: Server Platforms
---

### Post by dannyboy1121 on 2008-04-07
Hi there .... running Postfix with Cyrus on 7.04 (recently switched from a mail server on a different distro).

It appears that incoming mail attachments become corrupted (although I can send them outbound without issue). For instance, if someone sends a picture through ... I'm only getting a small part of it.

It's like there is an inbound size limit on attachments - chopping then at about 2k !!!

Any ideas?

---

### Post by MJN on 2008-04-08
There is a default message size limit, but it's around 10MB. However, this is not the problem as it would cause a message failure/reject and would be logged.

Do the logs mention anything about communication problems? What happens if you change the format of the attachment (e.g. zip it without compression) in order to keep the same size but alter the binary format?

It sounds to me like a problem outside Postfix, perhaps with your mail client (or the sender's).

Mathew

---

### Post by dannyboy1121 on 2008-04-08
I've been using Thunderbird as a client .. I can send mail out to the Intenet via Postfix and collect it back via a pop account on the same client (but being delivered by my ISPs mail server) and the attachments are not corrupted.

The issue purely seems to be on inbound traffic handled by Postfix / Cyrus.

I tried zipping a test file to see if it had any impact but it appears that it gets corrupted along the way (if I copy the same message in to my ISP account it delivers with no issue).

The file always seems to get cropped to 2k - regardless of the starting size.

I've tailed the mail.log but no major errors logged - other than  WARNING: sieve script /var/spool/sieve/d/username/defaultbc doesn't exist: No such file or directory

I'm not sure that would have any bearing on the problem that I'm experiencing though.

Perhaps I can turn up the volume on the debugging?

---

### Post by MJN on 2008-04-08
> **dannyboy1121 said:**
> The file always seems to get cropped to 2k - regardless of the starting size.

A pattern is a good sign... of what I don't know.. ;)

> Perhaps I can turn up the volume on the debugging?

Yes, try adding -v to the smtpd command at the end of the smtp line in /etc/postfix/master.cf (this will at least increase Postfix's verbosity, I don't use Cyrus so cannot comment on that)

Mathew

---

### Post by dannyboy1121 on 2008-04-08
Well ... a bit more playing and I've found that it appears to be the overall message size that's limited. The more text I put in the mail .. the more it crops the attachment. Eventually .. it starts cropping the message text.

It seems that my messages are limited in total to 4k :D

--- ok so I checked the log and grepped for warnings or errors. I found the following:

 postfix/smtpd[6218]: dict_eval: const  error

This was repeated a few times in the log since debug was turned up. It's a bit cryptic to me.

Any ideas?

---

### Post by dannyboy1121 on 2008-04-08
.. these are my size settings from main.conf ... all looks good here:

/etc/postfix# postconf -d | grep size
berkeley_db_create_buffer_size = 16777216
berkeley_db_read_buffer_size = 131072
body_checks_size_limit = 51200
bounce_size_limit = 50000
header_size_limit = 102400
mailbox_size_limit = 51200000
message_size_limit = 10240000

](*,)

---

### Post by dannyboy1121 on 2008-04-08
Sorry .. just one last post before I crash out for the day.

I've gone through my storage directly in to the mail queue to inspect the mail for the users. It's all there in full ...it must be being chopped in the transport process between server and client.

I've tried a couple of different clients now .. same result for each one.

---

### Post by MJN on 2008-04-09
It's a Cyrus issue then, which I'm afraid I have no experience of. Try increasing its logging verbosity.

Mathew

---

### Post by dannyboy1121 on 2008-04-10
You were right .. it was a Cyrus issue ..and I managed to fix it by doing the following ....

cd /usr/lib/cyrus/bin
su cyrus
./reconstruct -r -f user.username

ctrl+d to break out of su

I went back and found all my mail was displaying full content .. phew.

---

### Post by MJN on 2008-04-10
Nice one. Well done for reporting back as it may well help someone in the same boat.

Mathew

---

