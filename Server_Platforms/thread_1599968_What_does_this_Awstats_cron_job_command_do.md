---
title: "What does this Awstats cron job command do ?"
date: 2010-10-18
forum: Server Platforms
---

### Post by mistypotato on 2010-10-18
This line is in my cron jobs but I'm not sure what it does?

[B]
[ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null[/B]

This cron job is set to active and to execute every 10 minutes of every day.

My awstats configurations DO NOT update automatically.  I have to do them manually so this doesn't appear to be an update script?

When I google that command I get only a few results mainly from foreign countries so that makes me a bit suspicious even though I can't see how it would compromise anything.

---

### Post by James78 on 2010-10-18
What do you mean your configurations do not update?

That cron is simply saying, update Awstats using this Awstats configuration (-f /etc/awstats/awstats.conf) and this Apache access log (-r /var/log/apache/access.log).

If you invoke Awstats (/usr/lib/cgi-bin/awstats.pl) from a shell using a --help flag, I'm sure it'll give you a better explanation of what means what.

Also, from how you worded your post, it sounds like you may not know what Awstats is. A simple Google search brings me [here]("http://awstats.sourceforge.net/"). For example, if I go to [http://localhost/awstats](http://localhost/awstats), it'll give me a report of who accessed my server, their browser, user agent, IP, country location, stuff like that. So it just gives you statistics from the Apache access log.

---

### Post by mistypotato on 2010-10-19
Thanks James,

Yes, I've been using Awstats extensively for many years, but I'm not sure what that cron job command did.

thx

---

### Post by James78 on 2010-10-19
No problem. :)

---

