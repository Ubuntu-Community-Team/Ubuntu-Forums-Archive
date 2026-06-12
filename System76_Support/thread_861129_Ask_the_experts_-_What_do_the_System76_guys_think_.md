---
title: "Ask the experts - What do the System76 guys think of Ramlog?"
date: 2008-07-16
forum: System76 Support
---

### Post by imhavoc on 2008-07-16
Tom, have you ever looked at Ramlog? I'd like your expert opinion, if you have time.
[http://www.linux.com/feature/141231](http://www.linux.com/feature/141231)

---

### Post by thomasaaron on 2008-07-16
Well, I've not tried it, so this might be a little bit presumptuous of me, but I really don't see the point in it.

First, when you look at your logs, particularly /var/log/messages and /var/log/syslog, you see that they can produce *hundreds* of message entries in under a one second. If there is any performance penalty for the standard logging protocol of Ubuntu, it is about as negligible as negligible can be.

Second, as for it extending the life of hardware, Ramlog writes to your hardware when you turn the machine off anyway. So, either way, you are writing to your hardware.

Also, I'm not sure at first glance how it would help performance when: 1) You are using up valuable RAM to store logs until you shutdown, and 2) you are running the Ramlog daemon in the background *with* the other logging daemons.

I don't really have time to try to benchmark Ramlog to find out the truth about these things. But modern computers are already so fast that I have serious doubts that Ramlog is worth the extra effort and complexity.

Disclaimer: I haven't the slightest idea what I'm talking about. That was just a knee-jerk shot in the dark after scanning the link you provided. \\:D/

---

### Post by badbull on 2008-07-16
i think the point is, that you doesn't use your harddisk for the logfiles.
the log deamons wake the harddisk to write their logs. if you use ramlog the harddisk can sleep much longe and saves power.
for everyone who wants to try, there is a deb package for download at [http://freshmeat.net/projects/ramlog/?branch_id=72960&release_id=279333](http://freshmeat.net/projects/ramlog/?branch_id=72960&release_id=279333)
do it on your own risk

---

### Post by thomasaaron on 2008-07-16
Yeah, that might have a little positive effect on power consumption. I don't use my computer on battery power, though, long enough for it to make much of an impact.

Now that I think of it, though, it could conceivably prolong hard disk life, since it wouldn't be seating and re-seating the head for log entries. But I guess the sacrifice is using up RAM space. If you're a gamer or using heavy graphics programs, you might not like that.

---

### Post by SuperStuff on 2008-07-16
Is this the type of thing that will help with premature hard drive failure on laptops that folks keep mentioning?

---

### Post by thomasaaron on 2008-07-16
No.

That was a bug in which the hard drive head keeps re-seating itself constantly for no real good reason. There is a work-around for that.

Lot's of things cause the hard drive to seat and re-seat legitimately. The idea is that Ramlog would not be one of them. Thus, less seating and re-seating due to logging activities.

---

