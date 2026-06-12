---
title: "Is it possible to monitor network traffic in specific webfolders?"
date: 2007-06-10
forum: Server Platforms
---

### Post by Mr-Heier on 2007-06-10
I want to monitor the traffic from 
[www.mydomain.com/video](www.mydomain.com/video)
[www.mydomain.com/forum](www.mydomain.com/forum)

etc....

Is this possible? I have munin but it doesnt seem possible.

---

### Post by Mr. C. on 2007-06-10
Sure.  

The most reliable way is to configure them as virtual servers, and use separate logs files per virtual server.

Another way would be to use a log parser to analyze the HTTP requests.   However, this method requires work to do accurately.

MrC

---

