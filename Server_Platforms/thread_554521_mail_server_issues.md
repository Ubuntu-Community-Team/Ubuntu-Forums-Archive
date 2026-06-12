---
title: "mail server issues"
date: 2007-09-19
forum: Server Platforms
---

### Post by xIke on 2007-09-19
I'm trying to follow the guide at [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) and am having some trouble.  If there's another guide that's more up to date, or better, etc., feel free to link me to that and ignore the following.

When I start up postfix, I get this in the log file:

```
Sep 19 03:07:47 ubuntu postfix/postalias[28728]: fatal: open database aliases.db: Permission denied
Sep 19 03:48:43 ubuntu postfix/master[26376]: terminating on signal 15
```

I'm also having issues with the relayhost (an smtp server with authentication).  I'd probably prefer setting up a local smtp server instead if that's not too ugly of a process.

Thanks for any help!

---

### Post by glee on 2007-09-21
By the look of your error I would start by checking the entries in /etc/postfix/mysql_alias.cf

---

### Post by xIke on 2007-09-21
Nice...that got that problem resolved.

But now it's trying to use my relay host...I thought that was simply for sending email (smtp), not for when it receives them...?

It's not accessing mysql at all during the process...

---

