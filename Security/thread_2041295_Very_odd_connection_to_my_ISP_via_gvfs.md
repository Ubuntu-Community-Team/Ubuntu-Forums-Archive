---
title: "Very odd connection to my ISP via gvfs"
date: 2012-08-12
forum: Security
---

### Post by sanukcm on 2012-08-12
So I was poking around with netstat and ran:

```
$ netstat -natup
``` 

One particular connection was very odd: 


```
tcp        0      0 <myIP>:39456      <ip-associated-with-ISP>:80          ESTABLISHED 6546/gvfsd-http 
```


Anyone know why there would be an open connection to my ISP via gvfsd-http over some random local port?

According to [this article]("http://en.wikipedia.org/wiki/GVFS"), gvfs is a way to establish remote connections and browse file systems / access data remotely as if they are your own. Am I being paranoid here? Is there some benign, legitimate reason for this connection to exist? Is it just some normal connection that is going through my ISP because, well... they are my ISP and that's where connections go... or something else? 

If it isn't painfully obvious by now - I am completely ignorant about networking and security. Just trying to figure it out as I go and educate myself. Thanks! :)

---

### Post by Ms. Daisy on 2012-08-14
You haven't gotten a response so I'll give you another thread of the same subject matter:

[http://ubuntuforums.org/showthread.php?t=1757666](http://ubuntuforums.org/showthread.php?t=1757666)

This may help tell you more about what calls it:

[http://askubuntu.com/questions/31468/who-is-calling-gvfsd-and-when](http://askubuntu.com/questions/31468/who-is-calling-gvfsd-and-when)

---

