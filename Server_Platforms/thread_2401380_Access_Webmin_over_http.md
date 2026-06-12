---
title: "Access Webmin over http?"
date: 2018-09-17
forum: Server Platforms
---

### Post by warmango on 2018-09-17
So what im trying to do is access webmin from example.com/admin, but i am unaware on how to do it, i need to do it specifically over HTTP, as i am using dynu.com to host my website and i hate opening direct ports to my server. 
i know it involves the <Location *> config in apache, but i dont know how...

and ideas?

---

### Post by TheFu on 2018-09-17
>  and ideas? 
This is a terrible, terrible, terrible idea. 

You should only allow localhost connections to something like webmin/phpadmin or any other admin web tool.  Use an ssh tunnel to get that access. [http://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html](http://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html) has some other ssh ideas.

---

### Post by warmango on 2018-09-24
Because i need to be able to remotely access my server easily, and an ssh tunnel is unreliable because work may block SSH tunnels, and have having to use the commandline on my phone,

If your gonna be negative like this when im asking for help, please dont, and ive tried ssh tunnels, Webmin tends to NOT load 

I have moved to cloudflare so i wont be too worried about security, So a little help?
```


<VirtualHost *:443>
    ProxyPreserveHost off
    ProxyPass        "/" "https://127.0.0.1:10000/"
    ProxyPassReverse "/" "https://127.0.0.1:10000/"
    ServerName admin.merith.tk
</VirtualHost>
```

---

