---
title: "Little website help :)"
date: 2008-05-01
forum: The Cafe
---

### Post by qbox on 2008-05-01
Hi to all
I wonder what information can be collected from a user who access to a web page? Only to open a web, not to login things.. only to open.
Can be recovered serial number on CPU or MAC number on a NIC......?
Only with JavaScript and PHP.
I really appreciated if someone can give me an answer on all (2) upper questions.

The problem is that I have a web page and visitors vote on the site one time a day. On the end of the month I chose the winner. I put some restriction like IP and cookie so I can control people to vote only one time a day and after 24 h they can vote again. So that work nice until I recover that some users cheating. They use proxy, change IP, delete cookies and vote for them shelf more then one time....
If anyone have some idea that will be nice. :)

Thank you.

p.s. maybe this is not the right place for this post. I search for some off topic places and I think that is here. :popcorn:

---

### Post by elvinatom on 2008-05-01
I guess that depends on what kind of a page you access and with what browser. I heard that IE hands out all kind of info without any hesitation.

---

### Post by h4mx0r on 2008-05-01
You really should implement a login mechanism to keep track. To prevent/slow bots most sites use some sort of test thing which might work out against some. To prevent proxies some services scan the last hop to see if it had certain open ports (then again you might block most who do use that method for online viewing). You could possibly use browser information reported like version numbers and other stuff but most use more than one browser or update/fake the reporting (user agent switcher plugin). Hmm if its a small vote you could try localizing it. Like lets say the site is "Finland golfers association" or something no one using an isp not located in Finland should be voting right?

---

### Post by mech7 on 2008-05-02
You can save the ip to a database, its pretty much the closest you can get... it still sucks cause of people getting different ip and being behind proxy and all..

---

### Post by WorldTripping on 2008-05-02
> **qbox said:**
> Hi to all
I wonder what information can be collected from a user who access to a web page? Only to open a web, not to login things.. only to open.


As far as I'm aware, only the browser header infomation can be detected, (ip, browser, type, where referred from etc).

[http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html]("http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html")

However, this is easy to spoof:

[http://www.ericgiguere.com/articles/masquerading-your-browser.html]("http://www.ericgiguere.com/articles/masquerading-your-browser.html")

It is also possible to detect the screen resolution with javascript, using the function "window.screen.availWidth".

---

### Post by qbox on 2008-05-02
Thanks for the response.
I cant implement a login mechanism because site must be simple.
People form all over the world access to the site and isn't fair to not allow them to vote if I put some regional restrictions. ISP in the country give different IP address on every reconnect. 
I try to take IP address and put in the database but people reconnect all time or use proxy. If I can read from their computer any unique number will be great. If I store browser header information then will be a problem. Header information is not unique for every machine. Lets say that I use Mozilla and I vote. In the database is a information who say that user who using Mozilla just give a vote and he doesn't have right to vote in next 24h. So another users who use Mozilla can't vote either.
Can be read some how with javascript or php some unique information for the machine? Some unique number od something.
Thanks again :)

---

