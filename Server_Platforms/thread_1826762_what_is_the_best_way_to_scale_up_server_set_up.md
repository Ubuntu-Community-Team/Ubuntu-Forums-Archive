---
title: "what is the best way to scale up server set up?"
date: 2011-08-17
forum: Server Platforms
---

### Post by 007casper on 2011-08-17
what is the best way to scale up server set up for a high growth site?

- without getting a heart attack, where you can just open up a beer and watch tv as you push a red button to scale the server. :D

lets assume the site is getting 100,000 people a day. 
And, in thirty days, it will be getting 9 million people a month, and in a few months it will get 9 million people a day.  (I know it is a bit crazy)

How would you structure a roll out?

two load balancers, two front end app servers, two database servers, and a cdn.  And as traffic builds up, you would up the front end app servers, and maybe add two slave database servers.  ??? and maybe replicate the servers to east and the west to serve different parts of the world.

What kind of hardware?  

I know it is a bit weird question, and it matters a lot on app, server hardware, server set up, style, class, lifestyle etc - I just want to see if there are any aha moments and awesome set ups that I am not aware of...

I mean I even heard of only two servers, and a cdn :wink:

it is a serious question by the way ~

---

### Post by Perfect Storm on 2011-08-17
Moved to Server Platforms forum.

---

### Post by ocia on 2011-08-17
Well...

Before you're going to buy/lease/rent new servers, I would take a look first in optimizing your server setup.
And it all really depends on what kind of website.
If it's a very static website, you can get great use of caching the pages and even the SQL-queries.
Also, make sure (if you're not going for storage) that your server makes use of 15k RPM disks in a RAID10 config.
If you only have a 'read-heavy' website (for your disks), you can also use RAID5(0) or RAID6(0)

And if you're thinking about load-balancers, don't (until 5 or more webservers). You can use the DNS trick of load balancing: Round-Robin ;)
[http://en.wikipedia.org/wiki/Round-robin]("http://en.wikipedia.org/wiki/Round-robin")


Conclusion of my post:
Optimize first, then upgrade.
Especially for the MySQL-part, there is a LOT to optimize...

Hope this helps! ;)

---

### Post by 007casper on 2011-08-17
Above all, make sure the server makes use of 15k RPM disks in a raid 10 config.

so, you are suggesting I optimize mysql; cache the pages, and SQL queries, and dont load balance till 5 or more servers. Are these 5 servers all app servers?

so, would you suggest to use three servers?  CDN, One for the app, the other for mysql, and optimize these two servers in every shape and form, especially tune mysql server. Of course, mix all these with cache.  

Then, clone app server, and data server.

Then, roll out to two app, two database for failover, redundancy, round-robin load balancing. That makes four servers.  If the load is getting heavy add one more app server.  Thats five.

If adding any more front end app server, then include two load balancer.

right?

---

### Post by 007casper on 2011-08-20
> Conclusion of my post:
Optimize first, then upgrade.
Especially for the MySQL-part, there is a LOT to optimize...

I have been thinking about this... 

I agree optimizing is important, and it is crucial.  However, optimizing to the full extent could be silly.  

Applications improve with upcoming versions and change.  What works today might not work with tomorrow's update.

In that case, structuring a roll out without optimization might be more feasible. Even if you know, you can get much better efficiency with optimization.

It is like the bonus that they attach to your salary.  It is nice to get it, but you dont really count it to the bottom line till you receive it.

I think optimization a server is a bit like that.  It is a nice bonus.  However, how do you roll servers rapidly on a growing site?

---

### Post by Sanados on 2011-08-22
9 million ppl a day are a lot.

Also adding slaves to mysql might work out up to 7-8? slaves then you get too much replication overhead.

As stated above ... first optimize then upgrade.
And i would a layer in between .... optimize - cache - upgrade.
Also split!
Like server images and static content from other webserver ( perhaps using other webserver software that is better suited for your type of files)


Actually ... fast hard disks ... i would not go down that road.
Webserver normally do not have much disk read write ... especially when you outsource logging to scribe for example and keep htdocs in ramdrive.

And i would start to loadbalance already with 2 www ... when you use round-robin (dns based, session based, .... ) you can basically get 1 bad client to get your site down for half of your visitors.


would also start with 4 server:
2 loadbalancer (lvs)
1 www (with apc-opcode cache to beginn with)
1 database

