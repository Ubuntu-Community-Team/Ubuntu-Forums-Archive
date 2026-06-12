---
title: "Amavisd-new on Dapper"
date: 2006-06-13
forum: Server Platforms
---

### Post by ScatterBrain on 2006-06-13
A lot has changed with the configuration files between Breezy and Dapper when it comes to Amavisd-new.  ;-)

If I understand the documentation and comments correctly, then all the directives I place in /etc/amavis/conf.d/50-user will **override any of the other settings placed the remaining files**.

Is this correct?

I'm basically following this guide:  [http://www200.pair.com/mecham/spam/spamfilter20050626.html]("http://www200.pair.com/mecham/spam/spamfilter20050626.html") (the one I've used for years) and if the above statement is true then I can basically place all of the needed amavisd-new configuration statements in 50-user and move forward.  I've not had a chance to test this and would like a confirmation before I move forward.

---

