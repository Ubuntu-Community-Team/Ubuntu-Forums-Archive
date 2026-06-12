---
title: "&quot;server1&quot; redirects to IP address"
date: 2008-04-29
forum: Server Platforms
---

### Post by jfm30204 on 2008-04-29
I have 8.04 server installed and a website at server1/site (or server1/ave411/public_html/site).

When I put "server1/site" or "192.168.x.xx/site" in the browser address bar, it redirects to my IP address, or 72.xxx.xxx.xx/site. This way, I'm not really accessing the site over the network, am I? Why does this happen?

Jere

---

### Post by cdenley on 2008-04-29
If you're being redirected, then either a redirect is being added to your http header by an apache module (mod_rewrite) or web script (php,perl), or the page you are accessing uses javascript (window.location) or a meta refresh to redirect you.

Post this output
```

wget http://server1/site -O - |grep http://

```

---

### Post by jfm30204 on 2008-04-29
Here's the important part. Everything after that is just the html from the fetched page:

wget [http://server1/xgal](http://server1/xgal) -O - |grep http:// 

--17:16:13--  [http://server1/xgal](http://server1/xgal)
           => `-'
Resolving server1... 127.0.1.1
Connecting to server1|127.0.1.1|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://server1/xgal/](http://server1/xgal/) [following]
--17:16:13--  [http://server1/xgal/](http://server1/xgal/)
           => `-'
Reusing existing connection to server1:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://72.148.198.53/xgal/modules/extgallery/](http://72.148.198.53/xgal/modules/extgallery/) [following]
--17:16:13--  [http://72.148.198.53/xgal/modules/extgallery/](http://72.148.198.53/xgal/modules/extgallery/)
           => `-'
Connecting to 72.148.198.53:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

---

### Post by jfm30204 on 2008-04-29
I think I know the cause. This is a Xoops site, and in mainfile.php, the Xoops url is 72.148.198.53/xgal. So, Xoops is doing the redirecting. So, thanks. I can take it from here. If I get stuck, I'll post again.

Jere

---

