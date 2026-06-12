---
title: "My server clock is bananas"
date: 2008-06-11
forum: Server Platforms
---

### Post by mgribov on 2008-06-11
This is the craziest thing Ive seen so far on any computer, ever.
The clock on one of the servers i manage i stuck, at 17:25:28 to 17:25:33 since that time today.
I logged into the server, noticed the clock was off, ran rdate ntp0.cornell.edu. That was at 17:25 EST. Right now its about 22:49 EST, and its still the same time on the server.
There is even rdate cron job for once an hour:
root@static:~# crontab -l
# m h dom mon dow command
0 * * * * /usr/sbin/rdate -s ntp0.cornell.edu > /dev/null 2>&1

Heres the output of date command running over and over:
root@static:~# date
Wed Jun 11 17:25:30 EDT 2008
root@static:~# date
Wed Jun 11 17:25:31 EDT 2008
root@static:~# date
Wed Jun 11 17:25:32 EDT 2008
root@static:~# date
Wed Jun 11 17:25:33 EDT 2008
root@static:~# date
Wed Jun 11 17:25:29 EDT 2008
root@static:~# date
Wed Jun 11 17:25:29 EDT 2008
root@static:~# date
Wed Jun 11 17:25:30 EDT 2008
root@static:~# date
Wed Jun 11 17:25:31 EDT 2008
root@static:~# date
Wed Jun 11 17:25:31 EDT 2008
root@static:~# date
Wed Jun 11 17:25:32 EDT 2008
root@static:~# date
Wed Jun 11 17:25:32 EDT 2008
root@static:~# date
Wed Jun 11 17:25:33 EDT 2008
root@static:~# date
Wed Jun 11 17:25:28 EDT 2008
root@static:~# date
Wed Jun 11 17:25:29 EDT 2008
root@static:~# date
Wed Jun 11 17:25:29 EDT 2008
root@static:~# date
Wed Jun 11 17:25:30 EDT 2008
root@static:~# date
Wed Jun 11 17:25:30 EDT 2008
root@static:~# date
Wed Jun 11 17:25:31 EDT 2008

is this crazy or what?.. I googled, but its certainly not a known issue.
This is on 2.6.22-14-server kernel on Ubuntu 7.10

Has anyone ever seen anything like this?..

---

### Post by molotov00 on 2008-06-11
I've never seen it. Two things come to mind though:

cornell.edu is messed up. Try another? Could be another program changing the clock.
hardware problem.

If you have physical access you could find out for sure by booting into the BIOS, setting the clock and watching it tick in there. If it keeps track outside of Ubuntu then it's Ubuntu that's fouling it up. That would tell you rather quickly if it is a hardware issue.

---

### Post by mgribov on 2008-06-11
Nope, cornell ntp is fine:
root@web1:~# /usr/sbin/rdate ntp0.cornell.edu
Wed 11 Jun 2008 11:20:09 PM EDT

Dont have physical access, but yeah, my money is also on hardware, but I did want to make this public in case it is a weird kernel issue somehow (i dont see how personally..)

There are 3 other servers on the same network with same Ubuntu versions sync'ing to the same ntp server - no problem.

All that server is running is Apache and awstats from cron - nothing else.

There is nothing weird in dmesg or in /var/log/all.log which is full syslog dump (although last entries are all in that same time span of course, and nothing is being added since time stands still)

Like i said, CRAZY..

---

### Post by quelx on 2008-06-11
does **hwclock** agree with the system clock?

---

### Post by mgribov on 2008-06-11
Nope, they are different (and also wrong):
root@static:/var/log# hwclock
Tue 10 Jun 2008 03:43:27 AM EDT  -0.190204 seconds
root@static:/var/log# date
Wed Jun 11 17:25:33 EDT 2008

---

### Post by quelx on 2008-06-11
> **mgribov said:**
> Nope, they are different (and also wrong):
root@static:/var/log# hwclock
Tue 10 Jun 2008 03:43:27 AM EDT  -0.190204 seconds
root@static:/var/log# date
Wed Jun 11 17:25:33 EDT 2008
Try setting the clock manually with **date MMDDhhmm** and then **sudo hwclock --systohc** what is the output several minutes later of **date && hwclock**

---

### Post by mgribov on 2008-06-11
> **quelx said:**
> Try setting the clock manually with **date MMDDhhmm** and then **sudo hwclock --systohc** what is the output several minutes later of **date && hwclock**

I will certainly try this, but since this is a leased server with a bit of a history of random crashes, I opened a ticket with the provider, so I want to get a confirmation that they saw this before I "fix" it.

So, even if Im able to fix this, I am very curious how/why something like this can happen.. 

Thanks for the tip though!

---

### Post by gtdaqua on 2008-06-12
do a simple:
```

sudo apt-get install ntp ntpdate
sudo ntpdate server pool.ntp.org

```

That will run the NTP daemon and your server clock will always sync correctly.
If the 2nd command is not working, stop the "ntpd" service and run it. Then start the "ntpd" service.

---

### Post by cycloptivity on 2008-06-12
I've had my one of my two fiesty servers "lag" and end up taking a larger and larger amount of time for each min but not this problem; Mine I think is related to a flat BIOS battery throwing out the host clock. I have since bogged over it with NTP on the host and the virtual machines

---

### Post by mgribov on 2008-06-12
So I spoke with the tech at the colo company, and he said that adding clocksource=pit to kernel boot options should prevent this from happening (we'll see - so far time is good)

cat /boot/grub/menu.lst
/boot/vmlinuz-2.6.22-14-server root=UUID=6ba594e7-fa81-44e6-963b-524df9de7584 ro quiet splash clocksource=pit acpi=off pci=nommconf

pit = programmable interrupt timer. 
[http://en.wikipedia.org/wiki/Programmable_Interval_Timer](http://en.wikipedia.org/wiki/Programmable_Interval_Timer)
[http://www.linux-mag.com/id/866](http://www.linux-mag.com/id/866)

---

