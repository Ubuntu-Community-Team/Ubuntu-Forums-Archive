---
title: "apache access log entries?"
date: 2011-03-07
forum: Server Platforms
---

### Post by sdowney717 on 2011-03-07
so what is going on here in the log?

```
184.107.157.130 - - [07/Mar/2011:17:53:38 -0500] "GET http://184.107.157.133/~aaproxy/testprox.php?ip=24.254.241.192:8080&type=http&from=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Fp%3D10533194 HTTP/1.1" 404 486 "-" "Googlebot/2.1 (+http://www.googlebot.com/bot.html)"
66.249.71.234 - - [07/Mar/2011:18:43:08 -0500] "GET /robots.txt HTTP/1.1" 404 507 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
66.249.71.234 - - [07/Mar/2011:18:43:08 -0500] "GET / HTTP/1.1" 200 356 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
184.107.157.130 - - [07/Mar/2011:19:38:17 -0500] "GET http://184.107.157.133/~aaproxy/testprox.php?ip=24.254.241.192:8080&type=http&from=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Fp%3D10533194 HTTP/1.1" 404 486 "-" "Googlebot/2.1 (+http://www.googlebot.com/bot.html)"
184.107.157.130 - - [07/Mar/2011:20:46:38 -0500] "GET http://184.107.157.133/~aaproxy/testprox.php?ip=24.254.241.192:8080&type=http&from=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Fp%3D10533194 HTTP/1.1" 404 486 "-" "Googlebot/2.1 (+http://www.googlebot.com/bot.html)"
```

---

### Post by wongo888 on 2011-03-08
Someone might be testing your machine at 24.254.241.192 to see if you are running an open http proxy.

---

