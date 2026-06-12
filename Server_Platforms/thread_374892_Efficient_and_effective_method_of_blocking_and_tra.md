---
title: "Efficient and effective method of blocking and trapping spam bots"
date: 2007-03-03
forum: Server Platforms
---

### Post by mikestefff on 2007-03-03
Does anyone know of an efficient and effective method to ban spam bots on apache2? I read about a few simple methods that entail making directories that robots.txt ban so that anyone who accesses them has to be a bad bot. the directory then contains a php files which logs the IP and every regular php page that loads first checks the IP list to see if the user is allowed on the site etc. ( [http://linux.oldcrank.com/tips/antibot/]("http://linux.oldcrank.com/tips/antibot/") )

The problem with this is that 1) the IPs do not clear themselves after a certain amount of time and 2) looping through a IP list before every page load will consume resources and 3) the bad Ips arent actually blocked from the server, they are just referred..

I read about an article which used mysql and a daemon but I do not think it was for apache2..
[http://www.rubyrobot.org/article/protect-your-web-server-from-spambots]("http://www.rubyrobot.org/article/protect-your-web-server-from-spambots")

What do you suggest the best method is - anything I don't know about..anything at all??

THANKS

---

### Post by kidders on 2007-03-03
Hi there,

This method is reasonably effective. I use a similar method myself, where a PHP script automatically creates iptables rules to drop all incoming packets from offending IPs. Iterating over a list of banned IPs at every request isn't terribly labour-intensive, but using iptables would remove the need for it anyway. **Edit:** I would take the opposite approach, in fact, and check IPs to be blocked against a whitelist of previous legitimate users, before actually dropping any packets. This would reduce the probability of banning real people, which is important, because your server would appear to them to have gone offline.

Blocking the bot for a few hours should be enough, so you could, if you wanted, write a cron script to delete the firewall rules again, after a while.

All these "low tech" approaches rely on the idea that most bots tend to be a bit flaky with the standards. Any opportunity you can find to check whether a remote host is violating protocol specifications is worth consideration, because the traps are so easy to implement.

---

