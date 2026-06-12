---
title: "[SOLVED] Google's additions on Apache logs"
date: 2008-07-29
forum: Server Platforms
---

### Post by Folk Theory on 2008-07-29
hi,
i wanted to ask what is the meaning of the long string that google
adds to apache logs when someone hits my webpage through google. i
know it contains information like the search terms but i wanted an
indepth explanation. if you guys could help me or point me to a page
that explains this stuff it'll be much appreciated. 

sorry i dont paste a log showing this but im not with the server now physically and it's down now so i can't connect to it...

---

### Post by cariboo on 2008-07-29
I can't tell you waht the string contains, but apparently it gives the search string that brought people to your page and more. Have a look here:

[http://www.madboa.com/geek/apache-google/](http://www.madboa.com/geek/apache-google/)

there is a script for extracting the information form your logs.

Jim

---

### Post by MJN on 2008-07-29
It is the HTTP Referer as passed by the client to your server indicating the URL that referred it to you. Hence, in this instance, it contains the URL of the particular Google search page that your link was on.
 
e.g. [http://www.google.co.uk/search?hl=en&q=ubuntu&start=10&sa=N](http://www.google.co.uk/search?hl=en&q=ubuntu&start=10&sa=N)
 
In this case the laguage was 'english', the search term was 'ubuntu' and it was on page 2 of the results (i.e. start at result 10 (first result = 0, ten results per page)). I don't know what &sa refers to, and no doubt there are many more strings available.
 
Most log analysers will parse the referrer URLs to summarise where visitors are coming from, and in the case of search engines what search terms they are using.
 
Mathew

---

### Post by Folk Theory on 2008-07-29
after the __utma, __utmb, __utmc and __utmz cookies i have this ones
__kti
__kts
__ktv
__ktt
s_cc
s_sq

what do these mean?

thank you for your help

---

### Post by MJN on 2008-07-29
Google Analytics Cookies - see [http://www.morevisibility.com/analyticsblog/from-__utma-to-__utmz-google-analytics-cookies.html](http://www.morevisibility.com/analyticsblog/from-__utma-to-__utmz-google-analytics-cookies.html)

Mathew

---

