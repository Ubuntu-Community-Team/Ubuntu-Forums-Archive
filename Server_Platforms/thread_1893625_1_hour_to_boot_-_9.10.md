---
title: "1 hour to boot - 9.10"
date: 2011-12-10
forum: Server Platforms
---

### Post by shoshomiga on 2011-12-10
I had to reboot my server running 9.10 and the boot was stuck for 1 hour (58 minutes) after the file system check.

It has happened before the last time the power went out but I thought it was a unique occurrence.

I need to fix this asap because I will be lynched if the power goes out and on top of that there is another hour of downtime.

---

### Post by snowpine on 2011-12-10
Welcome to the forums!

9.10 reached its "end of life" in April and is no longer supported: [http://fridge.ubuntu.com/2011/05/26/ubuntu-9-10-karmic-koala-end-of-life-reached-on-april-30-2011/](http://fridge.ubuntu.com/2011/05/26/ubuntu-9-10-karmic-koala-end-of-life-reached-on-april-30-2011/)

I recommend a fresh reinstall of Ubuntu 10.04. This is the current long-term-support release and will be supported through April 2015 for servers.

---

### Post by shoshomiga on 2011-12-10
Is there a way to fix this without reinstalling?

Because I would need to borrow a 1tb hard disk from somewhere since they are so expensive and I don't know if you can copy 800gb of data twice during the night, since I have software raid, I need to copy it somewhere and then back, unless there is another way.

Sorry if It's hard to read, I'm not a native english speaker.

---

### Post by insane_alien on 2011-12-10
you could get a UPS (an uninterruptable power supply) which would provide power to the server for a while allowing it to either ignore the black out or allow a clean shutdown without a filesystem check upon restarting.

Also, boot time filesystem checks can be turned off. They are scheduled to happen every 30 boots or so.

Upgrading isn't necessary but it is advised.

---

### Post by shoshomiga on 2011-12-10
Its not the filesystem check that's slowing it down, its not doing anything in these 58 minutes, no hard drive activity or anything.

---

### Post by oldfred on 2011-12-10
What do the log files show?

If you also have gui:
System -> Administration->Log File Viewer 
Look for repeated entries or long times between entries in messages

Otherwise look at the log files in:
/var/log/dmesg

Also messages, syslog and other log files should be reviewed for issues.

---

