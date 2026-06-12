---
title: "Intermittent 403 Forbidden from Apache/suphp"
date: 2013-06-14
forum: Server Platforms
---

### Post by isecore on 2013-06-14
So, I've noticed a strange occurence on my server. Occasionally the client will get a "Forbidden: You don't have permission to access / on this server." error from the server. Recently I installed suphp and switched from prefork to worker MPM. So far so good, except for this strange behavior.

It's fairly easy to reproduce: Simply reload the website 5-6 times. Then you'll start getting the error message, and then just let it be for about 15 seconds and then you can reload the site just fine. Hammer it with 5-6 reloads and again you'll get the Forbidden error. You can try it yourself with [my photoblog]("http://blog.isecore.net/"). Just force-reload it a few times and boom. Then back off about 15 seconds or so and you're good to go again.

I've tried to figure out why this happens but I am now at my wits end. The only useful thing I've managed to google is [this page]("http://serverfault.com/questions/509533/apache-server-gives-403-forbidden-error-after-a-couple-of-request") which suggests it's a timeout issue which might seem appropriate. Not sure how to fix that though. Other than that, nothing have helped me much.

When poking through the logs, the error that gets logged is [error] [client IP-ADRESS OF CLIENT] client denied by server configuration: /home/username/sitename/etc/etc/etc

I'm running Ubuntu 12.04, 64-bit. All patched up. Apache 2.22. MPM is Worker and I've installed suphp.

--- SOLVED: It was mod_evasive that triggered this behavior. I discovered I had somehow somewhen installed it and that's the problem. Sorry for the inconvenience, I hope other people who have this problem finds this thread.

---

### Post by sandyd on 2013-06-15
> **isecore said:**
> So, I've noticed a strange occurence on my server. Occasionally the client will get a "Forbidden: You don't have permission to access / on this server." error from the server. Recently I installed suphp and switched from prefork to worker MPM. So far so good, except for this strange behavior.

It's fairly easy to reproduce: Simply reload the website 5-6 times. Then you'll start getting the error message, and then just let it be for about 15 seconds and then you can reload the site just fine. Hammer it with 5-6 reloads and again you'll get the Forbidden error. You can try it yourself with [my photoblog]("http://blog.isecore.net/"). Just force-reload it a few times and boom. Then back off about 15 seconds or so and you're good to go again.

I've tried to figure out why this happens but I am now at my wits end. The only useful thing I've managed to google is [this page]("http://serverfault.com/questions/509533/apache-server-gives-403-forbidden-error-after-a-couple-of-request") which suggests it's a timeout issue which might seem appropriate. Not sure how to fix that though. Other than that, nothing have helped me much.

When poking through the logs, the error that gets logged is [error] [client IP-ADRESS OF CLIENT] client denied by server configuration: /home/username/sitename/etc/etc/etc

I'm running Ubuntu 12.04, 64-bit. All patched up. Apache 2.22. MPM is Worker and I've installed suphp.

--- SOLVED: It was mod_evasive that triggered this behavior. I discovered I had somehow somewhen installed it and that's the problem. Sorry for the inconvenience, I hope other people who have this problem finds this thread.
mod_evasive is to block floods
Turn the settings up a bit, so that you can set how many times the site can be loaded per second at per ip :D

---

### Post by isecore on 2013-06-16
> **sandyd said:**
> mod_evasive is to block floods
Turn the settings up a bit, so that you can set how many times the site can be loaded per second at per ip :D

Yeah, I know what it's for :)

I was just too dimwitted to realize I had installed it. Currently I have no use for flood-protection but apparently at some point in the last year and a half I got paranoid and installed it.

---

