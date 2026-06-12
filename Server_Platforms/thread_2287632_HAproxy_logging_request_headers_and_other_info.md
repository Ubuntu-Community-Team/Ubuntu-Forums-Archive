---
title: "HAproxy logging request headers and other info"
date: 2015-07-21
forum: Server Platforms
---

### Post by andrew102 on 2015-07-21
Hello,

So I can see this info in the app. The problem we want to solve is having User-Agent and X-Forwarded-For in the haproxy logs.

i.e. This data (or selected header values)
```

[TABLE="class: table table-condensed table-striped"]
[TR]
[TH]connection:[/TH]
[TD]close[/TD]
[/TR]
[TR]
[TH]host:[/TH]
[TD]x.x.x.x[/TD]
[/TR]
[TR]
[TH]accept-language:[/TH]
[TD]en-AU[/TD]
[/TR]
[TR]
[TH]x-forwarded-for:[/TH]
[TD]x.x.x.x[/TD]
[/TR]
[TR]
[TH]x-forwarded-port:[/TH]
[TD]443[/TD]
[/TR]
[TR]
[TH][/TH]
[TD][/TD]
[/TR]
[TR]
[TH]accept:[/TH]
[TD]text/html, */*; q=0.01[/TD]
[/TR]
[TR]
[TH]user-agent:[/TH]
[TD][/TD]
[/TR]
[TR]
[TH]x-forwarded-proto:[/TH]
[TD]https[/TD]
[/TR]
[TR]
[TH]cookie:[/TH]
[TD]X[/TD]
[/TR]
[TR]
[TH]x-varnish:[/TH]
[TD][/TD]
[/TR]
[TR]
[TH]referer:[/TH]
[TD][/TD]
[/TR]
[TR]
[TH]x-requested-with:[/TH]
[TD]XMLHttpRequest[/TD]
[/TR]
[TR]
[TH]accept-encoding:[/TH]
[TD]gzip[/TD]
[/TR]
[TR]
[TH][/TH]
[/TR]
[/TABLE]

```

I tested this in a staging environment and can see host IP and user agent by using the log-format with %hr or %hrl

The problem is that the environment I used to test is not set up to add some of those request headers to the HTTP request. Such as x-varnish, x-forwarded-for, x-forwarded-proto, etc. So I do not know what fields hr would actually display and if all of that information normally appear or not?
To put it another way, does the logger for HAproxy automatically grab custom header values, such as X-Forwarded-For, and put them in the log (if specifying %hr) ?

---

