---
title: "Any Ubuntu (Desktop or Server) with &gt; 200 days uptime ?"
date: 2012-01-06
forum: The Cafe
---

### Post by cap10Ibraim on 2012-01-06
>  [via]("http://mail.google.com/support/bin/answer.py?hl=en&ctx=mail&answer=1311182") listserv.fnal.gov 


[IMG]https://mail.google.com/mail/images/cleardot.gif[/IMG]
[IMG]https://mail.google.com/mail/images/cleardot.gif[/IMG]
to SCIENTIFIC-LIN. 
[IMG]https://mail.google.com/mail/images/cleardot.gif[/IMG]

Hi,

Is there anyone who has/had SL-6 machines running > 200 days ?

There is a kernel bug that causes a system crash when the uptime goes
over 208.5 days. This was noted by an Scientific Linux user on the SL
Japanese mailing list [1].

According to available info, the patch [2] is now in kernel 3.1.5.
RHEL/SL 6 is affected in the sense that the buggy code is there. SL 6
has been out long enough to see this bug in action and so I wondered
if someone has already encountered a crash. I searched TUV's bugzilla
but have not been able to find one that looks related.

If your system's uptime is approaching 200 days, you might want to do
a 'planned' reboot to avoid possible crashes.
so any ubuntu machine with more than 200 days ?

---

### Post by mr clark25 on 2012-01-06
i had an old webservver going for a long time...   it got up to about 100-150 days a couple times. it never made it much past that, though.

---

### Post by 73ckn797 on 2012-01-06
I have not kept a system running for more than a few weeks. It seems that with the number of updates provided with Ubuntu there are those times when a restart is required to implement the updates. With that in view, how long can one actually run effectively before a reboot is needed? Now, if updates are never applied then that changes everything. At least it seems to me to be that way.

---

### Post by overdrank on 2012-01-06
[Uptime thread ]("http://ubuntuforums.org/showthread.php?t=558401&highlight=uptime&page=39") ;)

---

### Post by BrokenKingpin on 2012-01-08
My media server was up for 187 days before I rebooted it so I could move it to another room.

---

### Post by 3rdalbum on 2012-01-09
My home server, which funnily enough is no longer at my home, has probably been running longer than 200 days without reboot. As I said it's no longer at my home, so next time I'm there I'll have to SSH in and check.

It's running 10.04 though, so it might predate the bug.

---

### Post by lolium on 2012-01-10
I work at a data centre and although all the servers there aren't mine, we have thousands which have an uptime of 400 days and over although there our old school ubuntu dapper servers were still running. Seems they run more smoothly then 8-10 in my opinion. We don't often occur any system crashes, generally memory issues not often kernel issues, unless our clients cause a kernel panic :-)

---

### Post by CharlesA on 2012-01-10
> **73ckn797 said:**
> I have not kept a system running for more than a few weeks. It seems that with the number of updates provided with Ubuntu there are those times when a restart is required to implement the updates. With that in view, how long can one actually run effectively before a reboot is needed? Now, if updates are never applied then that changes everything. At least it seems to me to be that way.

The only time I reboot my server is when a kernel update is needed and I think you can get around that by using ksplice (but I've not used it).

---

### Post by a2j on 2012-01-10
> **CharlesA said:**
> The only time I reboot my server is when a kernel update is needed 

this

---

### Post by Basher101 on 2012-01-10
> **a2j said:**
> this

-1...you should save power when you can :s

---

### Post by a2j on 2012-01-10
> **Basher101 said:**
> -1...you should save power when you can :s

that's right. I will let our data center team know that they should power down their servers to "save" power.

---

