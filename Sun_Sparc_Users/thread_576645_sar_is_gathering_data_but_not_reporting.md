---
title: "sar is gathering data but not reporting"
date: 2007-10-15
forum: Sun Sparc Users
---

### Post by RobSand on 2007-10-15
I am running Solaris 10 in a sparc environment.

I have the sys crontab to setup to use sar to gather data and report it.
My sys crontab entry looks like this:

0,5,10,15,20,25,30,35,40,45,50,55 * * * 0-6 /usr/lib/sa/sa1
20,40 8-17 * * 1-5 /usr/lib/sa/sa1
5 18 * * 1-5 /usr/lib/sa/sa2 -s 8:00 -e 18:01 -i 1200 -A

I can manually run the sar command and it will report sar data to the screen: i.e. if I run   sar 1 10  it will report, to the screen, 10 instances every one second

However, whenever I depend on the cron job to run sar and report back the statistics in the /var/adm/saXX files, it will not report.

If I run the sar command by itself, I get the message:
sar: can't open /var/adm/sa/sa19

My question is this, why is the cron job not saving the data in the
/var/adm/saXX file?

On a server in which sar is reporting correctly, I can run the sar command (no arguments or switches) by itself and it will correctly report as follows:

SunOS cl1eriaps04 5.10 Generic_125100-08 sun4v    10/15/2007

00:00:00    %usr    %sys    %wio   %idle
00:05:00       0       0       0     100
00:10:00       0       0       0     100
00:15:01       0       0       0     100
00:20:00       0       0       0     100
00:25:00       0       0       0     100
00:30:00       0       0       0     100
00:35:00       0       0       0     100
00:40:01       0       0       0     100
00:45:00       0       0       0     100

---

### Post by RobSand on 2007-10-15
Just FYI...I solved the problem.  Seems as though I did not stop/start the cron service daemon after modifying the cron file to enable sar.  Running the following command fixed my problem:

svcadm restart svc:/system/cron:default

---

### Post by netztier on 2007-10-15
> **RobSand said:**
> I am running Solaris 10 in a sparc environment.


Ehm RobSand

I don't mean to trod on your feet too hard - and it's not as if this sub-forum wouldn't profit from a bit more traffic (and at the risk of getting "forum cop!" yelled at me) - but are you aware that this is an *Ubuntu* forum? I can't help but notice that you've been starting two or three threads now with a similar introducing statement as above. 

There is some chance that you'll find Solaris-enabled people here to help you with your problems or questions, since people owning Sparcs tend to know it. Still, this is an Ubuntu forum, so please let's stick with Ubuntu or Ubuntu-on-Sparc related topics, questions and problems.

best regards

Marc

---

