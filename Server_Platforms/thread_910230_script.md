---
title: "script"
date: 2008-09-04
forum: Server Platforms
---

### Post by root_at_home on 2008-09-04
Hi there

I was wondering if someone can help me.

I want to check a few thing on my linux server everyday. 
1. failed logins
2. disk space
3. last logins
4. services running
5. files change in last 24 hours.

I know how to check all of this, but would like it if I can write some kind of script that can do all this and mail me the results.

At the moment I have a small simple script that sends me the failed logins.

#!/bin/bash

cat /var/log/auth.log |grep FAILED | mail -s "Daily Failed logins from Server" [email]mail@mail.com[/email]

I am not sure how to add more commands to this one, and/or if there is a better way of doing this.

Regards
Root_at_home

---

### Post by zazuzimbo on 2008-09-04
Show me how you check all that information?!

I think I can put it all together in one simple thing. :)

---

### Post by Dr Small on 2008-09-04
You list the other commands, and I'll come up with a solution script.

---

### Post by heebus on 2008-09-04
Install logwatch.  It does a majority of that :)

---

### Post by root_at_home on 2009-04-02
Hey all.

Just want to say thanks for the reply for all of you.

Root at home

---

