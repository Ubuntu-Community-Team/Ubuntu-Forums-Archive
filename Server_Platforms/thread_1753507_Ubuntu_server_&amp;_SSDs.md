---
title: "Ubuntu server &amp; SSDs"
date: 2011-05-09
forum: Server Platforms
---

### Post by anwmalos on 2011-05-09
Although this is not exactly Ubuntu specific, I think that there is enough knowledge it this forum to answer my question.

I'm building a new server which will have ubuntu server 11.04 installed. A custom application will be developed for it that will collect information from a serial port and insert it in a mysql database (about 60-70 bytes INSERT once a minute), which in turn will be processed by a LAMP application which will serve nice pictures out of that data. As I'm researching my options on hardware, I am considering an SSD storage device because this server needs to be on 24/7/365 and I'm hoping for a minimum of 5-6 years. Downtime is not an issue but data loss is, so I need something that will not fail.

So my question is: How much will ubuntu wear down the SSD, considering that the server will be in an idle state most of the time (the LAMP app will be accessed 1-2 times a day)? Is it a reliable option for a non-raid setup? Will a software raid 0 with normal HDDs be more reliable? Would a ramdisk help minimise the writes on the SSD?

Sorry for being a bit of topic, but I don't know a community better suited to answer this question

---

### Post by Lars Noodén on 2011-05-09
Just guessing at the wear, but the SSDs should last at least as long as an old style magnetic drive.  If you want to be extra careful, buy two (preferably different brands) and set up [RAID level 1](http://www.pcguide.com/ref/hdd/perf/raid/levels/singleLevel1-c.html).

Also note that RAID is not a substitute for making good backup copies.

---

### Post by anwmalos on 2011-05-09
In my previous post I meant raid 1 :)

Well, the problem is that the server will be on a remote location so I cannot take frequent backups. I was thinking of backing up the system on a CF card that will be always connected on the machine but accessed only for backup purposes (cron job).

If I'm gonna go the raid way, I will install normal HDDs for sure, I was just thinking that SSDs are worn by writes, however normal HDDs are worn by time, after all they are mechanical. Isn't there a threshold of writes below which, the SSDs are actually more reliable than normal HDDs? And if yes, can an ubuntu server be below that threshold?

(I know that no one can answer my threshold question for sure, however I'm perfectly happy with educated guesses)

---

### Post by Lars Noodén on 2011-05-09
I've been looking for an authoritative source on SSD longevity.  Lifespan of storage media used to be something that the [US National Archives and Records Administration](http://www.google.com/search?hl=en&q=ssd+longevity+site:nara.gov) (NARA) tracked.  They seem to have gotten out of IT completely.  That leaves weaker sources to find. 

The current claims for SSDs are quite good because they've been improving each year.  In short, they're going to be very reliable.  One consultant page claims that you'd have to **write** an average of [22GB/day for 5 years](http://silvertonconsulting.com/blog/2010/01/08/toshiba-studies-laptop-write-rates-confirming-ssd-longevity/) to see any effect.  Reading is not so hard on SSDs.

---

### Post by Grenage on 2011-05-09
> **anwmalos said:**
> (I know that no one can answer my threshold question for sure, however I'm perfectly happy with educated guesses)

An SSD is going to be more reliable than a mechanical drive, there is no real doubt about that.  A mechanical drive could last 10 years, or fail after five minutes; while an SSD *could* fail after five minutes, it's far less likely.  I'm with Lars on this one.

The cron backup is also a good idea; backups are king!

---

### Post by ian dobson on 2011-05-09
Hi,

I know it's not really SSD related, but I have a box that boots from a 5 year old 2gb CF card. The system has been running since day 1 with the same card and I've not seen/heard of any problems with it (Data monitoring system).

In the same period of time I've seen several harddisks die, all of them used for the same data collection system. So maybe flash is better then rust :)

Regards
Ian Dobson

---

