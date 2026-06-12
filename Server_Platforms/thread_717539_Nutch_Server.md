---
title: "Nutch Server"
date: 2008-03-07
forum: Server Platforms
---

### Post by vanderkerkoff on 2008-03-07
Hello everyone

I've been using webglimpse on an old redhat box to index and search the index of a number of large websites.

It's been a crap experience all round, haven't liked webglimpse at all and found the support and documentation a bit painful.

I"ve started using solr to index and search my newer sites, writing the data into the database as it's added to the sites, much neater solution.  Old sites though, for them I still need an indexer and searching mechanism.

I've had a look at a few, and I think Nutch is winning so far and I'm going to try and install it on a brand new ubuntu box.

I'll keep my workings out so you can see how stupid/clever some of the things I'm doing are.

Has anyone built a Nutch server on Ubuntu to do what I've described above? 

Anyone have any other advice or suggest any other technologies?

---

### Post by monkeynuts84 on 2008-03-12
Hi,
    I've built a nutch system that is currently indexing UK only websites. There have been quite a few glitches along the way but fortunately I've documented them so if you have any issues let me and I'll see what I can do.

I've tried other products such as mnogo which are good but Nutch wins everytime. Check out some of the articles comparing Nutch against google.

Interestingly, the founder of wikipedia is probably going to use nutch for his new world wide search engine.

Regards,

monkeynuts84

My site, if you're interested, [http://www.webhopper.co.uk](http://www.webhopper.co.uk)

---

### Post by vanderkerkoff on 2008-03-28
Hi monkeynuts84.

I'm trying to style the search page and the results page and I'm having a bit of a time of it.

I found this link, is this the correct methodology or the methodology that you used?

[http://tinyurl.com/26nzfv](http://tinyurl.com/26nzfv)

All the documentation I'm finding is telling me it should be running on port 8080 as well, but mine runs on 8180, not a biggie, just thought I'd mention it.

---

### Post by monkeynuts84 on 2008-04-02
Apologies for not replying earlier but I didn't get a notification of your response. I have some custom jsp files in the root directory and a new logo. The jsp files point to the new logo and the search box.

Regarding ports: My site is an apache proxy (various methods are availble i.e mod_jk and mod_proxy ajp). Are you building on Linux or Windows?

Hope this helps.

---

### Post by vanderkerkoff on 2008-04-02
Hi Monkeynuts

I got the styling all sorted out, not as hard as I thought, everything was in the search.jsp file.

I'm building on a Ubuntu Linux box, hence the post in this forum mate.

I did some digging and I'm running it in tomcat5.5, I'm pretty certain I need to tell tomcat to run on port 80, I'll paste up how I work that out when I get some time.

I'm loving nutch though, very good so far, my auto script is starting tonight so I hope that goes OK, we're deleting the crawl filer completely, only a small crawl, 20000 pages at most.

thanks for getting back to me

---

### Post by monkeynuts84 on 2008-04-02
You could make Tomcat run on a port other than 8080/8081 (server.xml file) but then you bypass all the security features you get with Apache and mod_jk/mod_proxy ajp. To make it really simple you could simply make your Apache 2.2 virtual host file a proxy (very easy to do). This will at least hide tomcat from prying eyes. Also, if you do decide to decide to use only Tomcat make sure you read up on user roles and deletion of certain containers in tomcat.

Yeah, of course you're using Linux! My bad!

When does your site go live?

---

### Post by vanderkerkoff on 2008-04-07
I've used pound to catch on port 80 and hand over to tomcat on 8081, it will be invisible.

Also, if you do decide to decide to use only Tomcat make sure you read up on user roles and deletion of certain containers in tomcat.

I've never used tomcat before so this type of information is invaluable, cheers.

Search will be all online this week mate, I'll let you know when it starts

---

