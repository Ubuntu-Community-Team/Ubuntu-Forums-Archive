---
title: "postfix sender IP problem"
date: 2009-05-12
forum: Server Platforms
---

### Post by trileru808 on 2009-05-12
Hello. I run a perfect server 8.10. This is installed at IP 89.xxx.xxx.yyy. Some the users that have mail accounts are sending emails from 89.xxx.xxx.zzz . One of the computers at this ip is sending spam, not thru my server thou, but it's still sending spam. So that IP got blacklisted. Now...whenever someone at this IP sends email thru my server, I get an error in the logs that that email couldn't reach it's destination because it was sent from a blocked IP. How can I configure postfix so that any user that sends email from 89.xxx.xxx.zzz to show that he actually sent it from 89.xxx.xxx.yyy where the mail server is?

Also...can a virus from windows xp send spam, but not thru my mail server, thus having my IP blacklisted?

---

### Post by a9k3d on 2009-05-14
> Also...can a virus from windows xp send spam, but not thru my mail server, thus having my IP blacklisted?

YES! Windows PC zombies have their own SMTP send routines built-in. They usually have IRC and several other sneaky network features.

Get that PC cleaned up. Then you can go to the (good) blacklists IF you own the ip's and tell them you fixed the problem, and flogged the user.

Meanwhile they could send email via squirrelmail if you have it.

If they submit their email though your IP - they shouldn't see it refused unless the receiver if looking at all the headers (which are often fake in spam) and blocking based on IP's seen in there.

In my ten years of running ISP's, I've never tried to rewrite any headers that postfix inserts. It seems like the wrong answer to the problem.

Could you post the exact error log line? Is it a 500 error from a remote server or are you blocking .zzz with some local restriction?

Finally if this is a home network, you're better off sending through your ISP. Let them deal with the blacklists.

---

