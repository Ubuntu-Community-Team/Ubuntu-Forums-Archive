---
title: "Updating server 6.10 -&gt; 7.04"
date: 2008-05-17
forum: Server Platforms
---

### Post by Lupe0 on 2008-05-17
I've been very happy to run Ubuntu 6.10 (Edgy) for a long time, but now it's time to update first to 7.04 (Feisty Fawn) and later to newer one with LTS. I have a server version and my question is; how easily I can break my server with updating to newer version?

I found pretty good docs to do the update ( [https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades) ), but because I'm running 11k user website, there shouldn't be too long cuts to this service.

All suggestions are welcome. Thanks in advance. :)

---

### Post by Thirtysixway on 2008-05-18
Unless you have a backup server you can switch to, there will be downtime during the upgrade(s).  If you can't switch to a temporary server while you upgrade, I would do it really late at night when there are not a lot of users accessing the server.

Remember that you need to go 6.10 => 7.04 => 7.10 => 8.04 in your situation.

As far as risk of losing data, you should definitely backup your data.  I'm not saying it will go bad, but it's always better to play it safe.

---

