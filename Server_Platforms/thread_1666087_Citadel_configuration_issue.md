---
title: "Citadel configuration issue"
date: 2011-01-13
forum: Server Platforms
---

### Post by johnsjs on 2011-01-13
Not sure if this is the right spot, but since there appears to be a few Citadel experts who post around here I figure it's worth a go.

I have installed Citadel mail and groupware server on Ubuntu 10.10 server at work as an experimental replacement for our failing windows turnkey email server.

The main requirements are ease of maintenance (which Citadel seems to provide), and ability to deal with large mailstores (currently testing, but no issues so far - we don't have many email addresses but some of them have 40k old messages in 10 GB of mail folders.

I've used imapsync to move the messages which worked surprisingly painlessly (albeit the old mailserver refused to share any status flags, so 40k of unread messages - bah!)

In fact this has been the least painful migration of all time - first time I've used Ubuntu for 'real work', and will do again.

However I have one problem - when using thunderbird as the email client it refuses to send email using a display name of anything other than the account name.  The webmail client behaves as instructed, and uses the correct display name (the senders given name) but thunderbird merrily sends emails wherever instructed (external addresses) with the account user name as the send name.

I believe this to be a Citadel configuration issue, as Thunderbird only knows about the account name from the log in details, nowhere else is it recorded - and I've never known Thunderbird do anything like this before with other servers.

If I can't fix this I'm going to have to give postfix/dovecot/etc a go - which will be interesting, but take rather more time than I was planning, as it will be a learn from scratch exercise.

Thanks in advance.

John

---

