---
title: "[SOLVED] new to ubuntu- random RAID mdadm daemon checks?"
date: 2008-08-03
forum: Server Platforms
---

### Post by alecm3 on 2008-08-03
I decided to switch from SuSE to Ubuntu, and I am configuring my first production MySQL server with 8.04.
I am using software RAID 1.
The machine is not yet deployed, it's sitting in the office.
Suddenly, i hear loud fan noise, even though there are no tasks running, and I check the load average: 2.8! Using "top" I notice that
md2_resync process is the culprit.

Then I look at /proc/mdstat and see:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 sda3[0] sdb3[1]
      135347520 blocks [2/2] [UU]
      [============>........]  check = 62.9% (85253248/135347520) finish=7.9min speed=125122K/sec


So apparently, mdadm daemon decided to check the array. 
How can i disable or control the schedule of these "checks" without having to disable mdadm daemon alltogether in /etc/init.d?
 
It's not acceptable for a production database machine to suddenly start a maintanence process that saturates its I/O bandwidth.

---

### Post by windependence on 2008-08-03
I'm gonna get hammered for this but software RAID has no business on a "production" server. You found one of the reasons. It takes resources.

Do you even need RAID? Remember, it's no substitute for good backups. I am just curious, if you are new to Ubuntu, what made you decide you HAD to have RAID on your server? I'm just really curious where this is all coming from.

Also, when you say "production", what are we talking here, 1 web site? 30? 300?

-Tim

---

### Post by alecm3 on 2008-08-03
> **windependence said:**
> I'm gonna get hammered for this but software RAID has no business on a "production" server. You found one of the reasons. It takes resources.

Do you even need RAID? Remember, it's no substitute for good backups. I am just curious, if you are new to Ubuntu, what made you decide you HAD to have RAID on your server? I'm just really curious where this is all coming from.

Also, when you say "production", what are we talking here, 1 web site? 30? 300?

-Tim

You have never worked in professional IT dealing with large deployments.

Running one website with multiple database servers, bandwidth 100Mbps and knowing what we are doing. Have been using software RAID for 5 years with success, others with even bigger setups (of the order of 100 DB servers) are using it as well. In fact, we did extensive benchmarking, and software RAID is much more stable and in many cases faster than embedded RAID (like LSI controllers). 
I would reserve your posting style for Digg, not for Linux forums.



Here is the answer to my own question:

This problem is listed as Ubuntu bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/212684](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/212684)

There is a cron script 
/etc/cron.d/mdadm
which runs /usr/share/mdadm/checkarray on the first Sunday of each month (which happened yesterday).

root@db2:/etc/cron.d# more mdadm 
#
# cron.d/mdadm -- schedules periodic redundancy checks of MD devices
#
# Copyright © martin f. krafft <madduck@madduck.net>
# distributed under the terms of the Artistic Licence 2.0
#
# $Id$
#

# By default, run at 01:06 on every Sunday, but do nothing unless the day of
# the month is less than or equal to 7. Thus, only run on the first Sunday of
# each month. crontab(5) sucks, unfortunately, in this regard; therefore this
# hack (see #380425).
6 1 * * 0 root [ -x /usr/share/mdadm/checkarray ] && [ $(date +\%d) -le 7 ] && /usr/share/mdadm/checkarray --cron --a
ll --quiet

Apparently, this cron killed the systems for quite a lot of people:
[http://ubuntuforums.org/showthread.php?t=748418](http://ubuntuforums.org/showthread.php?t=748418) etc

---

### Post by windependence on 2008-08-04
> **alecm3 said:**
> You have never worked in professional IT dealing with large deployments.

You might be embarrassed if you actually knew where I work. I can't say, but I can tell you I have worked for IBM Global Services, and at least 2 other Fortune 500 companies, most with Global data centers. I current work for one of these and also have a small consulting biz on the side, as well as host my own production web sites

> **alecm3 said:**
> Running one website with multiple database servers, bandwidth 100Mbps and knowing what we are doing. Have been using software RAID for 5 years with success, others with even bigger setups (of the order of 100 DB servers) are using it as well. In fact, we did extensive benchmarking, and software RAID is much more stable and in many cases faster than embedded RAID (like LSI controllers). 

IF you have had that success with software RAID, one of two things is true:

1. You have been extremely lucky.

2. You have really good admins.

I'm going to guess it's number 2. :)


> **alecm3 said:**
> I would reserve your posting style for Digg, not for Linux forums.

