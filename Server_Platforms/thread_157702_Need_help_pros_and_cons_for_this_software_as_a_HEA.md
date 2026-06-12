---
title: "Need help: pros and cons for this software as a HEAVLY used server"
date: 2006-04-09
forum: Server Platforms
---

### Post by benkillin on 2006-04-09
I work for the University of Virginia's ITC division as a web developer. I found out a few days ago that we are planning to upgrade our server to an awesom hardware cluster of 2 HP blade machines for our production server and another 2 machines for our development server. My boss asked me to get a list of pros and cons to upgrade the software to something more reasonable than what we have been using in the past.

Before the servers were based off of AIX using extremely outdated software: Apache 1.3, PHP 4.2.3, and mysql 3. 

My boss and I want to put this software on the new server: a Linux OS (I prefer a deiban based distro like Ubuntu because of the ease of software installation using apt-get) Apache 2, PHP 5, Mysql 5, Ruby and Rails, and FastCGI. 

I need every positive detail documented so my boss's boss can present her boss with the proposal that will convince them to do things our way instead of their way with these new servers. So far I have these pros documented:

mini-Cluster:
FAST access
downtime minimal
can handle the growing number of requests (Our current website is around 12,000 pages, about 1000 of which are active content (perl, PHP, cgi, etc...))

Ubuntu OS (I'm pusing for Ubuntu, but any debian deritive would be fine by me):
Easy program installation and upgrades using apt-get
active development community; new version of OS every 6 months
easy to work on
huge software repositories
Lots more pople know how to use Linux better then AIX (bringing increased productivity)

Apache 2:
less security concerns
more features
... that's all I can think of right now

PHP 5:
Better Object Oriented support, you can use almost all features of inheritance
more features
... that's all I can think of right now

Mysql 5:
much better then mysql 3
more features
less security concerns
faster
... that's all I can think of right now

Ruby and Rails/FastCGI:
Fastest language to develop in (both in execution time and development time)
beatuful use of CRUD
easy to maintain code
... that's all I can think of right now

As you can see, my list is quite short. 
Could somebody please help me expand this list? It is important to me that they agree to this proposal because it will actually make my job FUN if we have all this cool software and hardware to develop on.

Thank you in advance for anybody that will help me.

---

### Post by LordHunter317 on 2006-04-09
> **benkillin]Before the servers were based off of AIX using extremely outdated software: Apache 1.3, PHP 4.2.3, and mysql 3.[/quote]Of those, only one is outdated enough to be a problem.

> can handle the growing number of requests (Our current website is around 12,000 pages, about 1000 of which are active content (perl, PHP, cgi, etc...))This is meanigless.  If those 1000 pages are being hit 99% of the time, you need to upgrade.  If they're 0.001% of the time, you don't.  A 486 can push static pages to 10 Mb/s network saturation on any webserver, given a good bit of RAM.

> active development community said:**
> A new version of the OS every 6 months isn't a positive thing per se for production servers.

[quote]huge software repositoriesUnsupported, mind you, which may or may not be an issue.

[quote]Lots more pople know how to use Linux better then AIX (bringing increased productivity)Seeing as the people who should be admining it ought to already be AIX trained, there is no benefit here unless your turnover rates are very high.

> Apache 2:
less security concerns
more features
... that's all I can think of right nowAnd both are wrong.

> PHP 5:
Better Object Oriented support, you can use almost all features of inheritance
more features
... that's all I can think of right nowAnd are meaningless, unless you're doing new development.  You may have to have PHP4 installed anyway, because PHP5 isn't upwards compatible, no matter what php.net may say.

> Ruby and Rails/FastCGI:
Fastest language to develop in (both in execution time and development time)Uhh, no on both counts. 

> Could somebody please help me expand this list?No, because it's clear you're just trying to come up with the biggest OSS buzzword list you can.  It's clear you're not even aware of the plusses or minuses of any of your recommendations, nor have done the research necessary.  It's also apparent you're not aware of your employer's concerns, which is where you need to start.

You can't solve a problem until you know what the problem is.

> It is important to me that they agree to this proposal because it will actually make my job FUN if we have all this cool software and hardware to develop on.Your responsibility isn't to make your job fun.  It's to server your employers needs in the way that benefits them the most.  That means recommending them the solutions that make the best use of their money.

Fun, when it happens, is an added bonus.

---

### Post by Glut on 2006-04-10
As a developer, I see your role in the procurement process as providing a list of software packages that you can use and providing reasons why your prefered packages should be chosen.
These reasons should be reasons that make a difference to the way that you work and the results that you produce. As such, I think that arguing for one OS over another is not your role, but the role of the administrators that will look after the machines. 

Probably presenting arguments around the web server is out of your control as well, unless you have parculiar knowledge of one over another. I would stick to  preseting a list of languages that you need, with reasoning and then a list that you want. Be well researched because if you get shot down like above you may never get another go at making recommendations again. Don't provide just dot points, maybe 200-300 words per recommendation. Of the above, I would limit myself to PHP, MySQL and Ruby-on-Rails. Avoid performance arguments as they are hard to prove with scripts and easily countered with 'well I could do it in assembler'. Good arguments would usually involve backwards compatibility (and by association useful lifetime), language skills currently possessed by the team, ease in recruiting new employees with those skills, language maintainence i.e. who patches and how often.

---

### Post by benkillin on 2006-04-10
These choices are MY BOSS'S. He wants this software on the server and asked me to get the plusses and minuses. My list was not right and I knew it, that is why I posted on this forum.

The OS is a minor issue to me. My boss wants a GNU/Linux OS on the machine, so I suggested Ubuntu because I am most familiar with it.

Thank you for your responses.

---

### Post by sciurus on 2006-04-10
[QUOTE=benkillin]The OS is a minor issue to me. My boss wants a GNU/Linux OS on the machine, so I suggested Ubuntu because I am most familiar with it.[/QUOTE]

As much as I like Ubuntu, Dapper will be the first release with a server target. I wouldn't be comfortable recommending that in my workplace. One thing to consider is what operating systems the hardware manufacturer supports. For instance, Sun will provide support for Solaris, Red Hat, or SuSE on their Sun Fire series. I don't know what HP's policies are.

---

