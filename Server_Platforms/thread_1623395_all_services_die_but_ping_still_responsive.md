---
title: "all services die but ping still responsive"
date: 2010-11-16
forum: Server Platforms
---

### Post by Jguy on 2010-11-16
Hello,

I'm having an interesting problem with one of the 10.04 ubuntu servers I administrate.

For starters, this system is in a VPS. It has I believe now 1 GB of RAM and 1.5GB of swap available to it.

the services we're running on it are;

apache2
nrpe through xinetd (part of remote monitoring for nagios)
openvpn
openssl

As part of apache2, the system has the following software it hosts through http:

IPB 3.0.x
Drupal (ver. unknown at this time)
ubercart (ver. unknown at this time)
mediawiki (ver. unknown at this time)
bugzilla (latest stable version, 3.6.3) 

At random times, sometimes within hours, sometimes it goes days, the system will become unresponsive and socket timeout all of its services but still respond to ping. 

Here is what nagios sees and I can confirm: [[IMG]http://img413.imageshack.us/img413/8885/nagios.th.png[/IMG]](http://img413.imageshack.us/i/nagios.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

I can ping the machine in question, but nothing else will respond. the only thing we can do is reboot it and everything is restored. 

the datacenter where the VPS is located at reports that not much else is hosted virtual wise on the machine which this VPS is located, so we can almost rule out that there is a struggle for resources on the host machine..

I believe that the swap usage I last recorded before the box went down this time has something to do with it, as it's been sitting in the high 90% free range, but before it went down, the swap usage was up to ~75% free before everything became unresponsive. 

Does anyone have any ideas as to what might be causing this? I am puzzled. Could it be a memory leak?

Please let me know your thoughts.

---

### Post by galvatron408 on 2010-11-19
I would take a look at /var/log/messages to see if anything shows up there. I would also console on to the server when the network services appear to die so I can see if there is any message on the console.


If no messages appear, I would just replace the machine or run some hardware diagnostics with the manufacture's CD (that is if your manufacture gave you one). I've seen bad memory, bad cpu's, bad motherboards, bad drives do the weirdest things.

---

### Post by Jguy on 2010-12-15
Hi, thanks for the response.

The last time I consoled to the VPS, this was in the console:

[505667.755652] Out of memory: kill process 15575 (apache2) score 77029 or a child
[505667.755667] Killed process 15575 (apache2) vsz:308116kB, anon-rss:8568kB, file-rss:60kB 
[505687.233153] Out of memory: kill process 15573 (apache2) score 77028 or a child      
[505687.233163] Killed process 15573 (apache2) vsz:308112kB, anon-rss:20612kB, file-rss:292kB 
[505687.298956] Out of memory: kill process 15599 (apache2) score 76735 or a child   
[505687.298980] Killed process 15599 (apache2) vsz:306940kB, anon-rss:46432kB, file-rss:80kB    
[505742.637102] Out of memory: kill process 15506 (apache2) score 76700 or a child         
[505742.637117] Killed process 15506 (apache2) vsz:306800kB, anon-rss:11972kB, file-rss:68kB  
[505756.811190] Out of memory: kill process 15595 (apache2) score 76575 or a child                                       [505756.811202] Killed process 15595 (apache2) vsz:306300kB, anon-rss:36636kB, file-rss:68kB     
[505789.954908] Out of memory: kill process 15565 (apache2) score 76442 or a child          
[505789.954918] Killed process 15565 (apache2) vsz:305768kB, anon-rss:13060kB, file-rss:68kB

This doesn't mean that apache2 is causing the problem, I would think, it's just what the memory manager decided to get rid of...

We have a log file that is generated every 5 minutes that shows us the top processes in memory and the total memory free and swap free, but that doesn't give us any real indication as to what might be going on.

Do you think moving to apache-mpm-worker mnight solve the problem, or at least help?

---

### Post by robert_pectol on 2010-12-15
Some process is probably exhausting your RAM as evidenced by the fact that the system goes into protective mode and starts killing off processes in order to maintain enough RAM for essential OS function.  It's also evidenced by the fact that your swap usage climbs just before the problem exhibits itself.  It would be interesting to see what processes are eating up your RAM, specifically which one(s) who's memory footprint steadily increases over time (use top).  If you find that's what is happening, then the process in question probably has a memory leak.

---

### Post by Jguy on 2010-12-16
Well, we actually think we've narrowed it down to a MySQL problem, I never would have thought to look at our database server being the cause. I guess apache just kept too many SQL threads open, so we've since adjusted some of our SQL settings and things went immediately stable after restarting SQL to reload the changes, all the apache processes just died that were waiting on SQL processes and the apache processes that were active just took off and loaded pages. Tt hasn't acted up in about 4 days and our website is under high load with no load issues, so we're knocking on wood and crossing our fingers we finally solved it for good.

Thanks again.

---

### Post by HugoSerrano on 2010-12-17
Hi!
Get some graphs one your nagios system! Will help you to check your system behavior over the time.

sudo apt-get install nagiosgrapher

Regards!

---

