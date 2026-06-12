---
title: "Mod Rewrite &amp; virtual hosts"
date: 2007-04-16
forum: Server Platforms
---

### Post by iluminate on 2007-04-16
Greetings all,

It's always a lottery to post something here on Servers and Security since many posts gets unanswered =)
Lets hope I get lucky then!

I am using mod_rewrite, and everything works perfect when adding the rules inside the htaccess file.
However, what I want now is to move the rules to the conf files, in this case to virtuall host config file.
Can someone let me know if this is possible or not, since I am experiencing problems when adding the rules to /sites-available/host1conf

Just can not figure it out how to.

Second, I have noticed a huge CPU increase when doing http requests. Sometimes the CPU load jumps to 50-70% - is this caused by mod_rewrite?
Also what is normal cpu load when doing a request if using  smarty, mod_rewrite & php5?
The server is a dual Xeon with 4 GB mem.

Peace to all!

---

### Post by Frosty Cold Drink on 2007-04-16
As far as rewrite in virtual host configs go, you should be OK so long as you are inside the VirtualHost block. Of course, context is different rules written as you would in the directory, so your rules may or may not need a little work. You can also wrap your mod_rewrite directives in a directory or location block inside of the VirtualHost block.

---

### Post by iluminate on 2007-04-19
Thanks for your reply!
It works fine now, but it was a little bit tricky to get it running.
Cut and paste did not do it heh =)

Peace

---

