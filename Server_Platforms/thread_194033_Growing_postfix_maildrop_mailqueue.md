---
title: "Growing postfix maildrop mailqueue"
date: 2006-06-10
forum: Server Platforms
---

### Post by briguy on 2006-06-10
I'm running a web server using Breezy (I'll upgrade it to Dapper when I get home - I'm away for a few months) and recently installed awstats and munin.  Looking at munin is great - lots of info, however it is showing that I have a growing postfix maildrop mailqueue.  I believe that it is due to some error being put in the mail queue when cron updates awstats.  The problem is that the mailqueue has about 1300 messages in it now!

Honestly, I have no idea how postfix works.  A bit of googling hasn't shed much light on how I can clear this queue up.  Ideas?

I am also running a Hula mailserver as well, and I don't want to break that...

---

