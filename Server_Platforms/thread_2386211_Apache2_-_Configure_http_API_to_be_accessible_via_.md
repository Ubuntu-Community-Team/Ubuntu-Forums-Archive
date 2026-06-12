---
title: "Apache2 - Configure http:// API to be accessible via https:// SSL"
date: 2018-03-02
forum: Server Platforms
---

### Post by dwaynem on 2018-03-02
I need to configure an API that is accessible via [http://127.0.0.1:26968](http://127.0.0.1:26968) from my https:// web site.  I've found the example below for nginx:


[LIST]
[*]Inside your SSL Listener add the following:
[/LIST]
```
location /json_rpc {
    proxy_pass http://127.0.0.1:26968/json_rpc;
}

location ~ ^/api/(.*) {
    proxy_pass http://127.0.0.1:8117/$1$is_args$args;
}
```
How do I accomplish the same thing with apache2 ?

---

