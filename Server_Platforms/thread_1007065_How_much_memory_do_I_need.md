---
title: "How much memory do I need?"
date: 2008-12-10
forum: Server Platforms
---

### Post by clay7 on 2008-12-10
Hello,

I am getting an Ubuntu 8.04 LTS VPS that gives me 128 MB RAM. It will be managed myself through Webmin. My site has no streaming media and I don't expect more than 1000 visits a month. The site is only 15 pages and only half of those run a small PHP script. Two pages access a MySql DB for access verification - nothing too complex. There are 2 files, 20MB each, that people can download, but I'm not concerned about bandwidth.

Is 128 MB RAM enough? Thanks!

---

### Post by jrusso2 on 2008-12-10
Personally I would want 512 mb of ram minimum for halfway decent performance.

128 mb is below the minimum of 256 mb which I wouldn't recommend.

---

### Post by clay7 on 2008-12-10
Thanks for your reply. I really don't know anything about server memory. I know desktop memory really well though.

1. What's the difference?

2. When you say that you wouldn't recommend 256 MB RAM (or even 128 ) for my site, why? It's a very small site and simple. The most complex thing it does is access a MySql db to verify a username and password. Just asking because I really don't know.

Thanks again!

---

### Post by CrucifiedEgo on 2008-12-10
I disagree!  </python>

I'm running a 64MB VPS from VPSlink for similar use.  A small site with a small DB backend (I use SQLite instead of MySQL -- check it out.)  In addition, I use it as a shell account and run irssi for IRC.  Instead of apache, I use lighttpd and PHP.  All told, i'm using 25MB of ram, 39 free.

If you can get away with not using MySQL, you can do a lot with very little.  The biggest memory hogs on my server right now are:

Screen - 6.4MB
irssi - 4.6MB
sshd(x2) - 2.6MB
bash

lighttpd is resident with only 660KB of RAM.  Using SQLite is great because it uses the same syntax as MySQL (basically) and saves to a flat file which makes it portable.  

Let me know if you need help, fitting a lot into a little is a very rewarding challenge.

---

### Post by clay7 on 2008-12-10
Mahalo! I hadn't thought of MySql Lite, but I will look into it. Any idea how much memory that uses compared to MySql 5?

---

### Post by khelben1979 on 2008-12-10
I don't know myself, but perhaps [this thread]("http://www.codingforums.com/showthread.php?t=48735") can be of interest?

According to the thread they are stating that it's better to stick with MySQL than MySQL Lite, according to my interpretation of the conversation.

---

### Post by CrucifiedEgo on 2008-12-10
They're targeting very different markets.  MySQL is great for high load applications and very tricky queries.  For pretty basic queries and low volumes, SQLite is a great alternative.  The main advantage is that it works without a daemon -- you load up the libraries and go.  Firefox uses SQLite for storage, as does Rythymbox and I think Amarok.  

When PHP goes to use the sqlite commands, it of course has to load the libraries into memory which takes a couple megs, but it's freed as soon as the script is over, instead of staying resident with many MB of RAM eaten up for nothing.

---

### Post by HermanAB on 2008-12-10
There is an ancient American proverb, circa 1980, which states: "You can never be rich enough, thin enough, or have enough memory in your computer".

---

### Post by Iowan on 2008-12-11
Along those lines, I suppose one could re-phrase the old question "How much money is enough?" to read "How much memory is enough?" The answer to both is "Just a little more!"

---

### Post by vpsville on 2008-12-12
128 will be fine for your intended usage.  But remember to edit the config of MySQL as it uses 100MB by default. With a quick edit you can bring it down to 30MB.

You may also want to use the 1.3 family of Apache instead of 2.x, its much leaner.

---

### Post by rokabear on 2011-04-17
It may depend on whether you are using OpenVZ or XEN or another [VPS]("http://www.rokabear.com/vps.html") tech.  With OpenVZ you may be able to get away with a 64, but you should lower MYSQL like the previous post described.

One common mistake in purchasing a vps is that people focus more on RAM than performance. Ram is important as a measure of what you need to fit all of your apps into memory.  But if you are on an oversubscribed box, your app may still run slow.

Try a provider that allows you to start at a lower end [cheap vps]("http://www.rokabear.com/vps.html") and try it out.  You can measure your ram and performance and upgrade or downgrade as you need.

Also make sure the provider has a control panel that allows you to monitor your space usage and bandwidth.  This is a common source of surprise at the end of the month when a customer gets overage charges.

Patrick
Rokabear Support

---

### Post by SeijiSensei on 2011-04-17
Patrick, no one has posted in this thread since 2008, so I'm guessing whatever concerns the OP had have long been resolved.

---