on upgrade first adding wwws (further use of apc) and relocating the sessions to the loadbalancers with sharedance
then adding memcache server
finally adding slaves to your master and generate mysql slave connection loadbalanced (be aware that your application has to able to differ master and slave connection)

I let aside fileserver ... just hoping you do not need Terrabytes on files. (if you have take a look at mogilefs, i love it for growing environments)



Next step will most likely be energy saving ... so shutting down wwws/mysql slaves when there is no load on your site and wake up on lan.

---

### Post by spynappels on 2011-08-23
Just reading your other posts, are you deploying/running this on a (number of) VPS server(s)?

At the 9 million hits per day, you should definitely be looking at 2 dedicated loadbalancer servers as the only internet facing servers in a HA scenario. These can also act as a firewall, or can be placed behind a separate firewall. These can then farm out connections to www servers, which can then connect to DB servers on a separate VLAN or even a physically separate network.

As to the number of www and DB servers required, this is definitely dependent on a number of factors such as hardware spec, query complexity etc.

If you want to go for east-west replication for geolocation, you need 2 HA loadbalancers in each location, but this will give further redundancy in terms of one physical location going down, you will be able to direct global traffic to the remaining location. Your DNS should be able to manage the geo-location based load balancing.

---

### Post by 007casper on 2011-08-27
@Sanados.  Thank you so much for your input.

I have been checking out MogileFS.  Thank you so much for the heads up.  I am definitely going to give it a 'go' at one point.

at the moment I have a loadbalancer, two application servers, one database server, and a CDN.

I do understand, this is not a failover set up.  Especially from the database side.  It will be nice, if mysql was separated with two masters or master/slave set up.  However, I read in a a few places that it is easy to have a read, write issues. Also, as suggested by you replication issues.  I have to figure out how to handle it without having database issues.

Energy saving is always on an issue.

@spynappels.  As the site is growing, it wont be cost effective to keep this on VPS servers.  

I would go fully dedicated at every level from loadbalancer, appserver to data server.  It will give me breathing room at every level.

At the moment, two application server gives me high availability in a silly way.  I can go up on the number of servers at any moment.  Take one of them out, reboot etc without effecting the site.  I do realize this is not a bullet proof at the moment, and it is not a true HA set up with heartbeat, ip failover etc.  I should establish those.  I should also have another set of servers in a seperate datacenter.  Serve different geo locations, and if one of the datacenter power goes out, hope the other location can handle the load.  Maybe it will be even feasible to have basic 'stand by' set up in a third location if load becomes a burden.

However, most people dont interact with sites in general.  They just observe.  

Besides, caching files. If you serve plain static pages, and take out of dynamic / database connection out of the equation.  The site flies, servers have less load.  I would like to get it to a point that the site only becomes dynamic, if user/visitor decides to interact with the site - only for write.  In any other case, the application would serve only static pages.  At that point, the only bottle neck becomes the pipe you are connected to... any thoughts on this?

---

### Post by Dangertux on 2011-08-27
I completely agree with sanados that is quality advice in fact I only posted because I have sort of been following your string of posts and remember you said you ran a rapidly growing wordpress site. You should toss me a link in a private message I am dying to see whatever it is that is becoming so large so quickly that you are doing these types of upgrades.

---

### Post by robgr85 on 2011-08-29
> **Sanados said:**
> 
As stated above ... first optimize then upgrade.
And i would a layer in between .... optimize - cache - upgrade.


+1, optimizing SQL & php code can really make a big difference with such a huge traffic. Optimizing your queries might boost Your capabilities (I've done some optimizing, and have seen even experienced programmers writing poor SQL queries, that could be speed up even 5-10 times with simple changes). It makes real difference where high traffic occurs.

Optimize Your code, your servers (both configuration & appropriate hardware) cache what can be cached and then think about everything else. 

> 
You should toss me a link in a private message I am dying to see whatever it is that is becoming so large so quickly that you are doing these types of upgrades. 


I could bet that it might be some kind of video porn website ;-) Or maybe some new press, tv, social networking or website similar to digg... ;)

---

### Post by 007casper on 2011-08-29
> I could bet that it might be some kind of video porn website :wink: Or maybe some new press, tv, social networking or website similar to digg... :wink:

I cant let the cat out of the bag.  It is a state secret.:wink:

---

