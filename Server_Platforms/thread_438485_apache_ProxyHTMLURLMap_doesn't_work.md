---
title: "apache: ProxyHTMLURLMap doesn't work"
date: 2007-05-09
forum: Server Platforms
---

### Post by eantoranz on 2007-05-09
I'm working on a fairly simple example to test ProxyHTMLURLMap (from mod_proxy_html), but I don't get to make it work. I just can'¡t get it to change the content of the web page I request.

Look at the configuration.

Inside 000-default, I added:

```

ProxyPass       /external        http://localhost:8080/internal
ProxyHTMLLogVerbose On
LogLevel Debug

        <Proxy *>
                Order deny,allow
                Allow from all
        </Proxy>

        <Location "/external/">
                Order deny,allow
                Allow from all
                ProxyHTMLURLMap /internal       /external
        </Location>

```

I have a service on port 8080 (resin... with a plain html page inside /internal)

Here's the page's content:
```

<html>
<body>
These are some links:<br>
<a href="www.gmail.com">GMail</a><br>
<a href="/internal/test1.html">Mapping from /</a><br>
<a href="http://localhost:8080/internal/test1.html">Mapping from localhost:8080</a><br>
</body>
</html>

```

When I ask apache to serve that page, I get the same unmodified content. :mad: I'm already sick of this.

Shouldn't it change the content of the page?

I have enabled mod_proxy, mod_proxy_http and mod_proxy_html

It's apache2 on feisty.

---

