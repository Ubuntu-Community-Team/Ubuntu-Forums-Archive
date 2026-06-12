---
title: "Advice needed for scaling up a web application"
date: 2015-07-06
forum: Server Platforms
---

### Post by coldraven on 2015-07-06
I'm involved with a project that's yet to make any money. It's an application that runs on a LAMP stack and currently has <1000 users. I have to give a presentation to a major organisation with the possibility of expanding that to maybe 250,000 users. I know very little about scaling up systems. Can anyone point me at a primer?
I'm not expecting to become an expert but I do need to know the buzzwords :) I hope that this post does not infringe any forum rules.

---

### Post by tgalati4 on 2015-07-07
Good luck.  Scale-up is normally handled with virtualization and migrating your local service to the Cloud so that you can "spin up" additional computer horsepower as it is needed.

[http://www.explainthatstuff.com/cloud-computing-introduction.html](http://www.explainthatstuff.com/cloud-computing-introduction.html)

Perhaps describe what your service does and we can give a more focused answer.

Since I was wearing a Linode T-shirt while BBQing:  [https://www.linode.com/pricing](https://www.linode.com/pricing)

It might be helpful to include some specific scale-up scenarios in your presentation with cost ratios.  Venture capitalists like that stuff.

---

### Post by coldraven on 2015-07-08
Thanks for your reply, I read your links but still need to formulate a plan. I might try interesting someone that I know who has experience in big business projects. They would no doubt make a better job of it than me :)
> Perhaps describe what your service does and we can give a more focused answer.
It's not so easy to do that because I don't want to leak any info to competitors. It is a browser based series of forms, the user enters data that gets stored in a MySql database. The PHP does various tricks including sending parts of the data to a government database. For this reason the server has to comply with data protection rules. It's being hosted            in an ISO 27001 accredited           data centre, very expensive!
Sorry for being vague and not replying sooner, I was out of town yesterday.

---

### Post by SeijiSensei on 2015-07-08
The biggest problem is going to be contention over the database.  I'd probably choose PostgreSQL over MySQL if you're designing something to handle 200K users.  PostgreSQL is designed to work in "enterprise" environments where it competes with Oracle.  As a result, it has some excellent tools for [replication]("https://wiki.postgresql.org/wiki/Replication,_Clustering,_and_Connection_Pooling") that you'll will need to spread the load across multiple database servers.

---

### Post by TheFu on 2015-07-08
Scaling DBs is relatively similar the first few times - buy bigger HW, faster storage connections and more disks to stripe across. This is "scaling up."
Scaling the application layer and the web layers tend to be adding more servers, better caching and more localized locations closer to users. This is "scaling out."

Along the way, both methods become very costly and alternative methods become worth the effort in people-time.  That's where application architecture changes come in and more of the data will be put into a NoSQL DB.

You'll want to have monitoring going on all the current servers and start capturing stats around web and DB TPS, average pages sizes, and start caching as much of the web traffic as close to the end users as possible.  Without TPS and transaction size data, we aren't planning - we are guessing.  Professionals avoid trying to guess. 

+1 on postgres

BTW - last month the SELF had a track on scaling mysql/mariaDB. A few of the videos should be online here: [https://www.youtube.com/user/southeastlinuxfest/videos](https://www.youtube.com/user/southeastlinuxfest/videos)

---

### Post by coldraven on 2015-07-09
> **SeijiSensei said:**
> The biggest problem is going to be contention over the database.  I'd probably choose PostgreSQL over MySQL if you're designing something to handle 200K users.  PostgreSQL is designed to work in "enterprise" environments where it competes with Oracle.  As a result, it has some excellent tools for [replication]("https://wiki.postgresql.org/wiki/Replication,_Clustering,_and_Connection_Pooling") that you'll will need to spread the load across multiple database servers.
Thanks SeijiSensei, that is very informative.
And also thanks to TheFu, I had not known the difference between scaling up and out.
I'll mark this as solved but if anyone else has some good tips then feel free to chip in.

---

