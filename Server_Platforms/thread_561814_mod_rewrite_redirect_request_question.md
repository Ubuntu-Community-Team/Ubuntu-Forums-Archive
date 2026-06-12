---
title: "mod_rewrite redirect request question"
date: 2007-09-28
forum: Server Platforms
---

### Post by papayiya on 2007-09-28
The following allows me to use mod_rewrite to redirect a given request from [www.whatever.com](www.whatever.com) to another server on my network:

```

<VirtualHost *:80>
        ServerName www.whatever.com
        RewriteEngine     On
        RewriteRule       ^(.*)$        http://192.168.1.40$1  [P]
</VirtualHost>

```

Is here anyway to attach in the rewrite URL the fact that this request is for whatever.com? Cause the way it is now, the second server will not know that this request is for whatever.com.

Thanks,
George

---

