---
title: "Head in the clouds!"
date: 2009-09-18
forum: The Cafe
---

### Post by Dragonbite on 2009-09-18
I keep hearing about Cloud computing, and I am not sure if I fully understand its difference from general websites.  The concept is interesting and I would be tempted to set up a "private cloud" at home to fool around with but don't know where to begin.

So I was wondering if anybody here is programming cloud applications and if so, what is a good way to get started?

Also, if anybody is managing servers which are running cloud applications, what is a good way to set up a server, what kind of iron do you need and what pitfalls are there?

Thanks.

---

### Post by castrojo on 2009-09-18
ubuntu-server comes with eucalyptus, which is a run-your-own cloud thing, I don't have the hardware at home to play with it though. 

I've been playing with amazon ec2 a bit to test the ubuntu EC2 images. I tested a few instances for about half a day (for about 24 cents worth of usage). As long as you don't keep the instances running when you don't need them it's pretty cheap.

---

### Post by wildman4god on 2009-09-18
Cloud computing is similar to grid computing back in the day of main frames, except that grid computing happened over a LAN and cloud computing happens over the public internet. Cloud computing is also a natural evolution in web pages, over time web pages added more and more functionality and finally some one said "Hey why don't we use this to make an app"

---

### Post by Dragonbite on 2009-09-18
I'm thinking of trying it with a home box because I'm cheap. :) 

Ubuntu Server with Eucalyptus is one platform I was thinking of, CentOS (since Red Hat is pushing for clouds) is another.

Programmically, then, the applications are basically built PHP or Python or Java or AJAX web pages that save and run on the server?

---

