---
title: "Setting up a query server"
date: 2012-09-21
forum: Server Platforms
---

### Post by ki4jgt on 2012-09-21
A company I'm working for has asked me to design a query based website. I need to allow member registrations and return query strings based on ?query=search+term

I know basic PHP concepts so this should be no problem in and of itself. The problem arises when I bring in advanced hosting problems and circumstances. Such as the fact that at any given time, I will need to perform roughly around 500 - 1000 query searches every minute (It's a communication company and the queries help make the connections). In the words of my employer "I want something which can compete with Skype." The bandwidth for the actual communications has been taken care of, but the requirements for the queries are a little shaky at the moment. Basically I need a website which allows users to register a username, password, address, payment information, nickname, and serial number for the site. The site when addressed as [http://url.com/?query=Username](http://url.com/?query=Username) will return a single string containing the serial number. This will tell the person calling the direct routing number to the person receiving the call (it's a VERY weird concept). For every call, text, file, video, whatnot, the server will be queried. Basically it's a type of DNS idea.

My problems:
- What would be the best setup for a server like this?
- How would I backup the database to keep it from going bad?
- What would be the best server to use? At current, the budget is limited but the only thing we need now are the query servers. Everything else has been taken care of. I thought about stringing a few Raspberry Pis together (256Mb RAM with ARM processors, they're $35) with external USB harddrives.

---

### Post by koenn on 2012-09-23
this is the sort of thing LAMP was made for :
a webserver (apache), a database  with good read performance (mysql) and a web-friendly scripting language (php) on a linux box.

the rest is just a simple matter of creating a database and writing the php and the relevant queries, preferably in a secure manner. 

performancewise, i don't think 15 requests/queries per second is all that much. but to make sure, you can probably test it by setting up the simpliest configuration that would work, and running an awful lot of wget statements against it to see how it copes. 

otoh, i think for something like this  I'd be looking at a cheap server rather than a handful of Raspberry Pis. External USB drives sounds scary.
Think something like HP Proliant Microserver - it's marketed as "server hardware for the stuff you used to put on a dedicated PC". 

And if you're entire business is gonna depend on the availability of this system, you might want two.

---

### Post by ki4jgt on 2012-09-23
> **koenn said:**
> this is the sort of thing LAMP was made for :
a webserver (apache), a database  with good read performance (mysql) and a web-friendly scripting language (php) on a linux box.

the rest is just a simple matter of creating a database and writing the php and the relevant queries, preferably in a secure manner. 

performancewise, i don't think 15 requests/queries per second is all that much. but to make sure, you can probably test it by setting up the simpliest configuration that would work, and running an awful lot of wget statements against it to see how it copes. 

otoh, i think for something like this  I'd be looking at a cheap server rather than a handful of Raspberry Pis. External USB drives sounds scary.
Think something like HP Proliant Microserver - it's marketed as "server hardware for the stuff you used to put on a dedicated PC". 

And if you're entire business is gonna depend on the availability of this system, you might want two.

Thanks for this intel. :) How would I go about load balancing them (if I go with two) and what is the best method for mysql backups of this size?

---

### Post by koenn on 2012-09-23
I wasn't thinking about load balancing - it was just a general remark that if your entire business communication depends on 1 server, and it breaks, you're out of business. So you'd want at least a cold standby, i.e. machine that is close enough in config and data that it can be put into action as a replacement within a very short time if something bad happens with your main server. It would only need to take you through the time it takes to get your primary system up and running again so anything that can run apache and mysql would probably do. 

mysqldump is the most common database backup tool and probably do just fine (test it). The only issue is the time it takes to backup and restore, and that depends on the size of your database. 


If you want to go  high availability you'd be looking at keeping 2 machines in sync and (preferably transparently) switch from one to the other if one fails. That's more complicated, and I don't think there are paint-by-numbers solutions for that. The tools are there, but you'll have to work out a solution yourself, suited for your needs/goals. 
In such a scenario, you're not looking for a mysql backup, but a synchronization/replication mechanism. I think that exists, but I've never done it.
You might still want mysqldump backups in case your database goes bad and the problem is replicated to your second system.


Once you go the two identical machines route, you may also want load balancing, but that's probably just nice to have, if you can combine it with fail-over without complicating things too much. 
If you *need* load balancing to cope with demand, it means that in case of a failure of 1 machine (out of 2) you fall back to +/- half the performance your users expect. It's up to you (or your boss) to decide whether that is acceptable.

Ah, the joys of system administration ..

---

### Post by JKyleOKC on 2012-09-23
And once you've configured the hardware, be sure that you are completely familiar with the entire subject of "SQL Injection" which is probably the single largest cause of security breaches in SQL databases. The general idea is that when you ask the user to provide a query request, a baddie can include a single common character in his response, followed by SQL commands, and do his will with the server. It's fairly easy to defend against, but to do so you absolutely have to know and fully comprehend exactly how and why it works -- which many so-called professional DBAs apparently do not.

Just Google for "SQL Injection" to get a start on it...

---

### Post by ki4jgt on 2012-09-23
> **JKyleOKC said:**
> And once you've configured the hardware, be sure that you are completely familiar with the entire subject of "SQL Injection" which is probably the single largest cause of security breaches in SQL databases. The general idea is that when you ask the user to provide a query request, a baddie can include a single common character in his response, followed by SQL commands, and do his will with the server. It's fairly easy to defend against, but to do so you absolutely have to know and fully comprehend exactly how and why it works -- which many so-called professional DBAs apparently do not.

Just Google for "SQL Injection" to get a start on it...

LOL, time to create my own database :(

---

### Post by SeijiSensei on 2012-09-26
You'll also need to become familiar with "cookies" and "sessions."  Take this site, for instance.  When you log in, the server sends a cookie to the browser that it uses on subsequent page requests to know you are an authenticated user.  You'll probably want to set the expiration date on these cookies to a fairly short period so that a login today won't carry over to tomorrow.  You'll need to read up on the session handling functions in PHP.  

If you're talking about handling 1,000 queries per minute, I'd guess you need a heftier machine with a RAID array of 7200 RPM drives on which to install the SQL server.  It sounds to me like the biggest performance issue will be querying the database, which means the task is heavily I/O bound.

---

### Post by lykwydchykyn on 2012-09-26
If you write this in PHP, use PDO and prepared statements rather than the venerable "mysql_*" commands, and it should mitigate the risk of SQL injection.

---

### Post by koenn on 2012-09-26
> **SeijiSensei said:**
> 
If you're talking about handling 1,000 queries per minute, I'd guess you need a heftier machine with a RAID array of 7200 RPM drives on which to install the SQL server.  It sounds to me like the biggest performance issue will be querying the database, which means the task is heavily I/O bound.

1000 queries a minute, or 17 per second, is not that much.

To get a ballpark figure, I ran 1000 queries against a database on an P4 PC with IDE disks. it took 15 seconds, so ~4000 per minute.

These were simple queries against a very small table (if that matters), but still. 

Nonetheless, RAID's a good idea, if only to protect against hardware failure.

---

### Post by SeijiSensei on 2012-09-26
I just didn't think a Raspberry Pi would be sufficient, especially with only 256M of memory.  There wouldn't be much memory left over to cache disk I/O.

---

