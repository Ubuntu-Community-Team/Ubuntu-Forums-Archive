---
title: "occasional random crash"
date: 2008-01-15
forum: System76 Support
---

### Post by caviar on 2008-01-15
Hi,

Running feisty on a ratel I bought in May.

It has been running great - Until about a month ago.

Then: in the middle of the night, it had a hard crash - machine completely dead.  I rebooted. The next night, same thing.

I turned the machine off for a few days, and it has been back on now for weeks.

Until this morning: bingo! Another crash!

NOTHING in the logs (AFAICT)

Any ideas as to why, or how I could diagnose?

Thanks!

---

### Post by thomasaaron on 2008-01-15
If you don't mind, go ahead and post the output of: cat /var/log/messages
If there's nothing in there, it is hard to tell. Have you checked to make sure it has good air flow (i.e. not clogged up with dust-bunnies)?

---

### Post by caviar on 2008-01-15
Hi,

As far as I can tell (without stopping the machine and taking it apart), all air pathways look clear.

The log file seems to be too big to upload as an attachment - is there another way I can get it to you?

Thanks!

---

### Post by thomasaaron on 2008-01-15
Sure, you can run...

```
cat /var/log/messages >> ~/Desktop/messages.txt
```

...to create a text file on your Desktop that you can email to me at support(at)system76(dot)com.

---

### Post by thomasaaron on 2008-01-15
Well, I got your logs and this appears to be the offending entry:

```
GConf server is not in use, shutting down
```

There are a ton of leads via Google:
[http://linux.derkeiler.com/Mailing-Lists/Fedora/2004-05/7728.html](http://linux.derkeiler.com/Mailing-Lists/Fedora/2004-05/7728.html)
[http://lists.us.dell.com/pipermail/linux-poweredge/2004-April/013881.html](http://lists.us.dell.com/pipermail/linux-poweredge/2004-April/013881.html)
[http://www.getautomatix.com/forum/index.php?showtopic=1295](http://www.getautomatix.com/forum/index.php?showtopic=1295)
[http://ubuntuforums.org/showthread.php?t=214706](http://ubuntuforums.org/showthread.php?t=214706)
[http://www.linuxforums.org/forum/redhat-fedora-linux-help/30985-please-help-server-lockup-screen-freeze.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/30985-please-help-server-lockup-screen-freeze.html)

Some interesting things that I found linked to this error are:
* GDesklets downloaded via automatix
* KVM switches
* And Gconf being mis-configured

Do any of these ring a bell?

---

### Post by caviar on 2008-01-15
Hmmmm.

I am not sure why "gconf" problems would cause a crash....

And as you can see, the crash occurred  after around 3:36 am, with the gconf problems occuring at around 7:00pm the previous evening.

And those links - most of them were people asking about the log entries like mine, but no one replied! What *do* these log entries mean?

I will say this, though. For at least two of the three crashes, the screensaver was running (that is, the screensaver pattern was frozen on the screen). And the screen was *not* blacked out, as it normally does after (I think) 1/2 hour of non-use. And for one crash, the disk light was frozen on (the other two, not).

The weird thing is, from May until November, everything was running just fine!

Perhaps due to an update/new kernel? (I haven't updated in a while...)

---

### Post by thomasaaron on 2008-01-16
OK, I have actually seen the screensaver freezing bug on my own computer. However, I never checked the logs. I just re-booted.

Are you using a wireless connection, because I suspeced that on my own computer it might be related to a bug with the ipw3945 driver.

---

### Post by caviar on 2008-01-16
No wireless on my system.

When your screensaver froze, had the computer crashed? Or just the screesaver/xserver?

---

### Post by thomasaaron on 2008-01-16
Just the screensave/xserver.

---

### Post by thomasaaron on 2008-01-16
OK, if that log entry isn't indicative of what is going on, I'm don't really see anything else that seems like the culprit.

Just out of curiosity, have you checked System > Preferences > Power Management? There are settings there to put an idle computer to sleep.
(I realize that your issue seems random, so this is probably not it. But it never hurts to get all of the basic stuff out of the way.)

---

### Post by caviar on 2008-01-16
"Put computer to sleep when inactive for:"  Never
"Put display to sleep when inactive for:"  41 minutes

---

