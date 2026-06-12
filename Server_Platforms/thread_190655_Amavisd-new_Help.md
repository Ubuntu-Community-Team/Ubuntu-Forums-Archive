---
title: "Amavisd-new Help"
date: 2006-06-06
forum: Server Platforms
---

### Post by twren71 on 2006-06-06
I have been following [this tutorial"]this tutorial]("http://www200.pair.com/mecham/spam/spamfilter20050628.html#razorconfig") to set up a linux email filter for my exchange environment. Unfortunately these are written for Debian unstable and I followed the instructions too closely and borked my amavisd installation. If anyone can post the text of the file /etc/cron.daily/amavisd-new for Dapper it would be much appreciated.

---

### Post by cyracks on 2006-06-06
#!/bin/sh
#
#  Daily maintenance for amavisd-new
#  $Id: amavisd-new.cron.daily,v 1.6 2005/12/28 00:08:52 hmh Exp $
#
# Needed only if spamassassin is in use
umask 022
test -e /usr/bin/sa-learn && test -e /usr/sbin/amavisd-new && {
        su - amavis -- /usr/bin/sa-learn --sync --force-expire >/dev/null
}
exit 0

---

