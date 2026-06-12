---
title: "exim delivery to cyrus"
date: 2009-11-12
forum: Server Platforms
---

### Post by pbrille on 2009-11-12
I'm desperate, sorry for that easy question maybe.
I set up cyrus and exim with this:

[https://help.ubuntu.com/community/Exim4](https://help.ubuntu.com/community/Exim4)
[http://wiki.ubuntuusers.de/Cyrus_IMAPD](http://wiki.ubuntuusers.de/Cyrus_IMAPD)

Incoming email is delivered to /var/spool/mail. I'd like to have it delivered directly into the cyrus-mailboxes I created. What can I do?

I guess it has to do with this option in update-exim4.conf.conf:
dc_localdelivery='mail_spool'

THX A LOT

---

