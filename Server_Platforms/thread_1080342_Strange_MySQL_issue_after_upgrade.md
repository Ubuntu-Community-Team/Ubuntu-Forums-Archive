---
title: "Strange MySQL issue after upgrade"
date: 2009-02-25
forum: Server Platforms
---

### Post by lykwydchykyn on 2009-02-25
Let me preface this by saying this involves a Debian server, and I posted this at Debian-Administration.org, but I wanted this forum's take on it as well.
> 
I'm stumped.

Let me lay out the situation.  I have a legacy app written in gtksharp that communicates directly to a mysql server.  The users of the app are all on subnet A.  The server is on subnet B.  Most users are running this app in windows xp, but I run it in Ubuntu intrepid and another person runs it on Ubuntu Hardy.

After upgrading the server (Dell 2950) to Lenny and MySQL 5.051a, the program is unusably slow.  When I say "slow", I don't mean "a little sluggish", I mean it takes literally 10 minutes for the program to load up, and 2-3 minutes to do even the smallest things in it.  For all practical purposes it doesn't work.

However, I soon discovered that not everyone had this problem.  So let me lay out the facts in this case as I have discovered them.
 - It is slow on my computer, running Ubuntu Intrepid
 - It is not slow on the Hardy heron computer
 - Downgrading to the hardy version of mono/gtksharp did not fix it on my computer.
 - It is slow on Windows XP running in virtualbox on my computer, running the exact same version of mono as the other (non-virtual) Windows XP boxes on Subnet A.
 - It is slow on fresh installs of  Lenny or Intrepid on subnet A.
 - It is not slow on Lenny boxes on subnet B (can't put an intrepid box on subnet B).
 - It is not slow on my Intrepid box if I change to a test server on Subnet A also running Lenny and MySQL 5.051a with the same data dumped in.
 - It is not slow when a Lenny box on Subnet B is using the test server on Subnet A.

I have checked syslog, the mysql logs, and dmesg, but I don't see anything different being logged when a slow machine connects.  I have run a packet sniffer on the server, and haven't seen any different traffic when a slow machine connects.  I've run a program trace on the client app, and while I noticed a lot of socket exceptions being thrown, it was that way on the ones working correctly as well.

I don't realistically expect anyone to have an idea of how to fix this, but if you have any thoughts on the next thing to investigate, I'm all ears.


Any thoughts here?  Thanks for reading.

BTW, the original post is here: [http://www.debian-administration.org/users/lykwydchykyn/weblog/18](http://www.debian-administration.org/users/lykwydchykyn/weblog/18)
I've been adding more information about the problem if anyone wants to help.

---

### Post by lykwydchykyn on 2009-02-25
The folks at debian-administration got me fixed up.  Apparently mysql will try to resolve the dns names of clients unless you explicitly tell it not to. 

So for whatever reason clients without DNS lookup info were experiencing the delay, and the others were fine.

I'm guessing this will speed up everyone now.

Just in case anyone ever has a similar issue.

---

