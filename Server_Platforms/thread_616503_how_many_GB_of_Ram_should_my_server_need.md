---
title: "how many GB of Ram should my server need?"
date: 2007-11-18
forum: Server Platforms
---

### Post by tom_mk on 2007-11-18
hello, 

the question might b very simple to most ppl,
but as a newbie like me who is trying to set up an efficient server
i really need help

my problem is , i trying to get a server running
this server will consist of a few softwares
http server, db server and ads server, (plan to expand the number of server box later, but for now, # of server = 1)

let's say i pick this server out of nowhere
[http://www1.ap.dell.com/content/products/productdetails.aspx/pedge_840?c=th&l=en&s=lca](http://www1.ap.dell.com/content/products/productdetails.aspx/pedge_840?c=th&l=en&s=lca)

and i estimated that there will be 1.75 request for one second
and each request size would b roughly b/w 12kb - 25kb

my question is.
how many GB of ram should i need?
:guitar:

Thanks for any suggestion.
Tom

---

### Post by James79 on 2007-11-18
It depends not only on the amount of traffic you'll be expecting, but also the type of site you will be hosting.

To serve static pages isn't very complicated. Even my lowly 550mhz server with 128mb of ram could keep up with a request every 1-2 seconds provided it doesn't have to perform instensive server side scripting.

Where the ram will serve you most is for your DB - but even there, how large of a DB are we talking about? Again, my server is running several small DBs without any problems at all.

If your DB is small, and your pages are simple (or static), then don't worry too much about getting a lot of ram. _1 or 2gb will be more than enough_, and that's only because ram is so cheap now there's no point in getting any less than that.

Hope that helps.

---

### Post by tom_mk on 2007-11-18
what if i going to serve lots of dynamic page,
what are the factors that i should keep in mind,
so that i could consider the amount of Ram correctly.

assume that the size of DB is around ~2GB
and could grow to 5Gb

Thanks a lot
Tom
:popcorn:

---

### Post by James79 on 2007-11-19
Where your ram will be needed most is if you do *lots of large joins* on your DB. Even if your DB is several gigs large with several million records in it, if all you are doing is perfoming simple index queries you _won't be taxing it much_. So only you know unfortunately how much you need. 

PHP and other server side scripting (ie dynamic pages) will be more CPU intensive than anything else. DBs also loooove cpu power :)

It sounds like your needs are fairly modest... Get a 2gb machine with a modern dual core CPU and you should be fine. 

If you aren't satisfied with my explanation, perhaps you could describe a little further exactly what type of websites you will be hosting with this server?

---

