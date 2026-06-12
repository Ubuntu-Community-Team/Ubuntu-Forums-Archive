---
title: "Trouble installing mail server.  IMAP dropping."
date: 2008-11-16
forum: Server Platforms
---

### Post by Phases on 2008-11-16
Hey guys. First, let me say - I did post a reply with this question on the original HowTo thread I followed:

[http://ubuntuforums.org/showthread.php?t=40047](http://ubuntuforums.org/showthread.php?t=40047)

..but after looking at it, it seems to get little traffic and the OP seems to be the only person providing support there, so I'm just hoping this will be viewed by more people and hopefully someone can help me.

If you feel I'm in the wrong please delete.

Ok. I'm hoping someone pretty familiar with this can help me out. I followed the guide the best I could, and have been working on it for five hours now, but am left with a little trouble.

Wherever the part was toward the beginning (can't seem to find it now) where you test sending an email CLI, I could do. The MAILTO: blah.com part. I emailed my gmail account fine.

However, when trying to login squirrelmail I get (got: now getting told wrong user and pass) the "Connection dropped by IMAP" message, and also when trying the test to connect to IMAP with the CLI test (can't find where I found that, now), I get some sort of 'error, terminating'.

I will try to find the references to these ^^ and will edit them into this post when I find them. I'm sorry I'm just so scatterbrained right now, been at this long time.

I can't figure out how to run /usr/share/squirrelmail/src/configtest.php ...even as root I get permission denied. I tried to open it with FF and that didn't work, tried to make +x, that didn't work.

My syslog, when I try to connect either way, says 1 of 2 things:

If i try to log in with [email]phases@superstickphase.com[/email] I get told supplied password doesn't match encrypted password. I've tried combos galore to get them to match.

If I try to log in with just my username, phases, I get told zero rows returned, no password to compare.


I've been all over this, and google, for almost six hours now.. Hope someone can help. Thanks.

---

### Post by Phases on 2008-11-17
Anyone?

---

