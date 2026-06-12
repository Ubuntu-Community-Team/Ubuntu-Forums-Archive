---
title: "Tips for installing Ubuntu Server on an SSD?"
date: 2010-02-11
forum: Server Platforms
---

### Post by fizgig on 2010-02-11
I'm installing Ubuntu on an 8gig SSD (industrial grade (SLC-type) that isn't cheap).  I'm doing so because I read the MTBF is a bit better with SSD and this is going into a fanless box in an industrial environment with a little vibration.

It will be a very low-load machine as it will simply be getting temperature data through the network every five minutes or so and writing it to a mysql database.  It will also have apache running so that when someone wants to see a graph of the data, they can just look at the webpage it hosts.

System logging isn't important to me so I'd like to reduce or even disable it. Are there other settings I can do that will reduce access to the drive even further to get the longest lifetime possible?  I really want the temperature logging program to be the only constant use of the SSD after bootup.

Thanks for any tips!

---

### Post by dragos2 on 2010-02-11
Not relevant. SLC chips have a life expectancy of about 6 years with 10-20 GB of data
written to them daily.

So relax, after 3-4 years you will probably be replacing him with a faster one.

---

### Post by fizgig on 2010-02-11
That certainly makes me feel better.  Still, I don't plan to use the logs and would still love to know anything I can do that could make it last longer than 6 years.

[**This page**]("http://www.brighthub.com/computing/linux/articles/9170.aspx") has a few pointers but it isn't specific to Ubuntu.  That might not matter at all but thought there might be an ubuntu guide to do this kind of thing somewhere.

---

