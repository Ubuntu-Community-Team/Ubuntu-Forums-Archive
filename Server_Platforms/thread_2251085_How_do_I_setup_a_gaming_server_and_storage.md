---
title: "How do I setup a gaming server and storage?"
date: 2014-11-01
forum: Server Platforms
---

### Post by adam15 on 2014-11-01
I am looking at putting up a gaming  server but i am not sure how to put it up with alot of storage as i have never done anything at this size before. Also how would i add more storage as need.

Is there any info or guides to do this 

Any help will be great
Thanks

---

### Post by yancek on 2014-11-01
Not sure what "put it up with a lot of storage" means?  If you need a lot of storage the obvious answer is get large hard drives.  If you mean setting up a server to host the game that is another question.

---

### Post by adam15 on 2014-11-01
i mean like a host where when someone hits my server it will pull the data from the storage servers and not the one with the os on it 

is that possible



for a gaming server i think i am going to use smartfox for that running on Ubuntu

---

### Post by pfeiffep on 2014-11-02
> **adam15 said:**
> i mean like a host where when someone hits my server it will pull the data from the storage servers and not the one with the os on it 

is that possible for a gaming server i think i am going to use smartfox for that running on Ubuntu 
 I think what you need is load balancing software / hardware.  I'm only familiar with enterprise offering from F5 which is probably way more than you need.

---

### Post by adam15 on 2014-11-03
i think i need to to put up a server farm for what i am trying to do but not sure how to connect everything to add storage as i need it

---

### Post by adam15 on 2014-11-07
ok so i need to run load balancing software and server clusters 

and that will allow me to hold all my users profile from the game i am looking at putting up 

I would use maas for the cluster is that right

---

### Post by Bucky Ball on 2014-11-07
*Thread moved to **Server Platforms**.*

... and thread title changed to describe what you actually want support with. Feel free to change it to something you think is more descriptive, but NOT 'I want info' as it tells potential helpers nothing and generic thread titles don't help your chances of getting support. Good luck. ;)

---

### Post by adam15 on 2014-11-07
thanks for sending my post to the right place

---

### Post by adam15 on 2014-11-09
so i take it either no one knows how to do this or just doesn't want to share how to do it.

---

### Post by TheFu on 2014-11-09
> **adam15 said:**
> so i take it either no one knows how to do this or just doesn't want to share how to do it.

Or the question is too vague. "Gaming Server" could mean almost anything. "Storage Server" can also mean almost anything.

Or the time necessary to get enough real information to make a reasonable, helpful, response it too great.  We are all volunteers here.

If any concrete details were provided with the questions, someone may be able to help. 
* the exact game(s) to be run - if they aren't well known, something similar architected in a similar way would help. The requirements for java-based games is completely different from php or perl-based games.
* amount of storage, redundancy for that storage, backups, etc.
* number of users, total and concurrent
* type of hardware to be used
* the knowledge level of the people who will implement all this stuff.  Helping a noob is much harder than talking with a fellow expert with any background in this stuff.

Plus, while I've been running servers for decades, I've only run 1 gaming server in all that time and only for a few months. That experience probably does NOT translate easily to what you know or need.

---

### Post by adam15 on 2014-11-09
ok this is what i am trying to do

1. I have ran servers for other things like i have put up my own hosting server with no problem
2. i am looking to implement smart fox server as the gaming platform 
3. The game will be a mmorts game that will need to run on different browsers and from my website.

this is really what i need help with is the storage
I can not figure out how to get the storage to store all the users info for the game 

I need to have 1 server for my website and the login and other servers to hold all the info for the games and the users 
somthing like a company called kixeye does i am looking to do the same 

let me know if this helps a little better on what i am trying to do

---

### Post by lukeiamyourfather on 2014-11-10
From a quick Google search it sounds like SmartFoxServer is a API to facilitate creating multiplayer games which has a server and a client. In that case the question is more like how do I setup a database server with scalable storage. You might consider their "cloud" offerings if you're asking these kinds of questions.

