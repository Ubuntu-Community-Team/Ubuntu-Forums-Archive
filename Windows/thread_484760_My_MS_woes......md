---
title: "My MS woes....."
date: 2007-06-26
forum: Windows
---

### Post by Circus-Killer on 2007-06-26
Well, I know there are a thousand of these MS bashing threads, but this one is the Business Edition. For a few extra grand you can get to read the Ultimate Edition, but blah, im just talking rubbish.

Anyways, as said, this is the business edition, in other words I'm about to release my woes on to you, for no benefit to either of us. Well, where to start. Today, we got new machines in the office. And what pretty machines they are. Nice 19" LCD's, core 2 duo 1.8ghz processor, gig of ram. All round, nice machines, except for the vista installed. But unfortunetly, this is work, and I dont have a choice, so I happily went along with vista.

Here's where my troubles start. About a good 30% to 40% of our companies data is on a MS SQL Server 2000, which is unsupported in Vista. So not only do I have to switch to SQL server 2005, but our main server has to be upgraded. The worst part is that my company has no one in the IT department with half-a-brain, so it looks like it will be me doing the upgrade. Which sucks, mainly because I'm not in the IT department, yet most of their responsibilities fall on me. Now, that is more of a problem with my company than MS. But what my gripe is, is that it is such a bleeding mission to upgrade from one SQL server to the next.

Basically, just switching to Vista, is going to put my work on hold for a couple of weeks, at the very least. Unfortunetly, managers really don't have the brains to look into things before making decisions, leaving the little guys to sort out the crap thats left behind.

Anyways, thats my rant for the day....apologies to those who found this post mundane.

---

### Post by timcredible on 2007-06-26
a lot of us are in the same boat - stuck with using windows of some form at work.  every time i get the blue screen of death i just shake my fists and wonder why??????  of course, the answer is that management just doesn't understand.  most of the it people where i work run linux at home or on 'test' machines, and if you look at IBMs ESX product that a lot of companies are moving to, you'll see that they're running windows in vmware on top of linux (makes it easy to provide failover).  but still, we're stuck with windows as the desktop of choice at most businesses  ;-(

---

### Post by mips on 2007-06-27
Can the DB not be migrated to something like [MySQL]("http://www.mysql.com/") ?  This would be an open platform that can be run on a rock solid Linux/BSD server or even a windows server and you have no licensing fees.

---

### Post by Circus-Killer on 2007-06-27
well, i dont know.....
i would have to look into it. unfortunetly the database server hosts a number of seperate databases for seperate  applications (some belonging to seperate companies). however, since i am the most knowledgable person about, i do have quite a bit of say.

only problem is, last time i checked, coldfusion couldnt connect to mysql server. but then again i could be completely wrong. i dont know. as said, need to look into it. but it is a marvelous idea. i actually dont know why i didnt think of it. thanks for that mips.

edit: actually. i just remembered that a while back we were gonna switch our oracle servers to linux. hmmmm.......
       i can see a lot of hard work coming my way. but by the end of it......oh the possibilities.....

       thanks very much for that mips, you've given me such a brilliant idea. so brilliant, that it would make me indespensable. *rubs hands evily*
       thanks you very much.:twisted:

---

### Post by mips on 2007-06-27
> **Circus-Killer said:**
> 
       thanks very much for that mips, you've given me such a brilliant idea. so brilliant, that it would make me indespensable. *rubs hands evily*
       thanks you very much.:twisted:

Lol, I know jack about SQL. All I know is that MySQL is an alternative to proprietary SQL and it runs on just about any platform.

Just pick a stable server platform whatever you do. Something like Debian for example. I would also look into FreeBSD but dunno what the performance is like on that OS.

Is this an internet facing (edge) db or a internl one as security might be an issue. Then again if you are using MS now I dont see any degregation in security...

---

### Post by Circus-Killer on 2007-06-27
well, i'de probably go for linux, would have to try out a few distros before deciding. luckily, the servers are all for internal purposes, with security only being a mild issue. actually. the switch i'm planning would take quite a few months to plan and implement, but it could be well worth it.

cos now i'm not just thinking about one db server. i'm thinking of switching 2 out 3 servers, and these servers are huge, and critical. heavy  stuff. this is gonna need some long thought.

---

### Post by mips on 2007-06-27
[http://dev.mysql.com/books/hpmysql-excerpts/ch06.html](http://dev.mysql.com/books/hpmysql-excerpts/ch06.html)
[http://jeffr-tech.livejournal.com/5705.html](http://jeffr-tech.livejournal.com/5705.html)

---

