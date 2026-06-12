---
title: "Ubuntu 5.10 Server Performance"
date: 2006-05-07
forum: Server Platforms
---

### Post by gymsmoke on 2006-05-07
I've got Ubuntu 5.10 server running (NO GUI).  It's currently running ssh, proftp, mysql 4, apache 2, php5, qmail/vpop, spamassassin, qmail-scan, clam, and iptables.

It seems to be running somewhat sluggishly.

I'd like to look into a little performance tuning.

Does anyone here have some suggestions as to where you start ?

Thanks for the input.

---

### Post by Kurt` on 2006-05-08
What processes are hogging CPU/memory/disk time? Does `top` show anything relevant? Are you running any sort of graphical stats package (such as Munin) to assist in debugging?

---

### Post by gymsmoke on 2006-05-10
Kurt~
I'm currently running 5.10 Server (no GUI), proftpd, bind9, apache2, mysql-server 4, php5, ssh, qmail/vpop.  No other apps are installed.

---

### Post by soce_32 on 2006-05-11
What kind of hardware are you using?  MySQL, SpamAssassin, and clam can be resource hungry depending upon the mail and web traffic you are handling.  As Kurt suggested, run top and watch it in a console while you do the web app or mail process that makes you think that performance is sluggish.  You should see a process jump to the top while the computer is chugging away.  With this many services on one box, you may be I/O or memory bound at points.  The top process will show lots of swap being used if you are memory bound, and lots of I/O wait if you are slow there.  One solution would be to move some of the services to another server if it is a production situation.

---

### Post by nihilocrat on 2006-05-11
[QUOTE=gymsmoke]I've got Ubuntu 5.10 server running (NO GUI).  It's currently running ssh, proftp, mysql 4, apache 2, php5, qmail/vpop, spamassassin, qmail-scan, clam, and iptables.

It seems to be running somewhat sluggishly.

I'd like to look into a little performance tuning.

Does anyone here have some suggestions as to where you start ?

Thanks for the input.[/QUOTE]

Another thing you could do is make a set of webpages and run ab2 on them.

Have one webpage which is just a bunch of html. No PHP, nothing special.
Have another webpage which has some possibly complicated PHP code but no calls to access the MySQL database.
Have another one which involves PHP and calls to MySQL. Your average open source CMS (drupal, joomla, etc.) will do the trick.

Run ab2 on each of these pages (look at its manpage or on stuff on the net for how to configure the benchmark) and pay attention to failed requests and how many pages it's serving a second. You might also want to run a benchmark for a significant amount of time and look at top to see how much load each process (apache, php, mysql, anything else) is putting on the server.

Also, I'm very surprised someone didn't see 'php' and immediately think **INSTALL A PHP ACCELERATOR** like eAccelerator. It will DRASTICALLY increase performace of any PHP apps, but keep in mind that it's a big memory hog (but you can modify the amount it uses) because all it really does is cache frequently-used php scripts. There aren't any packages for it, but you can get the source off of their site, install the php5-dev package, and follow the instructions they have to compile and install the module yourself. You'll need to be careful, though, that if you ever upgrade php5 you also recompile the module.... that bit me in the *** one time and caused several hours of downtime for my Moodle install when I was frantically trying to figure out what the hell went wrong.

Finally, looking at your crontab to see if there are any unneccessary scheduled processes would probably be good. I occasionally get lots of CPU eaten up by some dumb process I never knew existed running for several minutes. If you can't remove them, just reschedule them for some time like 5 in the morning.

Hope all this helps. If you can't tell, I've already done some research into speeding up my server when I was having performance issues a few months ago.

---

### Post by gymsmoke on 2006-05-15
All great information!  Thanks.  I'm looking into the excellerator, and I'm monitoring processes.  I did notice that Ubuntu likes installing raid processes without being asked.  I don't think that they use much process space, but I also know I didn't ask for it, either,  If Ubuntu uses those processes by default, that's fine.  I'll also check cron to see what's being scheduled.

---

### Post by linuxone on 2006-05-15
Hi,

[QUOTE=gymsmoke]I've got Ubuntu 5.10 server running (NO GUI).  It's currently running ssh, proftp, mysql 4, apache 2, php5, qmail/vpop, spamassassin, qmail-scan, clam, and iptables.[/QUOTE]

same here, except spamassassin and clam, but with some additional software like mod-security (apache2), Kaspersky Antivirus for qmail, sqwebmail, qmailadmin and the original ZendOptimizer 3.00 for PHP speedup.

I installed **netqmail-1.05** from sources instead of the precompiled qmail package. Very important is the qmail installation by using **softlimit** and **tcpserver** (from daemontools and ucsp-tcp tools). softlimit can limit the memory usage of qmail. See the great [life with qmail](http://www.lifewithqmail.org/) docs.

But I run ~100 domains (http, https, smtp, pop3, ftp) on a single machine **without problems**. (except the very specific apache2 problem, see some topics below)

Thomas

---

