---
title: "Any optimizations I can make for a new server?"
date: 2009-02-17
forum: Server Platforms
---

### Post by Znupi on 2009-02-17
My brother is getting a development server for a project of his. So I'm in charge of setting up the new server, and I think I'm going to use Ubuntu Server. Here are the server specs:
```
Case: Asus TA-851 MiddleTower ATX ASUS, 2 USB 2.0 Fan 80mm, 4bay, Screw-less design; W-out PS Black-Silver
Power Supply: Sirtec 400W HP-400-A12S
DVD-RW Pioneer DVR-216DBK 20xDVDRW SATA Dual Bare Bulk Black
Memory: A-Data (2x1GB) 2GB-DDR2-800-Vitesta-Extreme-Dual
Motherboard: Gigabyte EG31MF-S2 Intel G31, s.775, LAN, 4xSATA2, 4xDDRII 800, mATX
Intel Core2 Quad Q8200 2,330 GHz FSB1333 4MB QuadCore
HDD WD VelociRaptor SATA-2 300 GB, 2.5" ThermalRadiator 3.5", 10.000rpm, 16MB, Read Seek Time 4.2 ms / Write Seek Time 4.7 ms
```
As you can see, the processor and the HDD are quite powerful and my brother needs to squeeze all the power he can from the two. The server will run Apache (not so used), MySQL (really heavily used) and PHP5 (heavily used) and sshd for file sharing and remote administration.

My question is: are there any tweaks I could do to squeeze more power and to make sure he uses it at its full potential? HDD tweaks especially -- it's going to be under heavy fire :D.

Also, since the server is going to live in our home, we are probably going to use it for file storage, too (backups, music, movies etc.). So, what partitioning scheme do you recommend? I was thinking three partitions: **/**, **/home** and **/mysql**. Now, I'm not sure if a /mysql partition would be efficient but I'm thinking that because MySQL will be bashed a lot a separate partition for it might prove a bit of a performance boost. Also, if the system crashes for some reason, the /mysql partition will hopefully stay more or less intact.

Any other advice would be really nice. Although I've never done a professional server setup before, I have installed Ubuntu + Apache + MySQL + PHP a few times so I sort of know my way around these. I'm not too much of a stranger to command line, either. Basically I'm just going to pop an Ubuntu Server CD in the machine and go from there.

---

### Post by Titan8990 on 2009-02-17
Honestly, if you are trying to squeeze every ounce of power out of your hardware, you want a much smaller kernel than Ubuntu has to offer. Specifically, a kernel you have compiled yourself. 

Often distros that support running on a vanilla kernels are less used as production servers. There is much that can go wrong when most to all configuration is done manually, as well as the long amounts of time needed to setup and maintain them. 


In short you really need to ask yourself some questions:


Is performance more important that stability?

Will it be cost-effective to spend the time to set up a server in gentoo or arch linux given the long time setup and its given performance increases?

Do I need to learn new skills while setting up a server that is going in to production?

---

### Post by HermanAB on 2009-02-17
Spend $50 more on a faster machine and save thousands in configuration and maintenance effort...

Cheers,

Herman

---

### Post by Znupi on 2009-02-17
**HermanAB:** $50? Huh. My brother had to choose between that HDD and one that had 8ms access time (compared to this one's 4ms) and that had 7200rpm (compared to this one's 10,000). The cost difference was $250. That's quite something, the HDD is almost half of the whole machine cost (the HDD alone is about $325). It would be a pitty if he wouldn't get to use the whole potential of the HDD.

**Titan8990:** The machine is not a production server, it's a development server. I don't think I'm going to go as far as installing Archlinux (although I've played with it before, I think I still have a VM around here somewhere...) mainly because I don't have a lot of time on my hands and I don't have a couple or more days just to set it up (I'm hoping I'll be done in a few hours). I would have loved to toy around with it, though, but I think I'm going to go for the huge support and stability Ubuntu offers.

So, any tweaks? Any "edit this file set this hdd parameter and get 0.01ms less access time"? :D Or should I expect Ubuntu to go at full speed straight away?

---

### Post by Titan8990 on 2009-02-17
As a development server, stock ubuntu will be much faster than you will ever need on that hardware.

---

