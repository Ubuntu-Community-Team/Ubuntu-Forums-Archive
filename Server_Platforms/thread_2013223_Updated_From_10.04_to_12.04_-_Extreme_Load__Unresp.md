---
title: "Updated From 10.04 to 12.04 - Extreme Load / Unresponsive Server"
date: 2012-06-30
forum: Server Platforms
---

### Post by bsntech on 2012-06-30
Hello all,

Not sure if anyone can help with this issue or not.

A week ago, I upgraded two servers from Ubuntu 10.04 Server to 12.04 Server (64-bit).

One server (a home-built one) is working flawlessly with no problems.

However, another one - an HP ProLiant DL380 G4, is having major issues.  Server has two dual-core 3.4 GHz processors with 4 GB of memory.

I have a graphing system (Cacti) that graphs certain aspects of the servers for monitoring purposes.  One of those graphs is Load Average.

On the HP server, I have been noticing that the load average will shoot way up (400+) and then the graphing stops.  The server then becomes unresponsive and I'm unable to even ssh into it.  It still responds to ping requests, however.

I even went as far as to setup a cron job every five minutes that would e-mail me the results of top - so I could see what is potentially going on.  Well, that didn't work.  An example is at 4:35 am this morning, the load jumped from 0 to about 500 - and that is when the graph stopped at about 5:50 am this morning.  it is a constant straight line.  It is almost as though there is some kind of program that is looping over and over and never stops.

Unfortunately, this server is remote - so the only access I have to it is through ssh - and when I can't ssh into it, I'm not able to see what is going on.

Definitely a tough one - and wanted to know if anyone had any kind of advice.  I have checked the syslog after a reboot and the logs stopped right at 4:35 am.  There at least should have been some kind of log for the SNMP connection to get the load data between 4:35 am and 5:50 am (when the graph stopped), but that didn't even show up.

I've went as far as shutting off some services - but the issue seems to be completely random so it is very hard to troubleshoot and find the root cause when I don't have direct access to the server.

Any help is appreciated!

---

### Post by bsntech on 2012-07-01
I'm not sure if this was the cause or not, but I noticed one of the other servers spiked from 0.5 up to about 10 for several hours yesterday - and still was that high this morning.

I found out (at least I could ssh into that server) that the mysqld service was using 99% of the processor.  Apparently the 3.3.x kernel had a 'leap second' bug in it causing a race condition.

Upgrading the servers to that - and also ran the quick-fix for the update - and that immediately brought the load and CPU usage down.

I've already downgraded back to 10.04 on the other server that was having the issue all week - but I'll do another backup and then upgrade it again to 12.04 to see if that was also the issue.

---

### Post by yedidel on 2012-07-01
I have the exact same problem on my HP Proliant G7 server, started yesterday. How did you solve it? apt-get upgrade?

---

### Post by bsntech on 2012-07-21
I've not solved the problem myself.  I don't think that 'leap second' was the cause of it as several other Ubuntu computers only had high load that one day.

I am actually upgrading one of the ProLiant servers back to 12.04 again today.  I had to revert the server back to 11.04 when I couldn't find a solution (thank goodness I make backups!).

---

### Post by bsntech on 2012-07-23
Well, the server upgrade went fine.  This  morning, the load began exponentially increasing and died.  So that server was reverted back to Ubuntu 10.04 this morning.

While this can't be exactly discovered since the server is remote, I tried to make an SSH connection to it this morning - and it sat there and never would prompt for username/password.  That is the same time I saw the graph jump up to a 20+ load.  May have just been the luck of the draw that an SSH connection was attempted at the same time.

No idea what the problem is - but it looks like I'll be keeping those two HP ProLiant DL380 G4 servers on Ubuntu 10.04.

---

### Post by bsntech on 2012-12-06
Bringing up this old thread again.

I just upgraded one of the servers to 12.04.1 last night and the same thing is still happening.  Load went way off the charts to 400+ before my Cacti graph completely stopped.

Certainly was hoping that if there was a bug or something in a kernel or another piece of software between June and now - that it may have been corrected.

This server is a remote server and when it crashes, the only way I can get into it is through the out-of-band management controller - and I can only do a restart and that is all.

Strange thing is - some of the services still seem to be responding to an extent - like Cacti still graphing CPU usage.

At this point, I'm stuck as well because the other servers were updated over the weekend and it picked up MySQL 5.5.x.  The HP servers run MySQL 5.1.x and so now they will not work in a master-master replication mode due to architecture changes.

---

### Post by bsntech on 2012-12-06
Just restarted the server again and ucommented the lines in the .bash_profile that started the X Windows Session automatically.  I don't think it is the cause, but I'm out of ideas on what to try.

All public traffic has been diverted away from the server to reduce load - although it still does replicate SQL and data with the other mirror.

It is hitting some kind of race condition that doesn't seem to affect processor usage (according to the graphs anyway).

---

### Post by bsntech on 2012-12-07
Over the past two days, the server seems to be going into high load mode starting at around 12:30 AM in the morning - and it steps up by a load of 10 every five minutes.  The graph then seems to stop when the load hits close to 400.

The odd thing - DNS still works.  I can query records from the DNS server remotely.

I tried to do a:

top -n 1 > top.txt

In a SSH session that I left open throughout the day.  The words do show up - but it then just sits there.  That is expected with a load of 400+.  But if I try to establish a new SSH session, the session cannot be established.

Extremely odd behavior and this does indicate that X Windows doesn't have anything to do with it.  No idea what the root cause is since I cannot get "top" to return anything to me.  Even if it does, I doubt it will be of any use.

---

### Post by bsntech on 2012-12-07
I posted the question over at serverfault and a guy replied pretty quickly.  He believed the problem to be an I/O error since the server could still respond to network pings and was responding to DNS queries.  He mentioned that anything cached in RAM probably was working - although any I/O to the disk wouldn't work.

That pretty much hit it spot on for the most part.

There is a firmware update to the SmartArray 6i in the HP ProLiant DL380 G4 servers that was needed to be ran.  I installed the firmware update and we'll see what happens.

Also, I noticed by doing a "modinfo cciss" on Ubuntu 12.04, the cciss driver is now 3.6.26.  In Ubuntu 10.04, the driver was 3.6.20.

---

### Post by bsntech on 2012-12-10
Issue seems resolved now.  Updating the firmware of the SmartArray 6i on the servers have had good results for the past couple of days.  No lock-ups or large loads causing the server to hang.

---

