---
title: "proxy_pass to IIS doesn't work as expected"
date: 2012-04-25
forum: Server Platforms
---

### Post by prodigy_ on 2012-04-25
Not a really Ubuntu related question here though nginx is on Ubuntu sever in this case.

Anyway. A portion of nginx.conf:
```

        server {
                listen          80;
                server_name     site2.example.com;

                access_log      /var/log/nginx/access.log;

                location / {
                        proxy_pass              http://site1.example.com;
                        proxy_set_header        X-Real-IP $remote_addr;
                        proxy_set_header        X-Forwarded-For $proxy_add_x_forwarded_for;
                        proxy_set_header        Host $host;
                        proxy_redirect          off;
                }
        }

```

Unfortunately, when I try to access site2.example.com, nginx doesn't proxy to site1. Instead **it proxies to the IP address** site1.example.com resolves to. Or at least so it seems. Since site1 is a virtual host, this doesn't work. I get IIS welcome screen instead of my site content.

Any solution?

---

### Post by elico on 2012-04-25
you should understand that if you pass a request to site1.example.com that what it will do..
you should replace it with a $host$uri arguments and add a resovler option that will do the trick for you.
another thing is to set also the host header to match the site2.example.com but i wouldnt recommend it.

---

### Post by prodigy_ on 2012-04-26
Thank you for your reply. I'm sorry but my knowledge of nginx is very limited. Could you please post a more detailed example or a link to a howto?

I wouldn't ask but I've spent quite some time searching for a solution. Tried some things but nothing worked.

---

