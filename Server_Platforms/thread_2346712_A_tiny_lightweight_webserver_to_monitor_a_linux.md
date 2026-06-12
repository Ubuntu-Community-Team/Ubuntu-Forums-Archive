---
title: "A tiny lightweight webserver to monitor a linux"
date: 2016-12-17
forum: Server Platforms
---

### Post by cazz on 2016-12-17
Hi
I have a apache2 server on one of my Linux that I run Linfo on that make me monitor how the server feeling.
I have notice that is other scriptsystem that I can use but I wonder if that is any that can run on a lightweight webserver.

I have another Linux that is not so powerfull that I think is a waste to run a powerfull webserver as Apache2

Does anyone know any very lightweight webserver that you know that can run a free monitor system and make it works?

---

### Post by TheFu on 2016-12-17
No need to run a webserver to monitor server performance.  System monitoring is something everyone with a server should do and there are 20-50 tools for this. I use a central reporting server that every other server sends monitoring data at every other minute.  Munin is the name. It is pretty lite, but there are prettier options like Cacti.  Only the reporting server runs a web server.  There's also sysusage as a monitoring tool.  You can google for the 20-50 others.

Free? Is that really a question?  In 20 yrs, I recall paying for Linux software once.  It just isn't really part of the culture until you get into fairly large-scale enterprise software.  Even most of that is F/LOSS.

Apache is "everything and the kitchen sink" if you load everything into it.  Most people don't load all the addons/modules, so it isn't THAT bad. There are 20 other web servers, depending on your need.  We've been using nginx for about a decade now, but there are lighter options.  Going lighter means having limitations on some capabilities. That may or may not matter. Just depends on the requirements.  I've seen a web server written in about 120 lines of Perl.  Light enough?

---

### Post by cazz on 2016-12-17
Thanks for the replay

And first I have to say when I ask about free software I just do it automatic, I can't help it :)

hmm yes I have use Cacti before when I monitor the switch at my work.
I have never Think about it can monitor Linux but also Windows computers.

hmm yes I like that idea alot, one system to monitor all my servers I have at home (Have both Linux and Windows servers)

Cacti I have work Before but was not so always easy to understand :)
I have never heard about Munin

I maybe have to install a viritual server of Xubuntu with Apache2 to try the software.

I know it is alot to pick from but I like to have one that is easy to understand and use and it is very important that is easy to install.

---

### Post by TheFu on 2016-12-17
cacti is complex. Munin can be, depends on your skill level how "easy" anything is. Right?

Don't know anything about Windows. Sorry. You didn't mention it in the OP.  I forget that some people still run other OSes.

---

### Post by cazz on 2016-12-17
is ok, I Think I try to install cacti first and then see if I can get it to work as I want it work.
if not I can try Munin


lol I run alot of OS, always fun to try new stuff

---

### Post by TheFu on 2016-12-17
When I was younger, I ran lots and lots of OSes. Over the years, I've been an admin for 20+ different OSes and used over 40. These days, I don't have to deal with OSes that aren't interesting to me anymore.  Even other Unix-like OSes don't interest me anymore and I was an AIX/Solaris/HP-UX/Irix/OSF/SunOS admin for a long time.  Even ran Netware.

These days, Linux and BSD are my preferred platforms.

---

### Post by cazz on 2016-12-17
Ohh netware was fun, special DOS version it was fun.

But right now I work most with Linux, Windows, OSX and of course ios and Android

---

### Post by cariboo on 2016-12-17
Moved to server platforms.

---

### Post by Habitual on 2016-12-18
I found glances recently. Neat, old school program.
Not apache-specific, but still informational and certainly low-overhead.

---

### Post by ian-weisser on 2016-12-18
You can use ssh instead of a webserver. For example, plain old 'htop' other simple tools are highly customizable, and suck up very little CPU if you decrease the refresh rate.

---

