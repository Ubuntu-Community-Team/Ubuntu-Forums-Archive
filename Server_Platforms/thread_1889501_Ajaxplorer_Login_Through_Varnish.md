---
title: "Ajaxplorer Login Through Varnish"
date: 2011-12-01
forum: Server Platforms
---

### Post by joshruehlig on 2011-12-01
Hey guys!

*I have ajaxplorer successfully running on my ubuntu 11.10 64bit server using nginx and php-fpm. It works great but I can't seem to login when I use varnish. I have ajaxplorer on my subdomain "sub.domain.com" and wordpress on my main domain "domain.com".

**Whenever I try and login through varnish it just seems to refresh the page and never logs me in...**

Here is my varnish vcl, customized for wordpress

```
backend default {
    .host = "127.0.0.1";
    .port = "8080";
}
acl purge {
        "localhost";
}

sub vcl_recv {
        if (req.request == "PURGE") {
                if (!client.ip ~ purge) {
                        error 405 "Not allowed.";
                }
                return(lookup);
        }
        if (req.url ~ "^/$") {
               unset req.http.cookie;
        }
}
sub vcl_hit {
        if (req.request == "PURGE") {
                set obj.ttl = 0s;
                error 200 "Purged.";
        }
}
sub vcl_miss {
        if (req.request == "PURGE") {
                error 404 "Not in cache.";
        }
        if (!(req.url ~ "wp-(login|admin)")) {
                unset req.http.cookie;
        }
        if (req.url ~ "^/[^?]+.(jpeg|jpg|png|gif|ico|js|css|txt|gz|zip|lzma|bz2|tgz|tbz|html|htm)(\?.|)$") {
                unset req.http.cookie;
                set req.url = regsub(req.url, "\?.$", "");
        }
        if (req.url ~ "^/$") {
                unset req.http.cookie;
        }
}
sub vcl_fetch {
        if (req.url ~ "^/$") {
                unset beresp.http.set-cookie;
        }
        if (!(req.url ~ "wp-(login|admin)")) {
                unset beresp.http.set-cookie;
        }
}
```

I am thinking I should edit it to get it to completely pass ajaxplorer. I tried completely passing the url but it doesn't work.

Thanks!

---

