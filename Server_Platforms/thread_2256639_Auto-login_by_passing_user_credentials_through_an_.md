---
title: "Auto-login by passing user credentials through an Apache Redirect?"
date: 2014-12-13
forum: Server Platforms
---

### Post by regnumimbriumx on 2014-12-13
Hey friends,

I'm using the popular rss aggregator CommaFeed on my server. I want to use it to display aggregated news in a publicly-available format, but the software requires you to log in to see news feeds. Although I could make a landing page which informs users that they may log in with user "free" and password "free", I would prefer to figure out a way to log them in automatically. Would it be possible to achieve this through an Apache Redirect, which somehow passes on the user credentials? If so, can someone advise me how to figure out the url that I would need to program into the redirect?

THANKS! :KS

---

### Post by koenn on 2014-12-19
This would actually depend on the CommaFeed program itself  - I don't know nothing about that

First, you might want to see if CommaFeed itself provides unauthenticated access (some sort of gues access ?)

If you want a proxy to handle it, you need to know in what form or by what method the authentication is send to the program.
It's not impossible to let a proxy server add "user=free&password=free" to a URL, but that's not gonna halp any if this isn't how CommaFeed or whatever other program expects to receive authentication.

---

