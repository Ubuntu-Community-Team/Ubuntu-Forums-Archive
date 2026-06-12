---
title: "Help with postfix authentication configuration"
date: 2009-06-23
forum: Server Platforms
---

### Post by -=pug=- on 2009-06-23
I'm trying to setup limited authentication for postfix on a small server I run. In a nutshell here's what I want to be able to do...

1) Force all users on the system to have to authenticate when using postfix for sending mail from localhost. The only mail that's going to be sent to the outside world is going to originate from localhost via roundcube, so there is no need to allow relaying of any kind from the outside world.

2) Use system passwords for authentication, and I really don't want to go to the hassle of having having to install and configure Cyrus to achieve this. I've searched and searched on this and every solution I've found relies on Cyrus which for me is just one step too far in the complexity of what I want to achieve. Ideally I'd like to use system passwords in the same way that the likes of dovecot does, nice and simple but effective.

3) Allow system mails from localhost to localhost (cron, logwatch etc) be sent normally if possible without having to authenticate.


The history to this is that a couple of weeks ago my server was used as a relay from what I can gather due to a vulnerability in squirrelmail. So spammer broke squirrelmail and then used it to relay spam. postfix saw mail coming from localhost so happily forwarded it to the Internet as it's configured to.

My thinking is if I can authenticate all mail that's to be relayed to the outside world from localhost, but keep all localhost to localhost mail as is I'll be able to prevent a webmail vulnerability from allowing my server being used as an open relay while at the same time allow the server to let me know what it's doing when it needs to.

---