### Post by cariboo on 2009-02-17
Quicker hard  drive access times aren't going to help if you can't get the data to the network, optimize your network connection, because that is the bottle neck. Have a look [here]("http://www.ubuntu-unleashed.com/2008/05/howto-tweak-your-internet-connection.html").

Jim

---

### Post by jimv on 2009-02-17
When you say it's going to be heavily used, what's your definition of that?  What's he doing?

---

### Post by Znupi on 2009-02-18
**cariboo907:** My brother doesn't need it to just serve files really quickly. As I said, MySQL is going to be the one to force the HDD to its limit, so network speed has nothing to do with it.
**jimv:** By heavily used I mean millions of MySQL queries issued one after another (programatically, of course) on tables as large as 2GB+.

From what I've read on the net pretty much the only thing you can do is increase the readahead value using hdparm. Any other suggestions?

Also, what's your take on my partitioning scheme? Do you think a **/mysql** partition would be efficient?

Thanks :)

---

### Post by Mr.Carramba on 2009-02-18
> **Znupi said:**
> **cariboo907:** My brother doesn't need it to just serve files really quickly. As I said, MySQL is going to be the one to force the HDD to its limit, so network speed has nothing to do with it.
**jimv:** By heavily used I mean millions of MySQL queries issued one after another (programatically, of course) on tables as large as 2GB+.

From what I've read on the net pretty much the only thing you can do is increase the readahead value using hdparm. Any other suggestions?

Also, what's your take on my partitioning scheme? Do you think a **/mysql** partition would be efficient?

Thanks :)


if you are going to run huge mysql queries, then the fastest way to have a lot of ram and try to keep mysql in the RAM.
and optimizing mysql would be much more critical then "squeezing" hardware

---

### Post by moberry on 2009-02-18
1. Upgrade the ram to >4gb.
2. Update your PHP database API to cache with memcached.
3. Watch your database load go to nill (if you cache correctly).

As far as your partition scheme, nothing wrong with the default. I don't think you would get much improvement (if any).

---

### Post by Znupi on 2009-02-18
**Mr.Carramba:** We have thought of keeping the huge tables in RAM (temporarily) and writing them to disk when we are finished with them. It's definitely something we will try. Also, optimizing MySQL is indeed a very good idea, but what optimizations would you recommend? Any good resources on this topic?
**moberry:** memcached is only useful when doing lots of identical reading queries. My brother's program that will run on the server does pretty much the opposite, running always-different queries and mostly writing ones, so I don't think memcached would improve performance that much.

As for the partitioning scheme, I think I'm going to keep a separate **/mysql** partition (as long as there's no performance regression) just for the sake of having that partition intact in case of system failure (broken update, outside attack, overload etc.).

Thanks :)

---

### Post by moberry on 2009-02-18
Just because the queries are different every time doesn't the data can't be cached. It all depends on how much you plan on reading back. If you plan to read very little back then no, not a good solution.

Next question would be, if you never plan on reading the data back. What's the point of saving it?

---

### Post by Mr.Carramba on 2009-02-18
> **Znupi said:**
> **Mr.Carramba:** We have thought of keeping the huge tables in RAM (temporarily) and writing them to disk when we are finished with them. It's definitely something we will try. Also, optimizing MySQL is indeed a very good idea, but what optimizations would you recommend? Any good resources on this topic?
**moberry:** memcached is only useful when doing lots of identical reading queries. My brother's program that will run on the server does pretty much the opposite, running always-different queries and mostly writing ones, so I don't think memcached would improve performance that much.

As for the partitioning scheme, I think I'm going to keep a separate **/mysql** partition (as long as there's no performance regression) just for the sake of having that partition intact in case of system failure (broken update, outside attack, overload etc.).

Thanks :)

[http://forums.mysql.com/read.php?10,230413,230416#msg-230416](http://forums.mysql.com/read.php?10,230413,230416#msg-230416)
basically
give more cache to the indexes 
force index loading in memory 
see docs for how-to

---

### Post by Znupi on 2009-02-18
**moberry:** This is not about the project, it's about the server and its configuration. We did look at memcached (thanks for the suggestion) and he decided it is not useful for his application (he worked with other caching systems before).
**Mr.Carramba:** Thanks! :)

---

