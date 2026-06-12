---
title: "Reading Binary (systemd) Log Files On a System That Won't Boot?"
date: 2015-09-25
forum: Ubuntu/Debian BASED
---

### Post by TheFu on 2015-09-25
I have a system that won't boot and need to see the log files on the disk. It was written with journald - systemd logging.

I don't have the original media easily available, but to have 10 "save-my-butt" distros on a flash drive - like System Rescue, and assorted LTS based Ubuntu distros.

How can I read the logs?

Need to know before we start deploying this to remote locations.

---

### Post by QIII on 2015-09-25
You know, I was generally OK with systemd because I had been using it on my Fedora machine.  But this logging situation was a valid argument against going to systemd.

I don't recall that I have seen a resolution.

I don't generally give "google it" answers (you are definitely not a neophyte, so I hope we can work at it this way :) ), but what search terms have you used?

---

### Post by QDR06VV9 on 2015-09-25
Don't know if this will work in your case, but I have had a little luck with this information.
[https://www.digitalocean.com/community/tutorials/how-to-use-journalctl-to-view-and-manipulate-systemd-logs](https://www.digitalocean.com/community/tutorials/how-to-use-journalctl-to-view-and-manipulate-systemd-logs)
Maybe down to the past boots section.
Regards

---

### Post by QIII on 2015-09-25
That's a great catch, runrickus!  I'll use that.  Had no idea that existed.  

DigitalOcean is a treasure chest of useful stuff -- and not just for their customers.  I go there often to find some really good solutions to issues I face.

Not sure if that will help TheFu, though, since he can't boot.

---

### Post by TheFu on 2015-09-25
I've been reading all the systemd and journald information I can and haven't found an answer for this situation. Attended a journald class a few weeks ago and started thinking about this issue.

Large companies will push those logs to a log-server - so it isn't an issue for them on production systems.

Small users are expected to have the original distro available (optical/flash boot), know how to chroot (so the binary log files are in the expected location), then read them using journald.

How do we explain that to a noob in these forums? Worse, how do I explain it to a drone 1500 miles away who thinks the optical drive is a cup holder?  Not all our systems have remote power control - DRAC, RIBLO, IPMI ... sometimes just getting them to place the correct DVD into the optical drive is impossible.  Often fingerprints prevent a boot and fedex of new media is needed.

The only viable solution seem to be forcing journald to use syslog too. Which sorta defeats the purpose of binary logging if text is required to be enabled.

Or is there a trivial way for Ubuntu 14.04 to read journald binary logs?  What about TinyCore? Sometimes you just want a quick boot to see the logs.

Lots of stuff to try on my Centv7 boxes - just thought I'd ask here first.

---

### Post by QDR06VV9 on 2015-09-25
> [COLOR=#000000]How do we explain that to a noob in these forums?[/COLOR]
Exactly.
I was hoping TheFu could conjure some magic.
I think systemd will be A bit a of learning curve at least on my end.
Sorry it was not helpful.
Kind Regards

---

### Post by TheFu on 2015-09-25
Asked the same question to the journald presenter ... only answer is to boot off the installation media, go into rescue mode to gain access to journald.  He didn't elaborate about about chroot (if that was needed or not) or if we'd just be able to change a journald conf file or if the system automagically "knows" to find binary log files on the other disk.

We already need stuff like that for LVM or non-standard file systems, so what's the issue with 1 more new-distro dependency? Just another hassle in a modern OS.

[http://www.sysresccd.org/forums/viewtopic.php?f=6&t=4612](http://www.sysresccd.org/forums/viewtopic.php?f=6&t=4612) - System Rescue

I don't want to come off as anti-systemd. Having a single team creating interfaces rather than 20 different teams could bring sense to the Linux world.  As far as I can tell, systemd AND upstart were needed to fix issues that only large customers had. I never had any of those issues, so didn't see the point.  udev was a nice step.  I can see a binary system config tool coming - after all, it will save space, just like binary logging does.  Personally, I think gconf* is a abomination, but so are XML conf files. Plain text conf files make life easier. There are good reasons for this.

Plain text files are part of the '[Art of Unix Programming]("http://www.amazon.com/gp/product/0131429019")' ... which seems to have been lost in this generation of programmers who may have started out at MSFT training centers.

Oops - sorry for the digression.

Perhaps a fork of journald that always exports only text logs is needed?

---

### Post by QIII on 2015-09-25
Size is less of an issue in today's terabyte disk world, so I'm not entirely convinced that binary logs are really a great need.  Seems a bit late for that.

But logs should be human-readable because humans read them.  Having to jump through hoops like you are is counter-productive.

---

