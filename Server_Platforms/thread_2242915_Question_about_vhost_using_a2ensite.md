---
title: "Question about vhost using a2ensite"
date: 2014-09-04
forum: Server Platforms
---

### Post by dzulkifli on 2014-09-04
hi and good day,

the scenario is something like this.  we have around 24 websites running joomla 3 and wanted to host it in just one server. my questions is how many in number or the maximum websites can be reliable in apache vhost using a2ensite? in terms of performance wise it is good to host all of them into single server?

because of many issues in our server which is running windows, we need to migrate it to ubuntu 14.04. 

tq for an advise..

---

### Post by TheFu on 2014-09-04
I've seen servers host thousands of virtual websites.
Never used joolma, so I don't know how taxing it is.
If you plan to host more than 10 websites, definitely split the DBMS off to a different machine.

Performance considerations can't be quessed from the data provided and I suspect you don't have any performance statistics.  Best to gather those as you add more sites to the server - that should help to predict which part of the hardware will be the limiting factor first. Then you can take steps to address what needs addressing with facts, not guesses.

---

### Post by dudumomo on 2014-09-08
Hi dzulkifli,

I'm running close to 40 services (Not all websites) and a2ensite is managing them without a hurdle.
Some used a different domain name and most of them use a sub-domain.

I think the main question will be, can your current server host all these 24 Joomla websites.
How many visitors do you have? Bandwidth intensive? (Pictures, videos, etc..), how about disk access and Database performance, etc...

If all these are okay, no issue to have all of them in one server. (But obviously proper backup system is needed...all eggs in the same basket haha)

---

