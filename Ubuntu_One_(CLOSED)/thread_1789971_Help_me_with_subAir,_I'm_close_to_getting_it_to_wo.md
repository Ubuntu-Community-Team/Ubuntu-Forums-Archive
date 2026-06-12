---
title: "Help me with subAir, I'm close to getting it to work."
date: 2011-06-24
forum: Ubuntu One (CLOSED)
---

### Post by acqant on 2011-06-24
It's a long long story how I got to this point but I'll save that for later.

Ubuntu says subAir does not work due to lack of SSL support.  That's only one reason why it doesn't work.  I've gotten past that and a few more issues.

Here is what I've done:

[LIST]
[*]Used stunnel to get around the SSL issue.
[LIST]
[*]stunnel -c -f -d 127.0.0.1:8080 -r streaming.one.ubuntu.com:443
[/LIST]
 
[*]subAir still will not work and return a 403 because it wants to do a GET /
[LIST]
[*]I got around that two ways.  One was a reverse squid proxy and another was an Apache proxy.
[/LIST]
 
[/LIST]
Ok, now we're cooking.  Except now subAir is sending POST data to the subsonic server and ubuntu's version does not seem to like that.  Try it yourself

curl -d "c=myapp" [https://streaming.one.ubuntu.com/rest/getIndexes.view](https://streaming.one.ubuntu.com/rest/getIndexes.view) -v
curl  [https://streaming.one.ubuntu.com/rest/getIndexes.view?c=myapp](https://streaming.one.ubuntu.com/rest/getIndexes.view?c=myapp) -v

sigh.... so here I am thinking about writing a POST to GET 'thing' or maybe we can get some more info on how ubuntu's subsonic api works.

---

### Post by acqant on 2011-06-24
So got SubAir working with UbuntuOne streaming.


[LIST]
[*]Apache on local machine
[*]Apache mod_rewrite to get subAir to python.
[*]Python script(s) to intercept POST and convert them to GET
[*]Python script(s) to proxy GET to [https://streaming](https://streaming)
[/LIST]

---

### Post by duanedesign on 2011-06-29
Thanks for updating your thread. Glad you got it working.

---

