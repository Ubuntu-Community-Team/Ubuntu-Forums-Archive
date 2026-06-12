---
title: "Nginx + php5-fpm performance issues"
date: 2012-11-13
forum: Server Platforms
---

### Post by particle64 on 2012-11-13
Hi everyone,

I am running a high traffic site with some friends and recently we switched from Apache to Nginx. We're having huge performance issues since then. When we hit about 300 visitors the site starts to load very slow. It can take about 10+ seconds for a page to load.

It only seems to be pages with PHP that loads slowly. We don't have the same issues on pages with pure HTML.

The php5-fpm.log is filled with error messages like this:

[13-Nov-2012 20:33:53] WARNING: [pool www] seems busy (you may need to increase pm.start_servers, or pm.min/max_spare_servers), spawning 16 children, there are 0 idle, and 68 total children
[13-Nov-2012 20:33:54] WARNING: [pool www] server reached pm.max_children setting (70), consider raising it

We've tried to increase those values a lot, but that didn't do the trick.

Here's how our Nginx conf-file looks like for the moment:
[http://pastie.org/private/z34p8ptvbvx0ss0yaxoa](http://pastie.org/private/z34p8ptvbvx0ss0yaxoa)

Here's how our php5-fpm pool conf looks like:
[http://pastie.org/private/egidjh4v7is492zoqr1g1w](http://pastie.org/private/egidjh4v7is492zoqr1g1w)

Any help with this would really be appreciated!

---

### Post by star3am on 2012-11-14
Hello 

I had the same problem, and my config is mostly the same as yours. 

I just tested with siege and changing

pm = dynamic 

to

pm = static

seems to have fixed it. 

The image below, first spike, php5-fpm hanged with 502 gateway timeout, the second spike the process recovered.

[IMG]http://www.3am.co.za/php5-fpm.png[/IMG]

Hope this helps you too.

Riaan

---

### Post by particle64 on 2012-11-19
Thanks a lot for the tip! Changed to static and reduced the number of childrens a bit and voila! Huge difference! :)

Will try to tweak it even more, but the site's load time is more than acceptabel now during high load.

---

### Post by jaypabs on 2013-07-01
> **star3am said:**
> Hello 

I had the same problem, and my config is mostly the same as yours. 

I just tested with siege and changing

pm = dynamic 

to

pm = static

seems to have fixed it. 

The image below, first spike, php5-fpm hanged with 502 gateway timeout, the second spike the process recovered.

[IMG]http://www.3am.co.za/php5-fpm.png[/IMG]

Hope this helps you too.

Riaan

Currently I am using dynamic instead of static. I have the following server:

> 
Intel® Xeon® E3-1270 v2 Single Processor - Quad Core Dedicated Server
CPU Speed: 4 x 3.5 Ghz w/ 8MB Smart Cache
Motherboard: SuperMicro X9SCM-F
Total Cores: 4 Cores + 8 Threads
RAM: 32 GB DDR3 1333 ECC
Hard Drive: 120GB
Smart Cache: 8MB


And my nginx settings:

> 
PHP-FPM pm.max_children = 20
PHP-FPM pm.start_servers = 7
PHP-FPM pm.min_spare_servers = 4
PHP-FPM pm.max_spare_servers = 10
PHP-FPM pm.max_requests = 500


Is this settings good?

BTW, what benefit there is for a static vs dynamic?

---

### Post by sandyd on 2013-07-01
> **jaypabs said:**
> Currently I am using dynamic instead of static. I have the following server:



And my nginx settings:



Is this settings good?

BTW, what benefit there is for a static vs dynamic?

Depends on what you are running really,

Dynamic:
The amount of processes that are spawned are adjusted on the fly (spawning more as load gets higher).
There is a "minimum" version of php-fpm processes, as a maximum of php-fpm processes when php-fpm is idle. The processes take a bit of time to spawn, so some people think that Dynamic is a bit slower under variable load.

Static:
The amount of process that are spawned are set in the configuration.

---

