---
title: "TOR troubles"
date: 2009-04-06
forum: Security
---

### Post by Clang on 2009-04-06
Hi All,

I have been trying for the past 3 hours to get TOR working on my system (8.04).

First I tried TORButton/Privoxy. Privoxy is working ([http://p.p/](http://p.p/) is present and correct) but the TORButton "Test Proxy Setting" reports failure.

I did a search in these forums and found a suggestion to use OperaTor with wine. I have OperaTor up and running but going to [www.whatismyip.com](www.whatismyip.com) still reports my actual IP address.. not the IP address of some TOR node.

I tested TOR by doing the following:

torify wget --user-agent="Mozilla/5.001 (windows; U; NT4.0; en-US; rv:1.0) Gecko/25250101" [http://www.whatismyip.com/](http://www.whatismyip.com/)


The IP reported there is indeed different than my IP. 

So both TOR and Privoxy are working but nothing else seems to be?

Has anyone had this problem before? Ideally I would like to use TORButton with firefox but at this stage I would be happy with any way of browsing (bar wget) that uses TOR nodes.

Thanks

EDIT: Firefox version 3.0.5
Both privoxy and Tor are from the repos.

---

### Post by cdenley on 2009-04-06
Did you configure privoxy to use tor?
/etc/privoxy/config
```

forward-socks4a / 127.0.0.1:9050 .

```
[http://www.torproject.org/docs/tor-doc-unix.html.en](http://www.torproject.org/docs/tor-doc-unix.html.en)

Obviously, it does not use this configuration by default, since privoxy serves a seperate purpose from tor, and neither depend on each other, even though they are commonly used together.

As a side not, are you sure you understand how TOR works, and how it could potentially make you less secure? It seems a lot of people have a misconception that it stops people from intercepting your data, when the opposite is actually true.

---