Look, I am not here to pick a fight or start flame wars. I am here to help people, and you may have noticed by my thank you count that I have done a pretty good job. If you don't like my posting style, of course you can set me to "ignore".



> **alecm3 said:**
> Here is the answer to my own question:

This problem is listed as Ubuntu bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/212684](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/212684)

There is a cron script 
/etc/cron.d/mdadm
which runs /usr/share/mdadm/checkarray on the first Sunday of each month (which happened yesterday).

root@db2:/etc/cron.d# more mdadm 
#
# cron.d/mdadm -- schedules periodic redundancy checks of MD devices
#
# Copyright © martin f. krafft <madduck@madduck.net>
# distributed under the terms of the Artistic Licence 2.0
#
# $Id$
#

# By default, run at 01:06 on every Sunday, but do nothing unless the day of
# the month is less than or equal to 7. Thus, only run on the first Sunday of
# each month. crontab(5) sucks, unfortunately, in this regard; therefore this
# hack (see #380425).
6 1 * * 0 root [ -x /usr/share/mdadm/checkarray ] && [ $(date +\%d) -le 7 ] && /usr/share/mdadm/checkarray --cron --a
ll --quiet

Apparently, this cron killed the systems for quite a lot of people:
[http://ubuntuforums.org/showthread.php?t=748418](http://ubuntuforums.org/showthread.php?t=748418) etc

I am glad you got it fixed, however I stand by what I said for anyone first coming into Linux or any other OS for that matter. IMHO software RAID has no place in a mission critical production environment. Of course we agree to disagree on that point and YMMV.

-Tim

---

### Post by alecm3 on 2008-08-04
> **windependence said:**
> 

I am glad you got it fixed, however I stand by what I said for anyone first coming into Linux or any other OS for that matter. IMHO software RAID has no place in a mission critical production environment. Of course we agree to disagree on that point and YMMV.

-Tim

I am of course not a first timer with Linux (as you can probably tell), but this is the first time I used Ubuntu- I am coming from SuSE and Redhat/Fedora.
I liked the minimalistic setup of Ubuntu server installation so far, but it's disappointing that I have found a distribution bug withing my first 3 days of Ubuntu experience.

Big companies, such as eBay/PayPal have had software RAID database installations (I do not have first hand knowledge if they still do (I assume so), but they have had them). You might be interested to read what Jeremy Zawodny (ex chief Yahoo database architect, now at Craigslist) [http://en.wikipedia.org/wiki/Jeremy_Zawodny](http://en.wikipedia.org/wiki/Jeremy_Zawodny) has to say about this:

[http://jeremy.zawodny.com/blog/archives/008696.html](http://jeremy.zawodny.com/blog/archives/008696.html)

Even if I did not have a first-had experience with rock-solid software RAID installations, and I have not benchmarked them myself against hardware RAID, I would somehow trust Jeremy Zawodny more.

---

### Post by Krupski on 2008-08-04
> **windependence said:**
> IF you have had that success with software RAID, one of two things is true:

1. You have been extremely lucky.

2. You have really good admins.

I'm going to guess it's number 2. :)

Well now you have me curious.

I run a NAS box at home made out of an Intel mobo, Ubuntu Server 64 bit and two 1 TB drives setup as RAID-1 (mirror).

I of course had the option of using either the mobo RAID or a dedicated RAID disk interface card in the machine... but I chose to use MDADM.

In the end, ALL RAID implementations are software. Even a RAID card is just a multi-port I/O card with a RAID bios in it.

So, why would one be "lucky" to have MDADM working for them? It seems to work just fine for me... :confused:

-- Roger

---

### Post by fjgaude on 2008-08-04
From having a few years experience with both hardware and software raid I'd say the only issue with software raid is the learing curve. You have to know what the results will be before you do it or else you might get into deep trouble. With the menu-driven hardware raid things are easier to learn.

As far as speed, with multi-core CPU setups, both have the same issues regarding reliability, and are equally quick. We use raid to maintain 100% uptime regarding disk failures, and to improve I/O.

The controversy seems to be one of philosophy, bias. **mdadm** is sufficiently mature to be trusted in any situation.

---

### Post by StickyStyle on 2008-08-04
> **fjgaude said:**
> 
The controversy seems to be one of philosophy, bias. **mdadm** is sufficiently mature to be trusted in any situation.

I second that notion. Here is an excellent comparison of Software vs. Hardware RAID from one of the kernel devs if anyone is curious [http://linux.yyz.us/why-software-raid.html](http://linux.yyz.us/why-software-raid.html)

---

### Post by fjgaude on 2008-08-04
Interesting, mind-set altering link:

   [http://linux.yyz.us/why-software-raid.html](http://linux.yyz.us/why-software-raid.html)

Says a lot because many words are required. Such has been my feelings for about two years.

---

### Post by unixbills on 2008-08-04
They seemed like resonable questions to me.  He only asked if you realy needed it, what size, and why you picked it?

Maybe Win-d is thinking a little bigger then a few hard drives in a box when you say "production".

It is easy to spot the pro.  Just read the posts.

(They wouldn't need 100 DB's if they would off load the RAID and stop tearing up system resources for drive I/O!)  


Bill

---

### Post by windependence on 2008-08-04
> **unixbills said:**
> They seemed like resonable questions to me.  He only asked if you realy needed it, what size, and why you picked it?

Maybe Win-d is thinking a little bigger then a few hard drives in a box when you say "production".

It is easy to spot the pro.  Just read the posts.

(They wouldn't need 100 DB's if they would off load the RAID and stop tearing up system resources for drive I/O!)  


Bill

Thanks Bill, I didn't want to start a flame war. Where ever I have been, if we had that many web servers or DBs, we usually used SAN storage anyway. We certainly could not take the time to set up software RAID on every box even if it WAS better. As you know, in a data center that size, you are always running, and can't piss around fooling with mdadm or similar stuff, you just want it to work and that's it, on to the next project.

I actually WAS trying to get a handle on what size load he was talking about as the title was "new to Ubuntu" I figured he had no experience. Of course that's what happens when you assume, right? ;)

-Tim

---

### Post by alecm3 on 2008-08-05
> **unixbills said:**
> 

(They wouldn't need 100 DB's if they would off load the RAID and stop tearing up system resources for drive I/O!)  


Bill

Can you elaborate on this? Sounds like I personally know at least 2 large companies that this suggestion would save about $300,000 in hardware (assuming that they can replace their current DB servers with single drive boxes with no RAID, which would save say $1,000/box - no hotswap SAS subsystem).

I always thought that RAID 0 with N drives for example increases I/O speed by N, and RAID 1 with N disks increases reads by N as well. Perhaps I am wrong?

> **windependence said:**
> Where ever I have been, if we had that many web servers or DBs, we usually used SAN storage anyway. We certainly could not take the time to set up software RAID on every box even if it WAS better. 

-Tim

I actually have no experience in running managed hosting. So I do not know what the requirements there are. I have experience running large websites where optimization and performance are critical, and where backend is custom and specific for the site. For those, messing with mdadm definitely pays off even if you have of the order of 50-100 DB servers. (You do not have to figure out how to monitor arrays with each proprietory RAID driver, nor you have incompatibility problems with those proprietory drivers causing random intermittent SCSI lockups when you upgrade the kernel on all machines at once).

With software RAID, you DO have to learn mdadm (but only once), and you have to learn how to hot-swap disks.

---

### Post by fjgaude on 2008-08-05
> **alecm3 said:**
> With software RAID, you DO have to learn mdadm (but only once), and you have to learn how to hot-swap disks.

Do you have any pointers on how to learn, any documents you would recommend? I've learned what I know the hard way and it wasn't easy. If a book that covers all issues were available life with **mdadm** would be a piece of cake.

It's only a matter of time for software raid to replace hardware ones. It's the multi-core CPUs and fast memory that has made it all possible.

---

### Post by alecm3 on 2008-08-06
> **fjgaude said:**
> Do you have any pointers on how to learn, any documents you would recommend? I've learned what I know the hard way and it wasn't easy. If a book that covers all issues were available life with **mdadm** would be a piece of cake.

It's only a matter of time for software raid to replace hardware ones. It's the multi-core CPUs and fast memory that has made it all possible.



I do not know of any comprehensive book unfortunately.
The basic mdadm stuff is mostly in man mdamd.

Here are some non-trivial points that I have found useful:

Boot partition is on raid, cannot boot:
[http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

Hot-swapping SCSI disks (this does not have to be done if the model of the disk is the same as the replacement):
[http://tldp.org/HOWTO/SCSI-2.4-HOWTO/mlproc.html](http://tldp.org/HOWTO/SCSI-2.4-HOWTO/mlproc.html)

---

### Post by fjgaude on 2008-08-06
Thanks for the links, alecm3... here's one to add to aid newcomers:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)

Happy software raiding!

---

