---
title: "Up/Down speeds very slow all of a sudden"
date: 2015-04-14
forum: Server Platforms
---

### Post by CHaines on 2015-04-14
So I have a LAMP server running a site. It has been fine, but today when i went to view my site, it was extremely slow (it's an offline server at the moment, so i should be the only person accessing it)

>speedtest-cli results in: 
```
Testing download speed........................................
Download: 21.26 Mbit/s
Testing upload speed..................................................
Upload: 3.35 Mbit/s



```

Plugging in my laptop to the same router/firewall as the server and going to testmy.net results in:
55 down, 25 up.

htop or top shows that the server is hardly working at all.

A reboot or two didn't solve the issue.

I haven't changed anything recently, unless it was some auto-update...

Can someone please help me figure out why it is so slow all of a sudden?
Thanks!

(let me know what info you need)

---

### Post by ajgreeny on 2015-04-14
This may or may not be of consequence, but for some unknown reason I have always found **speedtest.cli** run in terminasl gives much slower upload results than speedtest.net run in my web browser.  Here's the results run now:-

speedtest.cli:-
Testing download speed........................................
Download: 34.13 Mbit/s
Testing upload speed..................................................
Upload: 1.57 Mbit/s

speedtest.net
Testing download speed........................................
Download: 37.02 Mbit/s
Testing upload speed..................................................
Upload: 9.06 Mbit/s

---

### Post by CHaines on 2015-04-15
Thanks for the info, but my webpages are still loading horribly slow, so something is going on. 

I just downloaded speedtest to try and get an idea, never used it before.

---

