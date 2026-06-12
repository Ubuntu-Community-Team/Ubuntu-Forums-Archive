---
title: "apache stats"
date: 2008-10-13
forum: Server Platforms
---

### Post by rwslippey on 2008-10-13
Good evening all,

I am looking for a good apache statistic package. Something that will give me server information and more inportantly page information on both of my virtual servers. 

I am just looking for information such as web hits. unique hits, server status... ... also I'm not sure if it would be possible to view the results  via either webmin or html as I configure the server remotly more offten than not..

thanks 


Rob

---

### Post by lykwydchykyn on 2008-10-13
Webmin has a module for Webalizer, the http log analysis package.  It uses your http logs for its data source, so you may need to tinker with your logging configuration to keep logs a certain time and not compress them (I had trouble working with bzip2 compressed logs last time I used webalizer, though that was on SLES not Ubuntu).  It's pretty thorough and generates nice charts too.

---

### Post by rwslippey on 2008-10-13
Hey that sounds great...

I am honestly very new to ubuntu and apache but over the past 2 and 3 months I have learned a ton!...  But I am hosting two websites for two amateur radio clubs I am with and our clubs have never had websites and from past experience I would like to improve web search results (SEO) and being able to track what works and what doesn't makes like a whole lot simpler!

appriciate the help, I'm adding a forum.... so Ill checking the webalizer out as soon as I am done once again appriciate the help

Rob

---

