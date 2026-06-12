---
title: "awstats for www and no-www domains"
date: 2008-07-26
forum: Server Platforms
---

### Post by girasquid on 2008-07-26
Hello, all.

I am currently using awstats to collect statistics on a number of virtualhosts that I host. My configuration files are all stored in /etc/awstats, with names in the form of **/etc/awstats/awstats.domain.com.conf**.

I have also provided an alias under Apache to access a user's stats - so they can visit mydomain.com/stats to get to their awstats page. However, because of the way that my configuration files are set up, they can only get to it from mydomain.com/stats - and **not** [www.mydomain.com/stats](www.mydomain.com/stats). 

Adding a second configuration file with a name like *awstats.[www.domain.com.conf](www.domain.com.conf)* solves this problem, but unfortunately means that awstats is treating the two domains separately - so if a user interacts with the www version vs. the no-www version, they will see different statistics. 

Is there a way to make sure that awstats works with and without the www, while still only having one configuration file?

Thanks,
Girasquid

---