### Post by songshu on 2009-02-18
as mentioned before, add RAM and as much as you can get in there, it will really increase your mysql performance. it would also help if mysql would have its own harddisk.

second, maybe not needed but its something i personally prefer, you could use something like Vserver to seperate different environments running next to each other without having a setback in performance in virtualisation overhead.

third, i used to tweak the hell out of the kernel when starting with Slackware 6 years ago, but nowadays i just use the stock kernel since the hours and days extra work are simply not worth the extra nano second you gain.

---

### Post by moberry on 2009-02-18
1. Definitely upgrade the ram. 2gb is pretty low for a 2gb+ high performance database. If money is an issue, and you're not doing tons of processing with the data, you could skimp out on the processor some to offset the cost.


2. Look into a performance enhancing data redundancy scheme (raid 10 or 0+1). This will of course provide some security for the data as well as increasing read and write speeds.

---

### Post by Znupi on 2009-02-18
**moberry:**
1. Yes, we will probably upgrade the ram more or less as soon as we get it. RAM is pretty cheap these days, so we can afford both the hefty CPU and another couple of RAM sticks.
2. Thanks for the suggestion, that would be a really good solution. Unfortunately the server is already ordered, but I'm having a gut feeling that even if it wasn't, the raid setup would be too costly.
**songshu:** Thanks, but I want to keep it relatively simple. Virtualising different environments sounds quite complicated and I don't think we're going to need it. And about the kernel, well, you said it yourself, it's not worth it :). On top of that, if I tweak the kernel later repository upgrades may break the whole system, which I would like to avoid.

---

### Post by songshu on 2009-02-18
[QUOTE=
**songshu:** Thanks, but I want to keep it relatively simple. Virtualising different environments sounds quite complicated and I don't think we're going to need it. And about the kernel, well, you said it yourself, it's not worth it :). On top of that, if I tweak the kernel later repository upgrades may break the whole system, which I would like to avoid.[/QUOTE]

The concept of virtualisation is definitely going to take some reading and trying before one can understand how simple it actually is, so just consider it a recommendation.

depending on how mission critical the server is, it does not hurt to optimize the kernel from an educational point of view, so if you have the time to do so i would say go for it, but if you want your life to be simple or do not have the time for failure then don't bother

---

### Post by Mr.Carramba on 2009-02-19
well if you can afford, get an SSD disk for your mysql partition, then it will not run but fly :)

---

### Post by windependence on 2009-02-19
> **Znupi said:**
> **Mr.Carramba:** We have thought of keeping the huge tables in RAM (temporarily) and writing them to disk when we are finished with them. It's definitely something we will try. Also, optimizing MySQL is indeed a very good idea, but what optimizations would you recommend? Any good resources on this topic?
**moberry:** memcached is only useful when doing lots of identical reading queries. My brother's program that will run on the server does pretty much the opposite, running always-different queries and mostly writing ones, so I don't think memcached would improve performance that much.

As for the partitioning scheme, I think I'm going to keep a separate **/mysql** partition (as long as there's no performance regression) just for the sake of having that partition intact in case of system failure (broken update, outside attack, overload etc.).

Thanks :)

Don't take offense to this because it's not meant to be that way but it's pretty obvious you have little experience setting up a hiigh capacity database server which is primarily what you are doing if I read you right. I know it's development, but mostly, you want a high performance MySQL server.

That being said, you're not going to want to hear this, but you should have done your research before you ordered the machine. The three most critical parameters for that kind of database server is disk performance, memory, and CPU, in that order. RAID should have been a must, with as many small drives as possible. More spindles increases throughput exponentially, especially when you are randomly accessing large amounts of data. A single drive, no matter how fast, is just going to suck for this. Secondly, databases are memory hungry, and as was said here, the more of the data you can get into memory, the better. 4 or even 8GB would be better. Memory is cheap right now. And finally, CPU is the absolute least of your worries. A 2 gig dual core would probably be fine here.

I would not create a separate /mysql partition, as this mucks with the locations of files that other applications depend on, and it will be a nightmare for you as you add other applications to the system, trust me. As to losing your data, as I state below, RAID should have been mandatory, and backups are an absolute necessity even of you have a RAID array.

