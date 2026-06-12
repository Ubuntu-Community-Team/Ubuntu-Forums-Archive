---
title: "Server locking up and resetting time?"
date: 2012-04-13
forum: Server Platforms
---

### Post by teqsun on 2012-04-13
My server has been locking up and is unresponsive to DNS or SSH requests.

I looked through the logs and it looks like right when it goes down, it is resetting the time to april 29th.

Here is a little snippet from the syslog file:

```

Apr 12 11:00:01 bigtobacco CRON[3186]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr 12 11:05:01 bigtobacco CRON[3641]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Apr 12 11:05:01 bigtobacco CRON[3642]: (munin) CMD (if [ -x /usr/bin/munin-cron ]; then /usr/bin/munin-cron; fi)
Apr 29 01:31:07 bigtobacco named[841]: timer.c:808: fatal error:
Apr 29 01:31:07 bigtobacco named[841]: RUNTIME_CHECK(isc_time_now((&now)) == 0) failed
Apr 29 01:31:07 bigtobacco named[841]: exiting (due to fatal error in library)

```

If anyone can point me towards a better way of troubleshooting I'd be happy to hear it.

So far I've tried removing recently installed software with no luck.

---

### Post by teqsun on 2012-04-13
ok took a look in the chron logs and found this itneresting little bit...

```

Apr 11 06:18:49 bigtobacco named[841]: client 37.59.91.212#25345: query (cache) 'isc.org/ANY/IN' denied
Apr 11 06:20:06 bigtobacco named[841]: last message repeated 3 times
Apr 29 01:31:07 bigtobacco named[841]: timer.c:808: fatal error:
Apr 29 01:31:07 bigtobacco named[841]: RUNTIME_CHECK(isc_time_now((&now)) == 0) failed
Apr 29 01:31:07 bigtobacco named[841]: exiting (due to fatal error in library)

```

I think it has something to do with BIND9 but I am not a BIND expert.

---

### Post by sj1410 on 2012-04-14
it looks like a DNS recursive attach or a DoS attack, have a look at this, it might help.


[http://chroot-me.in/blog/index.php/blog/34](http://chroot-me.in/blog/index.php/blog/34)

---

### Post by teqsun on 2012-05-02
Ok, after a few more weeks of isolating I still cannot figure out the issue.  I've used the link provided to block the attacks and they are no longer an issue.

Is there a log that is more helpful than syslog for debugging this?

I'm so close to just wiping the whole box but I got a lot of stuff on there so that is my last option.

edit: the time is no longer changing so IDK wtf is going on.

---

### Post by LHammonds on 2012-05-03
I know this sounds like a noob question but your root file system is not running out of space is it?

```
df -h
```

---

### Post by teqsun on 2012-05-03
no I am only using 6% of space available.

---

