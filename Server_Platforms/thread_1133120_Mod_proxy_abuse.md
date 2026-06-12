---
title: "Mod proxy abuse?"
date: 2009-04-22
forum: Server Platforms
---

### Post by CP1256 on 2009-04-22
A few days ago I enabled mod_proxy on Apache 2.2.9 and turned ProxyRequests on. Soon after someone started to use my server as a proxy, so I set ProxyRequests to off and unloaded mod_proxy and anything related to it. 

Now I'm seeing some guy connect to IRC. First he uses "CONNECT 1.2.3.4:6667" where 1.2.3.4 is the other server's IP, and my server returns a 405 error.
Then he sends "POST 1.2.3.4:6667" and my server return a 200 message. He uses HTTP/1.0. 

I even unloaded mod_proxy and restarted Apache, is it still possible someone is using my server as a proxy? I'm using Debian Lenny, btw.

---

### Post by cdenley on 2009-04-22
If mod_proxy is not being used, then the hostname given is ignored, and apache handles the request's URI. For example, these two commands yield the exact same results, assuming you haven't configured mod_proxy.
```

echo -e "GET / HTTP/1.0\n"|nc mydomain.com 80
echo -e "GET http://google.com/ HTTP/1.0\n"|nc mydomain.com 80

```
The second command may look like a successful proxy request in the logs, but "http://google.com" was ignored, and apache served "/" from your own server.

---

### Post by CP1256 on 2009-04-23
Thanks for your reply. I understand now.

---