[http://smartfoxserver.com/cloud](http://smartfoxserver.com/cloud)

If you want to do it all yourself you have a lot to learn. This would be a good place to start as it covers all of the basics of setting up Ubuntu Server.

[https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)

From there you can install the applications you want like SmartFoxServer. As for scalable storage I think the best option available right now is ZFS on Linux but there are lots of other options out there with various features.

[http://zfsonlinux.org/](http://zfsonlinux.org/)

---

### Post by TheFu on 2014-11-10
> **adam15 said:**
> let me know if this helps a little better on what i am trying to do

No, it doesn't help me. Specific questions were asked. If you don't understand, ask for clarification.
> 
* the exact game(s) to be run - if they aren't well known, something similar architected in a similar way would help. The requirements for java-based games is completely different from php or perl-based games.
* amount of storage, redundancy for that storage, backups, etc.
* number of users, total and concurrent
* type of hardware to be used

You've answered 1 of those. Thanks.  The Overview page for the server was next to worthless - it was all marketing speak - useless.  [http://smartfoxserver.com/products/sfs2x#p=features](http://smartfoxserver.com/products/sfs2x#p=features) finally said something useful - java server, odbc/jdbc for DB access.  Meh.

---

### Post by adam15 on 2014-11-11
the exact game(s) to be run - if they aren't well known, something  similar architected in a similar way would help. The requirements for  java-based games is completely different from php or perl-based games.

the game is not yet developed but it will be like a game called war commander by kixeye

* amount of storage, redundancy for that storage, backups, etc.

amount of storage i am not really sure as of yet but maybe to start something like 10tb but i will need that scalable 

redundancy for that storage, backups, etc     not sure what you mean 

* number of users, total and concurrent

number of users is hard to say it could be 100 to 100,000+
* type of hardware to be used
we will be using dell servers no sure on exact ones yet 
going to use extreme switches 

this is for a new company in the early stages so some of the info i may not have right yet   i am trying to give you what you need to help me

---

### Post by lukeiamyourfather on 2014-11-11
All of those things are dependent on how many users you will have and how much data they will generate. There are many orders of magnitude difference in the possibilities that we can't possibly accommodate for in our advice. For example 100 users with 1 MB of data each isn't a big deal, even a Raspberry Pi with a SD card for storage could handle that. However 500,000 users with 10 GB of data each isn't something that could be handled on a single server and would require a cluster.

If you don't have answers to these kinds of questions, like how much data each user will generate or if that data needs to be backed up, then either you're thinking too far ahead and wasting time or you're in over your head and should consider hiring people with the expertise you'll need for a project like this to succeed.

---

### Post by adam15 on 2014-11-11
ok i get that and i am trying to get some data that will help 

yes i will need backup for sure and will need redundancy for that storage so there is minimal to no downtime if something were to fail

as for users lets just say 500k with 5GB of data each   and i was thinking of needing a cluster     i was looking at mysql cluster

---

### Post by TheFu on 2014-11-11
> **lukeiamyourfather said:**
> If you don't have answers to these kinds of questions, like how much data each user will generate or if that data needs to be backed up, then either you're thinking too far ahead and wasting time or you're in over your head and should consider hiring people with the expertise you'll need for a project like this to succeed.

Testify!

I should say that since 1999, I worked as a technical/enterprise architect designing and implementing stuff like this for internal clients. With the data provided so far, we would reject the request and suggest a 30 hr paid consultation with one of my junior guys to gather requirements before they would be allowed to submit another request for an estimate.  90% of the time, that tiny amount of budget (about $5k) for the consultation would make them go away.  Sometimes political mandates would force we return an estimate so we'd ballpark it high - very high - and assume the worst for everything.

So ... with what I know today, I'll ballpark it for you:
* At least 20 servers - average $10K each
* At least 3 locations involved based on redundancy needs.
* We'd have to build out a SAN - with 5G/user, that means we cannot use cheap SAN equipment - NetApp or EMC is required -  $250K per location (could be much higher depending on required software (replication, dedup, BCVs, etc))
* Cisco switches for networking $15K (these are the cheap ones) 
* SAN switches (Brocade/Cisco) $30K
* Racks, PDUs, assume DC provided power backup - $20K
* assorted cables (fibre, CAT5e) $5K
* Assuming $0 in server software costs
* No tape drives, silos, or media included. site-to-site backups to SAN storage is expected.
* Est 2 FTE for server support/ month (devops experts)
* Est 1 FTE for DB support/month

Much of this assumes negotiated 40% discounts off list prices for equipment. 
I didn't include DC costs, since were I worked we didn't pay ourselves for that stuff.  Perhaps $5K/month? I dunno.

So ... for that estimate, a $150 check to me please. ;)   You could contact Dell and they will build in the price of their solution design team into the equipment prices. Enjoy.

Of course, the real requirements are currently unknown, so much less may be possible. We don't know that yet.

---

