---
title: "Apache service (CMS 3 Flash Site)"
date: 2016-07-26
forum: Server Platforms
---

### Post by bonnet26 on 2016-07-26
Hello,


It's my first publication and my native language is Spanish so I apologize for any inconvenience earlier.


I have some time with this problem (1 month) I'm installing a webpage based on Ubuntu 16.04 server, the page is a flash site (cms 3) and support this do not help much really, everything revolves around permits apache to write and modify the site files and thus can perform the installation.


When I can solve some other permits fail so they tell me that there is a fault in permits to a higher level, my question what is the most optimal configuration permits a website?


Thank you very much for your help and hope soon to be able to join this great community making contributions and helping others.

---

### Post by Graham_Willis on 2016-07-30
Generally, if you set up (inside public_html assuming that you're running Apache) file permissions to 644 and directory permissions to 755, then the page should load nicely. However, it's possible that it'll work with more restrictive permissions and they can be even recommended. Anyway, you can try what I wrote in the first sentence at least just to check if the site'll work properly and start restricting permissions later. However, if you messed up higher-level directories, then much more must be corrected.

---

