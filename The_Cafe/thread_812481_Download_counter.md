---
title: "Download counter"
date: 2008-05-29
forum: The Cafe
---

### Post by linux phreak on 2008-05-29
While browsing,i stumbled upon the website of the Maxthon web browser [www.maxthon.com](www.maxthon.com) .I saw a counter reading number of downloads.Is it in real time?.I am amazed at the rate of downloads because the browser itself is not much popular.

---

### Post by tamoneya on 2008-05-29
i think that is an approximation.  They know that they get a certain amount per day and they interpolate that to downloads per second.  Notice how it always goes up by twos and then every once and a while it goes up by three.  It is way to regular be actual real time downloads.

---

### Post by linux phreak on 2008-05-29
I remember seeing  that kind of counter in the vlc media player website too.

---

### Post by schiznik on 2008-05-30
whilst I cant code to save my life, it shouldnt be too difficult to write/create one that is realtime. 

It would need to monitor the web server logs for the specific requests for the download files and update a counter, then display this on a dynamic web page

---

### Post by tamoneya on 2008-05-30
its might not be TOO hard but it probably wont be worth it.  That will be a significant increase in server load if you are continuously checking the logs and there will need to be frequent communication with the server.  Currently it is all contained within one script and the browser just increments at a fixed rate.  If you want real time you would have to be hitting the server at least once per second.

---

### Post by SupaSonic on 2008-05-30
[http://www.maxthon.com/api/counter](http://www.maxthon.com/api/counter) - it makes tons of requests here. They are actually AJAX based so for all i know they are true. Most of the similar stuff I've encountered were fake javascript counters counting from some hard-coded number.

It isn't a good idea though. Unnecessary load.

---

### Post by Joeb454 on 2008-05-30
I don't know whether this would be on or off topic, but has anybody tried the browser?

---