On the OS, if you want as good a performance as you can get from the hardware, then you really should run software compiled on the box such as is done in the BSD operating systems.  Gentoo would be good as well, but BSD has been around since the 60s, is real Unix, and if you compile your MySQL, PHP, and other software specifically on the hardware, you squeeze every last drop out of it.

Basically, you're trying to make chicken salad out of chicken ***** because of your budget constraints. Exactly what kind of development will he be doing on this box? We may be able to offer some suggestions if we knew more about what he will be doing.

-Tim

---

### Post by linux_tech on 2009-02-19
There are some more tips to optimize large queries here-
[http://www.debianadmin.com/top-84-mysql-performance-tips.html](http://www.debianadmin.com/top-84-mysql-performance-tips.html)
[http://www.debuntu.org/2006/07/21/75-how-to-optimize-mysql-response-time](http://www.debuntu.org/2006/07/21/75-how-to-optimize-mysql-response-time)

---

### Post by Znupi on 2009-02-19
> **windependence said:**
> Don't take offense to this because it's not meant to be that way but it's pretty obvious you have little experience setting up a hiigh capacity database server which is primarily what you are doing if I read you right.
None taken. As I said in my first post, I'm quite new to this.
> **windependence said:**
> That being said, you're not going to want to hear this, but you should have done your research before you ordered the machine. The three most critical parameters for that kind of database server is disk performance, memory, and CPU, in that order. RAID should have been a must, with as many small drives as possible. More spindles increases throughput exponentially, especially when you are randomly accessing large amounts of data. A single drive, no matter how fast, is just going to suck for this. Secondly, databases are memory hungry, and as was said here, the more of the data you can get into memory, the better. 4 or even 8GB would be better. Memory is cheap right now. And finally, CPU is the absolute least of your worries. A 2 gig dual core would probably be fine here.
Indeed, RAID would've been a good idea. But considering the fact that he was running this program on a 6-year old 40GB IDE HDD, this is going to be quite an improvement. We're going to do regular backups on our desktops using some cron jobs (I know this isn't quite the best data redundancy system, but it's what we got). It's definitely a plan for the future, though.
> **windependence said:**
> I would not create a separate /mysql partition, as this mucks with the locations of files that other applications depend on, and it will be a nightmare for you as you add other applications to the system, trust me. As to losing your data, as I state below, RAID should have been mandatory, and backups are an absolute necessity even of you have a RAID array.
I don't get this -- isn't mysqld the only program that actually accesses the database files? Don't all client applications connect to the mysql server and issue queries? So, a client application would only have to know the IP and the port of the mysql server, while mysqld does all the lookups and such. Maybe you understood wrong -- I don't want to **install** mysql to a separate partition, I just want to keep the database files on a separate partition and change a few mysql configs to make it look on that partition for data. I've done that before.
> **windependence said:**
> On the OS, if you want as good a performance as you can get from the hardware, then you really should run software compiled on the box such as is done in the BSD operating systems.  Gentoo would be good as well, but BSD has been around since the 60s, is real Unix, and if you compile your MySQL, PHP, and other software specifically on the hardware, you squeeze every last drop out of it.
Gentoo, Archlinux and other hard-to-setup solutions were recommended before. While I am sure that would increase performance, we just don't have the time to do it. Thanks for the suggestion, though. And thanks for telling me that BSD systems are always compiled on the machine they run -- I didn't know that!
> **windependence said:**
> Basically, you're trying to make chicken salad out of chicken ***** because of your budget constraints. Exactly what kind of development will he be doing on this box? We may be able to offer some suggestions if we knew more about what he will be doing.
He has some programs that gather data and create huge relational databases. After he's done with that, he creates some statistics out of those databases and uses them on an actual production server which is hosted elsewhere.

Thanks to everyone for replying here and giving your advice. The server is coming in tonight (hopefully) and I will probably get to hack at it this weekend. I'm pretty excited :D.

---

### Post by JeppeM on 2009-02-20
Hey :)

From reading the post it seems like you have some great things to try out... One thing i would suggest is disabling the atime on the /mysql partition... atime is a small timestamp which is written every time a file is accessed, so you're able to see if it's being used (ie., we clean up our file servers of files which have not been accessed in the last 4 years). It's different from modification time, but often not needed on systems like this... So mount it with noatime and nodiratime - you can read more about the different mount options here: [http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)

Hope this helps, and best of luck with the system!

---

