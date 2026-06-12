---
title: "Squid web form authentication"
date: 2012-01-16
forum: Server Platforms
---

### Post by narcos on 2012-01-16
Hi all,

I'm trying to get my squid server to redirect users to a PHP login page. I've followed the tutorial @

[http://wiki.squid-cache.org/ConfigExamples/Portal/Splash](http://wiki.squid-cache.org/ConfigExamples/Portal/Splash)

When trying to access an arbitrary page I receive a 302 redirect to my splash page. However, when trying to access the splash page, I again receive a 302 redirect to it (i.e. an infinite loop). Below is the result of such a pair of requests:

```
nc -v my.server.com 3128
Connection to my.server.com 3128 port [tcp/ndl-aas] succeeded!
GET http://www.google.com HTTP/1.0

HTTP/1.0 302 Moved Temporarily
Server: squid/2.7.STABLE7
Date: Mon, 16 Jan 2012 15:52:44 GMT
Content-Type: text/html
Content-Length: 0
Location: http://my.server.com/splash.html
X-Squid-Error: 403 Access Denied
X-Cache: MISS from xxxx.com
X-Cache-Lookup: NONE from xxxx.com:3128
Via: 1.0 xxxx.com:3128 (squid/2.7.STABLE7)
Connection: close
```

```

nc -v my.server.com 3128
Connection to my.server.com 3128 port [tcp/ndl-aas] succeeded!
GET http://my.server.com/splash.html HTTP/1.0

HTTP/1.0 302 Moved Temporarily
Server: squid/2.7.STABLE7
Date: Mon, 16 Jan 2012 15:52:44 GMT
Content-Type: text/html
Content-Length: 0
Location: http://my.server.com/splash.html
X-Squid-Error: 403 Access Denied
X-Cache: MISS from xxxx.com
X-Cache-Lookup: NONE from xxxx.com:3128
Via: 1.0 xxxx.com:3128 (squid/2.7.STABLE7)
Connection: close
```

Any assistance with this would be greatly appreciated!

Also, I'd appreciate any advice on the next step of setting up authentication via a web form.

-n

---

### Post by SeijiSensei on 2012-01-16
Is there some reason you need to take such a convoluted approach when you could just use the [authentication built into Squid already]("http://wiki.squid-cache.org/Features/Authentication")?

---

### Post by narcos on 2012-01-17
> **SeijiSensei said:**
> Is there some reason you need to take such a convoluted approach when you could just use the [authentication built into Squid already]("http://wiki.squid-cache.org/Features/Authentication")?

Thanks for the reply SeijiSensei. I looked into the built in Squid authentication options- but as far as I can tell there are no options for a web form?

I'm building a proxy with a kind of captive portal, and I'd like to give users the option to create an account via a web form.

---

### Post by neelim on 2013-01-06
Hi I am a new to squid, I am planning to develop a web based front end for squid as a project I also like the idea of authenication like captive portal as the pop up authenication looks very odd. Did you succeeded in the external authenication system? I need your help.

Thanks in advance

---

