---
title: "My web page in another website"
date: 2013-09-24
forum: Security
---

### Post by alfirdaous on 2013-09-24
Good morning everybody

I would like to check this thing:

```
[Tue Sep 24 13:47:09 2013] [error] [client VISITOR_IP] File does not exist: /home/MY_HOMER_USER/www/forum, referer: http://VISITOR_WEB/forum/index.php
```

I was checking my logs and found that, when I access the visitor website, I found my web page with my own links, what is that exactly?

Thanks in advance

---

### Post by TheFu on 2013-09-24
Are you running a forum? 
Is it php?
Has it been hacked?
Could the settings be wrong?
Could someone outside just be fishing?

I block all external php requests. ALL OF THEM - for security reasons.

---

### Post by alfirdaous on 2013-09-24
> **TheFu said:**
> Are you running a forum? 

No

> 
Is it php?

Yes

> 
Has it been hacked?

No

> 
Could the settings be wrong?

??

> 
Could someone outside just be fishing?

How to block phishing?

> 
I block all external php requests. ALL OF THEM - for security reasons.


How to blcok external php requests?

Thanks

---

### Post by TheFu on 2013-09-25
With nginx, it is easy to refuse php.
```
if ($request_uri ~* (\.php$) ) { return 403; }
```

nginx also lets us specify allowed URLs, so that prevents bogus requests from getting to the app-servers at all. They are blocked by the reverse proxy.  If you aren't running forums, then that location doesn't exist and external people shouldn't be able to hit the web server at all.  

Lots of cookbook recipes for nginx exist. [Block exploits, sql-injections, spam, user-agents, selected remote IPs.]("http://www.howtoforge.com/nginx-how-to-block-exploits-sql-injections-file-injections-spam-user-agents-etc")

Apache probably has a way to do this too, I stopped using it years ago - too many features, too hard to secure, IMHO. I'm lucky. We have more control over which things we run or refuse to run. If you are stuck on Apache (not necessarily a bad thing), google is your friend for these type of settings. Isn't there a mod_security thing for apache?

---

### Post by alfirdaous on 2013-09-25
Thx [**[COLOR=#000000]TheFu[/COLOR]**]("http://ubuntuforums.org/member.php?u=1037685"), I am using apache

---

